---
title: Visual Studio Container Tools oluşturma ve hata ayıklama genel bakış
author: ghogen
description: Konteyner Araçları oluşturma ve hata ayıklama işlemine genel bakış
ms.author: ghogen
ms.date: 11/20/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: d91dd01879ac3bb62b981109463f6762046382ef
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77027268"
---
# <a name="how-visual-studio-builds-containerized-apps"></a>Visual Studio’nun kapsayıcılı uygulama oluşturma şekli

Visual Studio IDE'den bina inşa ediyor olun, ister bir komut satırı yapısı oluşturuyor olun, Visual Studio'nun projelerinizi oluşturmak için Dockerfile'ı nasıl kullandığını bilmeniz gerekir.  Performans nedenlerinden dolayı Visual Studio, kapsayıcı uygulamalar için özel bir işlem izler. Visual Studio'nun projelerinizi nasıl oluşturduğunu anlamak, Özellikle Dockerfile'ı değiştirerek yapı sürecinizi özelleştirdiğinizde önemlidir.

Visual Studio Docker kapsayıcıları kullanmayan bir proje oluşturduğunda, yerel makinede MSBuild çağırır ve yerel çözüm `bin`klasörünüzün altında (genellikle) bir klasörde çıktı dosyaları oluşturur. Ancak, kapsayıcılaştırılmış bir proje için, yapı işlemi, Dockerfile'ın konteynerleştirilmiş uygulamayı oluşturmak için yönergelerini dikkate alır. Visual Studio'nun kullandığı Dockerfile birden çok aşamaya ayrılmıştır. Bu işlem Docker'ın *çok aşamalı yapı* özelliğine dayanır.

## <a name="multistage-build"></a>Çok aşamalı yapı

Çok aşamalı yapı özelliği, kapsayıcıoluşturma işlemini daha verimli hale getirmeye yardımcı olur ve kapların yalnızca uygulamanızın çalışma zamanında ihtiyaç duyduğu bitleri içermesine izin vererek kapsayıcıları küçültür. Çok aşamalı yapı ,.NET Framework projeleri için değil.NET Core projeleri için kullanılır.

Çok aşamalı yapı, kapsayıcı görüntülerinin ara görüntüler üreten aşamalarda oluşturulmasını sağlar. Örnek olarak, Visual Studio tarafından oluşturulan tipik bir Dockerfile düşünün - ilk `base`aşamada:

```
FROM mcr.microsoft.com/dotnet/core/aspnet:2.2-stretch-slim AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443
```

Dockerfile'daki satırlar Microsoft Konteyner Kayıt Defteri'ndeki (mcr.microsoft.com) Debian `base` görüntüsüyle başlar ve 80 ve 443 bağlantı `/app`noktalarını ortaya çıkaran ve çalışma dizini ayarlayan bir ara görüntü oluşturur.

Bir sonraki `build`aşama , aşağıdaki gibi görünür:

```
FROM mcr.microsoft.com/dotnet/core/sdk:2.2-stretch AS build
WORKDIR /src
COPY ["WebApplication43/WebApplication43.csproj", "WebApplication43/"]
RUN dotnet restore "WebApplication43/WebApplication43.csproj"
COPY . .
WORKDIR "/src/WebApplication43"
RUN dotnet build "WebApplication43.csproj" -c Release -o /app
```

Aşamanın, `build` tabandan devam etmek yerine kayıt defterinden`sdk` farklı `aspnet`bir orijinal görüntüden (yerine) başladığını görebilirsiniz.  Görüntü `sdk` tüm yapı araçları vardır ve bu nedenle sadece çalışma zamanı bileşenleri içeren aspnet görüntü, çok daha büyüktür. Dockerfile'ın geri kalanına baktığınızda ayrı bir görüntü kullanmanın nedeni netleşir:

```
FROM build AS publish
RUN dotnet publish "WebApplication43.csproj" -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "WebApplication43.dll"]
```

Son aşama yeniden `base`başlar ve `COPY --from=publish` yayınlanan çıktıyı son görüntüye kopyalamayı içerir. Bu işlem, `sdk` görüntüdeki tüm yapı araçlarını eklemesi gerekmediğinden, son görüntünün çok daha küçük olmasını mümkün kılar.

## <a name="building-from-the-command-line"></a>Komut satırından bina

Visual Studio'nun dışında bir yapı oluşturmak `docker build` `MSBuild` istiyorsanız, komut satırından oluşturabilir veya kullanabilirsiniz.

### <a name="docker-build"></a>docker build

Komut satırından kapsayıcıbir çözüm oluşturmak için genellikle çözümdeki her proje için komutu `docker build <context>` kullanabilirsiniz. *Yapı bağlamı* bağımsız değişkenini sağlarsınız. Dockerfile'ın *yapı bağlamı,* görüntüyü oluşturmak için çalışma klasörü olarak kullanılan yerel makinedeki klasördür. Örneğin, dosyayı kopyaladığınız klasördür.  .NET Core projelerinde, çözüm dosyasını (.sln) içeren klasörü kullanın.  Göreceli bir yol olarak ifade edilen bu bağımsız değişken, proje klasöründeki Dockerfile ve üst klasöründeki çözüm dosyası için genellikle ".." olarak ifade edilir.  .NET Framework projeleri için yapı bağlamı çözüm klasörü değil, proje klasörüdür.

```cmd
docker build -f Dockerfile ..
```

### <a name="msbuild"></a>MSBuild

Visual Studio tarafından .NET Framework projeleri için oluşturulan Dockerfiles (ve Visual Studio 2017 Güncellemesi 4'ten önce Visual Studio sürümleriyle oluşturulan .NET Core projeleri) çok aşamalı Dockerfiles değildir.  Bu Docker dosyalarındaki adımlar kodunuzu derlemez.  Bunun yerine, Visual Studio bir .NET Framework Dockerfile oluşturduğunda, ilk olarak MSBuild kullanarak projenizi derler.  Bu başarılı olduğunda, Visual Studio daha sonra sadece ortaya çıkan Docker görüntü içine MSBuild yapı çıktı kopyalayan Dockerfile oluşturur.  Kodunuzu derleme adımları Dockerfile'a dahil olmadığından, komut satırından .NET Framework Dockerfiles'ı oluşturamazsınız. `docker build` Bu projeleri oluşturmak için MSBuild'i kullanmalısınız.

Tek docker konteyner projesi için bir görüntü oluşturmak `/t:ContainerBuild` için komut seçeneği ile MSBuild kullanabilirsiniz. Örnek:

```cmd
MSBuild MyProject.csproj /t:ContainerBuild /p:Configuration=Release
```

Visual Studio IDE'den çözüm oluşturduğunuzda **Çıktı** penceresinde gördüğünüze benzer çıktı görürsünüz. `/p:Configuration=Release`Visual Studio'nun çok aşamalı yapı optimizasyonu kullandığı durumlarda hata **ayıklama** yapılandırmasını oluştururken sonuçlar beklendiği gibi olmayabilir. Bkz. [Hata Ayıklama](#debugging).

Docker Oluştur projesi kullanıyorsanız, görüntü oluşturmak için bu komutu kullanın:

```cmd
msbuild /p:SolutionPath=<solution-name>.sln /p:Configuration=Release docker-compose.dcproj
```

## <a name="project-warmup"></a>Proje ısınma

*Proje ısınması,* sonraki çalıştırmaların **(F5** veya **Ctrl**+**F5)** performansını artırmak için bir proje için Docker profili seçildiğinde (diğer bir proje yüklendiğinde veya Docker desteği eklendiğinde) meydana gelen bir dizi adımı ifade eder. Bu **Araçlar** > **Seçenekleri** > **Konteyner Araçları**altında yapılandırılabilir. Arka planda çalışan görevler şunlardır:

- Docker Desktop'ın yüklü ve çalışır durumda olup olmadığını kontrol edin.
- Docker Desktop'ın projeyle aynı işletim sistemine ayarlandığından emin olun.
- Dockerfile'ın ilk aşamasındaki görüntüleri çekin `base` (çoğu Dockerdosyasındaki sahne).  
- Dockerfile'ı oluşturun ve kapsayıcıyı çalıştırın.

Isınma yalnızca **Hızlı** modda gerçekleşir, böylece çalışan kapsayıcı uygulama klasörüne ses monte edecektir. Bu, uygulamada yapılan değişikliklerin kapsayıcıyı geçersiz kılmayamayacağı anlamına gelir. Bu nedenle hata ayıklama performansını önemli ölçüde artırır ve büyük görüntüleri çekme gibi uzun süren görevler için bekleme süresini azaltır.

## <a name="volume-mapping"></a>Birim eşleme

Hata ayıklamanın kapsayıcılarda çalışması için Visual Studio, ana makineden hata ayıklama ve NuGet klasörlerini eşlemek için ses eşlemini kullanır. Birim eşleme [burada](https://docs.docker.com/storage/volumes/)Docker belgelerinde açıklanmıştır. Kabınıza monte edilen birimler şunlardır:

|||
|-|-|
| **Uzaktan hata ayıklama** | Proje türüne bağlı olarak hata ayıklamayı kapsayıcıda çalıştırmak için gereken bitleri içerir. Bu daha açıklanmıştır |[Hata Ayıklama](#debugging) bölümünde ayrıntılı olarak.
| **Uygulama klasörü** | Dockerfile'nin bulunduğu proje klasörünü içerir.|
| **Kaynak klasör** | Docker komutlarına geçirilen yapı bağlamını içerir.|
| **NuGet paketleri klasörleri** | Projedeki *\{obj project}.csproj.nuget.g.props* dosyasından okunan NuGet paketlerini ve geri dönüş klasörlerini içerir. |

Temel web uygulamalarını ASP.NET için, SSL sertifikası ve kullanıcı sırları için iki ek klasör olabilir ve bu klasör bir sonraki bölümde daha ayrıntılı olarak açıklanabilir.

## <a name="ssl-enabled-aspnet-core-apps"></a>SSL özellikli ASP.NET Core uygulamaları

Visual Studio'daki konteyner araçları, ssl özellikli ASP.NET çekirdek uygulamasının dev sertifikasıyla hata ayıklamasını destekler, aynı şekilde kapsayıcılar olmadan çalışmasını beklersiniz. Bunu gerçekleştirmek için Visual Studio, sertifikayı dışa aktarmak ve kapsayıcıya kullanılabilir hale getirmek için birkaç adım daha ekler. İşte Visual Studio'nun kapsayıcıda hata ayıklarken sizin için işlediği akış:

1. `dev-certs` Yerel geliştirme sertifikasının hazır olmasını ve alet aracılığıyla ana makinede güvenilmesini sağlar.
2. Sertifikayı bu uygulamanın kullanıcı sırları deposunda depolanan güvenli bir parolayla %APPDATA%\ASP.NET\Https'ye dışa aktarın.
3. Ses seviyesi aşağıdaki dizinleri bağlar:

   - *%APPDATA%\Microsoft\UserSecrets*
   - *%APPDATA%\ASP.NET\Https*

ASP.NET Core, *Https* klasörü altında derleme adı ile eşleşen bir sertifika arar, bu nedenle bu yoltaki kapsayıcıya eşlenir. Sertifika yolu ve parola alternatif olarak ortam değişkenleri `ASPNETCORE_Kestrel__Certificates__Default__Path` (yani) `ASPNETCORE_Kestrel__Certificates__Default__Password`veya kullanıcı sırları json dosyası, örneğin kullanılarak tanımlanabilir:

```json
{
  "Kestrel": {
    "Certificates": {
      "Default": {
        "Path": "c:\\app\\mycert.pfx",
        "Password": "strongpassword"
      }
    }
  }
}
```

Yapılandırmanız hem kapsayıcı hem de kapsayıcı olmayan yapılar destekliyorsa, yollar kapsayıcı ortamına özgü olduğundan ortam değişkenlerini kullanmanız gerekir.

Kapsayıcılarda ASP.NET Core uygulamalarıyla SSL kullanma hakkında daha fazla bilgi [için, HTTPS üzerinden Docker ile Barındırma ASP.NET Core görüntülerine](/aspnet/core/security/docker-https)bakın).

## <a name="debugging"></a>Hata ayıklama

**Hata Ayıklama** yapılandırmasında oluştururken, Visual Studio'nun kapsayıcı projeler için yapı işleminin performansına yardımcı olan birkaç optimizasyon vardır. Kapsayıcı uygulamalar için yapı süreci, Dockerfile'da özetlenen adımları izleyerek basit değildir. Bir konteyner de bina çok yerel makine üzerinde bina daha yavaştır.  Bu nedenle, Hata **Ayıklama** yapılandırmasında oluşturduğunuzda, Visual Studio projelerinizi yerel makinede oluşturur ve çıktı klasörünü ses montajını kullanarak kapsayıcıya paylaşır. Bu optimizasyon etkin bir yapı *hızlı* mod oluşturma denir.

**Hızlı** modda Visual `docker build` Studio, Docker'a yalnızca sahneyi `base` oluşturmasını söyleyen bir argümanla çağırır.  Visual Studio, Dockerfile'ın içeriğine bakılmaksızın sürecin geri kalanını yönetir. Bu nedenle, kapsayıcı ortamını özelleştirmek veya ek bağımlılıklar yüklemek gibi Dockerfile'ınızı değiştirdiğinizde, değişikliklerinizi ilk aşamaya koymanız gerekir.  Dockerfile's, `build` `publish`veya `final` aşamalarında yerleştirilen herhangi bir özel adımlar yürütülmez.

Bu performans optimizasyonu yalnızca **Hata Ayıklama** yapılandırmasında oluşturduğunuzda oluşur. **Sürüm** yapılandırmasında, yapı Dockerfile'da belirtildiği gibi kapsayıcıda oluşur.

Performans optimizasyonunu devre dışı bırakıp Dockerfile'ın belirttiği gibi oluşturmak istiyorsanız, **ContainerDevelopmentMode** özelliğini proje dosyasındaki **Düzenli** olarak aşağıdaki gibi ayarlayın:

```xml
<PropertyGroup>
   <ContainerDevelopmentMode>Regular</ContainerDevelopmentMode>
</PropertyGroup>
```

Performans optimizasyonunu geri yüklemek için özelliği proje dosyasından kaldırın.

 Hata ayıklamaya başladığınızda **(F5),** mümkünse daha önce başlatılmış bir kapsayıcı yeniden kullanılır. Önceki kapsayıcıyı yeniden kullanmak istemiyorsanız, Visual Studio'daki **Yeniden Oluşturma** veya **Temizle** komutlarını kullanarak Visual Studio'yu yeni bir kapsayıcı kullanmaya zorlayabilirsiniz.

Hata ayıklama nın çalıştırılma işlemi, proje ve kapsayıcı işletim sisteminin türüne bağlıdır:

|||
|-|-|
| **.NET Core uygulamaları (Linux kapları)**| Visual Studio `vsdbg` indirir ve konteyner eşler, daha sonra program ve argümanlar `dotnet webapp.dll`(yani, ) ile çağrılır alır ve sonra hata ayıklama işlemine bağlanır. |
| **.NET Core uygulamaları (Windows kapsayıcıları)**| Visual Studio `onecoremsvsmon` kullanır ve konteyner için haritalar, giriş noktası olarak çalışır ve daha sonra Visual Studio ona bağlanır ve programınıza bağlanır. Bu, normalde başka bir bilgisayarda veya sanal makinede uzaktan hata ayıklama ayarlamak nasıl benzer.|
| **.NET Framework uygulamaları** | Visual Studio `msvsmon` kullanır ve konteyner için haritalar, Visual Studio bağlanabilir giriş noktasının bir parçası olarak çalışır ve programınıza bağlanır.|

Hakkında bilgi `vsdbg.exe`için Visual [Studio'dan Linux ve OSX'te .NET Core'un Offroad hata ayıklanmasına](https://github.com/Microsoft/MIEngine/wiki/Offroad-Debugging-of-.NET-Core-on-Linux---OSX-from-Visual-Studio)bakın.

## <a name="container-entry-point"></a>Konteyner giriş noktası

Visual Studio proje türüne ve konteyner işletim sistemine bağlı olarak özel bir kapsayıcı giriş noktası kullanır, burada farklı kombinasyonları şunlardır:

|||
|-|-|
| **Linux konteynerleri** | Giriş noktası, `tail -f /dev/null`kapsayıcının çalışmasını sağlamak için sonsuz bir bekleyiştir. Uygulama hata ayıklama yoluyla başlatıldığında, uygulamayı çalıştırmaktan sorumlu hata ayıklamadır (diğer `dotnet webapp.dll`bir şekilde). Hata ayıklama olmadan başlatılırsa, araç uygulaması `docker exec -i {containerId} dotnet webapp.dll` çalıştırmak için bir çalıştırın.|
| **Windows kapsayıcıları**| Giriş noktası hata `C:\remote_debugger\x64\msvsmon.exe /noauth /anyuser /silent /nostatus` ayıklama çalışır gibi bir şeydir, bu yüzden bağlantıları dinliyor. Hata ayıklamanın uygulamayı çalıştırdığı ve hata `docker exec` ayıklama yapılmadan başlatıldığında bir komutun da geçerli olduğu gibi. .NET Framework web uygulamaları için giriş noktası, `ServiceMonitor` komuta eklenen yerdeki nden biraz farklıdır.|

Konteyner giriş noktası, tek konteyner projelerinde değil, yalnızca docker-compose projelerinde değiştirilebilir.

## <a name="next-steps"></a>Sonraki adımlar

Proje dosyalarınızda ek MSBuild özellikleri ayarlayarak yapılarınızı nasıl daha da özelleştirebilirsiniz öğrenin. [Konteyner projeleri için MSBuild özelliklerine](container-msbuild-properties.md)bakın.

## <a name="see-also"></a>Ayrıca bkz.

[Windows'da](../msbuild/msbuild.md)

Windows[Linux kapsayıcılarında](/virtualization/windowscontainers/deploy-containers/linux-containers) MSBuild[Dockerfile](/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile)
