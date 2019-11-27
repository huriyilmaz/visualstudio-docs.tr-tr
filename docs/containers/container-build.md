---
title: Visual Studio kapsayıcı araçları derleme ve hata ayıklamasına genel bakış
author: ghogen
description: Kapsayıcı araçları derleme ve hata ayıklama işlemine genel bakış
ms.author: ghogen
ms.date: 11/20/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: 6b96f23bc7bcd7e6d970025b23f89f572d07daf1
ms.sourcegitcommit: e825d1223579b44ee2deb62baf4de0153f99242a
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2019
ms.locfileid: "74473995"
---
# <a name="build-and-debug-containerized-apps-using-visual-studio-or-the-command-line"></a>Visual Studio veya komut satırı kullanarak Kapsayıcılı uygulamalar derleme ve hata ayıklama

Visual Studio IDE 'den oluşturuluyor veya bir komut satırı derlemesi ayarlıyoruz, Visual Studio derlemelerinizin projelerinizi oluşturmak için Dockerfile 'ı nasıl kullandığını bilmeniz gerekir.  Performans nedenleriyle, Visual Studio Kapsayıcılı uygulamalar için özel bir işlem izler. Visual Studio 'Nun projelerinizi nasıl derlemediğini anlamak, Dockerfile dosyasını değiştirerek yapı işleminizi özelleştirirken özellikle önemlidir.

Visual Studio, Docker Kapsayıcıları kullanmayan bir proje oluşturduğunda, yerel makinede MSBuild 'i çağırır ve çıkış dosyalarını yerel çözüm klasörünüzün altında bir klasörde (genellikle `bin`) oluşturur. Bununla birlikte, kapsayıcılı bir proje için yapı işlemi, Dockerfile 'ın Kapsayıcılı uygulama oluşturma yönergelerinin bir hesabını alır. Visual Studio 'Nun kullandığı Dockerfile birden çok aşamaya bölünmüştür. Bu işlem Docker 'ın *çok aşamalı derleme* özelliğini kullanır.

## <a name="multistage-build"></a>Çok aşamalı derleme

Çoklu aşama oluşturma özelliği, kapsayıcıları oluşturma işleminin daha verimli olmasına yardımcı olur ve yalnızca uygulamanızın çalışma zamanında ihtiyaç duyacağı bitleri içermesine izin vererek kapsayıcıları daha küçük hale getirir. MultiStage derlemesi, .NET Framework projeleri değil .NET Core projeleri için kullanılır.

Hatlarında derlemesi, ara görüntü üreten aşamalarda kapsayıcı görüntülerinin oluşturulmasına izin verir. Örnek olarak, Visual Studio tarafından oluşturulan tipik bir Dockerfile 'ı düşünün; ilk aşama `base`:

```
FROM mcr.microsoft.com/dotnet/core/aspnet:2.2-stretch-slim AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443
```

Dockerfile içindeki satırlar, Microsoft Container Registry (mcr.microsoft.com) ' den nano sunucu görüntüsüyle başlar ve 80 ve 443 bağlantı noktalarını kullanıma sunan bir ara görüntü `base` oluşturun ve çalışma dizinini `/app`olarak ayarlar.

Sonraki aşama, aşağıdaki gibi görünen `build`.

```
FROM mcr.microsoft.com/dotnet/core/sdk:2.2-stretch AS build
WORKDIR /src
COPY ["WebApplication43/WebApplication43.csproj", "WebApplication43/"]
RUN dotnet restore "WebApplication43/WebApplication43.csproj"
COPY . .
WORKDIR "/src/WebApplication43"
RUN dotnet build "WebApplication43.csproj" -c Release -o /app
```

`build` aşamasının, temelden devam etmek yerine kayıt defterinden farklı bir orijinal görüntüden (`aspnet`değil`sdk`) başlayacağını görebilirsiniz.  `sdk` görüntüde tüm derleme araçları bulunur ve bu nedenle yalnızca çalışma zamanı bileşenleri içeren ASPNET görüntüsünden çok daha büyük bir. Dockerfile ' ın geri kalanına göz atadığınızda ayrı bir görüntü kullanmanın nedeni açık olur:

```
FROM build AS publish
RUN dotnet publish "WebApplication43.csproj" -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "WebApplication43.dll"]
```

Son aşama `base`' den yeniden başlar ve yayımlanan çıktıyı son görüntüye kopyalamak için `COPY --from=publish` ekler. Bu işlem, `sdk` görüntüde bulunan tüm derleme araçlarını içermesi gerekmiyorsa nihai görüntünün çok daha küçük olmasını mümkün kılar.

## <a name="faster-builds-for-the-debug-configuration"></a>Hata ayıklama yapılandırması için daha hızlı yapılar

Visual Studio 'nun Kapsayıcılı projelere yönelik yapı sürecinin performansına yardımcı olan birkaç iyileştirmesi vardır. Kapsayıcılı uygulamalar için derleme işlemi, Dockerfile içinde özetlenen adımları takip etmek kadar basit değildir. Kapsayıcıda derleme, yerel makinede oluşturmaktan çok daha yavaştır.  Bu nedenle, **hata ayıklama** yapılandırmasında derleme yaparken, Visual Studio projelerinizi gerçekten yerel makinede oluşturur ve ardından çıkış klasörünü birim bağlama kullanarak kapsayıcınıza paylaşır. Bu iyileştirme etkin olan bir yapıya *hızlı* mod oluşturma denir.

**Hızlı** modda, Visual Studio, Docker 'ın yalnızca `base` aşamasını oluşturmasını söyleyen bir bağımsız değişkenle `docker build` çağırır.  Visual Studio, Dockerfile içeriğiyle ilgili olarak işlemin geri kalanını işler. Bu nedenle, kapsayıcı ortamını özelleştirmek veya ek bağımlılıklar yüklemek gibi Dockerfile 'ı değiştirdiğinizde, değişikliklerinizi ilk aşamada koymanız gerekir.  Dockerfile 'ın `build`, `publish`veya `final` aşamalarına yerleştirilmiş özel adımlar yürütülmez.

Bu performans iyileştirmesi yalnızca **hata ayıklama** yapılandırmasında derleme yaparken oluşur. **Yayın** yapılandırmasında, yapı, Dockerfile içinde belirtildiği gibi kapsayıcıda oluşur.

Dockerfile tarafından belirtildiği gibi performans iyileştirmesini ve derlemeyi devre dışı bırakmak istiyorsanız, proje dosyasında şu şekilde **Containerdevelopmentmode** özelliğini **normal** olarak ayarlayın:

```xml
<PropertyGroup>
   <ContainerDevelopmentMode>Regular</ContainerDevelopmentMode>
</PropertyGroup>
```

Performans iyileştirmesini geri yüklemek için, özelliği proje dosyasından kaldırın.

## <a name="building-from-the-command-line"></a>Komut satırından oluşturma

`docker build` veya `MSBuild`, komut satırından oluşturmak için kullanabilirsiniz.

### <a name="docker-build"></a>Docker derlemesi

Komut satırından kapsayıcılı bir çözüm oluşturmak için, çözüm içindeki her proje için genellikle komut `docker build <context>` kullanabilirsiniz. *Yapı bağlamı* bağımsız değişkenini sağlarsınız. Dockerfile için *derleme bağlamı* , yerel makinedeki, görüntüyü oluşturmak için çalışma klasörü olarak kullanılan klasördür. Örneğin, kapsayıcıya kopyaladığınız sırada dosyaları kopyaladığınız klasördür.  .NET Core projelerinde, çözüm dosyasını (. sln) içeren klasörü kullanın.  Göreli yol olarak ifade edilen bu bağımsız değişken, genellikle proje klasöründeki bir Dockerfile ve onun üst klasöründeki çözüm dosyası için ".." olur.  .NET Framework projeleri için, yapı bağlamı çözüm klasörü değil, proje klasörüdür.

```cmd
docker build -f Dockerfile ..
```

### <a name="msbuild"></a>MSBuild

.NET Framework projeleri için Visual Studio tarafından oluşturulan dockerfiles (ve Visual Studio 2017 güncelleştirme 4 ' ten önceki Visual Studio sürümleriyle oluşturulan .NET Core projeleri için) çok aşamalı Dockerfiles değildir.  Bu Dockerfiles içindeki adımlar kodunuzu derlemez.  Bunun yerine, Visual Studio .NET Framework Dockerfile oluşturduğunda, öncelikle projenizi MSBuild kullanarak derler.  Bu başarılı olduğunda Visual Studio, yapı çıkışını MSBuild 'ten elde edilen Docker görüntüsüne kopyalayan Dockerfile öğesini oluşturur.  Kodunuzu derlemek için gereken adımlar Dockerfile 'a dahil edilmediğinden, komut satırından `docker build` kullanarak .NET Framework Dockerfiles derlenemez. Bu projeleri derlemek için MSBuild 'i kullanmanız gerekir.

Tek Docker kapsayıcı projesi için bir görüntü oluşturmak üzere, MSBuild 'i `/t:ContainerBuild` komut seçeneği ile kullanabilirsiniz. Örneğin:

```cmd
MSBuild MyProject.csproj /t:ContainerBuild /p:Configuration=Release
```

Visual Studio IDE 'den Çözümünüzü oluştururken **Çıkış** penceresinde gördüklerinize benzer bir çıktı görürsünüz. Her zaman `/p:Configuration=Release`kullanın, Visual Studio 'Nun çok aşamalı derleme iyileştirmesini kullandığı durumlarda, **hata ayıklama** yapılandırmasını oluştururken sonuçlar beklendiği gibi olmayabilir.

Docker Compose projesi kullanıyorsanız, görüntüleri derlemek için komutunu kullanın:

```cmd
msbuild /p:SolutionPath=<solution-name>.sln /p:Configuration=Release docker-compose.dcproj
```

## <a name="project-warmup"></a>Proje ısınma

Bunlar, sonraki çalıştırmanın (**F5** veya **CTRL**+**F5**) performansını artırmak amacıyla bir proje için Docker profili seçildiğinde (yani, bir proje yüklendiğinde veya Docker desteği eklendiğinde) gerçekleşen bir adım dizisidir. Bu, **araçlar** > **Seçenekler** > **kapsayıcı araçları**altında yapılandırılabilir. Arka planda çalışan görevler şunlardır:

- Docker Desktop ' ın yüklü olduğundan ve çalıştığından emin olun.
- Docker Desktop ' ın, projeyle aynı işletim sistemine ayarlandığından emin olun.
- Dockerfile ' ın ilk aşamasında görüntüleri çekin (çoğu Dockerfiles içindeki `base` aşaması).  
- Dockerfile 'ı oluşturun ve kapsayıcıyı başlatın.

Warmup yalnızca **hızlı** modda gerçekleşecektir, bu nedenle çalışan kapsayıcıda uygulama klasörü birimi takılmış ve uygulamadaki tüm değişiklikler kapsayıcıyı geçersiz kılmaz. Bu nedenle, hata ayıklama performansı önemli ölçüde artar ve büyük görüntüleri çekme gibi uzun süre çalışan görevler için bekleme süresini azaltır.

## <a name="volume-mapping"></a>Birim eşleme

Kapsayıcılarda çalışan hata ayıklama için, Visual Studio hata ayıklayıcı ve NuGet klasörlerini konak makinesinden eşlemek için birim eşlemesi kullanır. Kapsayıcıda bağlanan birimler şunlardır:

|||
|-|-|
| **Uzaktan hata ayıklayıcı** | Proje türüne bağlı olarak kapsayıcıda hata ayıklayıcıyı çalıştırmak için gereken bitleri içerir. Bu konuda daha fazla bilgi açıklanmaktadır |[hata ayıklama](#debugging) bölümünde ayrıntılar.
| **Uygulama klasörü** | Dockerfile dosyasının bulunduğu proje klasörünü içerir.|
| **Kaynak klasör** | Docker komutlarına geçirilen yapı bağlamını içerir.|
| **NuGet paket klasörleri** | Projedeki *obj\{Project}. csproj. NuGet. g. props* dosyasından okunan NuGet paketlerini ve geri dönüş klasörlerini içerir. |

ASP.NET Core Web Apps için, SSL sertifikası ve Kullanıcı gizli dizileri için, sonraki bölümde daha ayrıntılı olarak açıklanan iki ek klasör olabilir.

## <a name="ssl-enabled-aspnet-core-apps"></a>SSL özellikli ASP.NET Core uygulamalar

Visual Studio 'daki kapsayıcı araçları, bir geliştirme sertifikasıyla SSL özellikli ASP.NET Core uygulamasında hata ayıklamayı destekler, bu sayede kapsayıcı olmadan çalışmayı beklemeniz gerekir. Bu işlemi gerçekleştirmek için, Visual Studio sertifikayı dışarı aktarmak ve kapsayıcı için kullanılabilir hale getirmek için birkaç adım daha ekler. Akış şu şekildedir:

1. Yerel geliştirme sertifikasının konak makinede `dev-certs` aracı aracılığıyla mevcut ve güvenilir olduğundan emin olun.
2. Sertifikayı bu belirli uygulama için Kullanıcı gizli dizileri deposunda depolanan güvenli bir parolayla%APPDATA%\ASP.NET\Https 'e aktarın.
3. Birim bağlama aşağıdaki dizinler:

   - *%AppData%\microsoft\usergizlilikler*
   - *%APPDATA%\ASP.NET\Https*

ASP.NET Core, *https* klasörü altındaki derleme adıyla eşleşen bir sertifika arar. Bu, neden bu yoldaki kapsayıcıya eşlendiğine ilişkin bir sertifikadır. Sertifika yolu ve parola, diğer bir deyişle, ortam değişkenleri (yani, `ASPNETCORE_Kestrel__Certificates__Default__Path` ve `ASPNETCORE_Kestrel__Certificates__Default__Password`) veya Kullanıcı parolaları JSON dosyası kullanılarak tanımlanabilir; örneğin:

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

Kapsayıcılarda ASP.NET Core uygulamalarla SSL kullanma hakkında daha fazla bilgi için bkz. [https üzerinden Docker Ile barındırma ASP.NET Core görüntüleri](https://docs.microsoft.com/aspnet/core/security/docker-https).

## <a name="debugging"></a>Hata Ayıklama

 Hata ayıklamayı başlattığınızda (**F5**), mümkünse daha önce başlatılmış bir kapsayıcı yeniden kullanılır. Önceki kapsayıcıyı yeniden kullanmak istemiyorsanız, Visual Studio 'Nun yeni bir kapsayıcı kullanmasını zorlamak için Visual Studio 'da **yeniden oluşturma** veya **Temizleme** komutlarını kullanabilirsiniz.

Hata ayıklayıcıyı çalıştırma işlemi proje ve kapsayıcı işletim sisteminin türüne bağlıdır:

|||
|-|-|
| **.NET Core Uygulamaları (Linux kapsayıcıları)**| Visual Studio `vsdbg` indirir ve kapsayıcıya eşler, ardından program ve bağımsız değişkenlerle (yani, `dotnet webapp.dll`) çağrılır ve sonra hata ayıklayıcı işleme iliştirir. |
| **.NET Core Uygulamaları (Windows kapsayıcıları)**| Visual Studio `onecoremsvsmon` kullanır ve kapsayıcıya eşler, giriş noktası olarak çalıştırır ve ardından Visual Studio buna bağlanır ve programınıza ekler. Bu, normalde uzak hata ayıklamayı başka bir bilgisayarda veya sanal makinede ayarlamaya benzer.|
| **.NET Framework uygulamalar** | Visual Studio `msvsmon` kullanır ve kapsayıcıya eşler, Visual Studio 'nun buna bağlanabildiği giriş noktasının bir parçası olarak çalıştırır ve programınıza iliştirir.|

`vsdbg.exe`hakkında bilgi için bkz. [Visual Studio 'Dan Linux ve OSX üzerinde .NET Core 'da hata ayıklama](https://github.com/Microsoft/MIEngine/wiki/Offroad-Debugging-of-.NET-Core-on-Linux---OSX-from-Visual-Studio).

## <a name="container-entry-point"></a>Kapsayıcı giriş noktası

Visual Studio, proje türüne ve kapsayıcı işletim sistemine bağlı olarak özel bir kapsayıcı giriş noktası kullanır, farklı birleşimler şunlardır:

|||
|-|-|
| **Linux kapsayıcıları** | Giriş noktası, kapsayıcının çalışır durumda tutulması için sonsuz bir bekleme olan `tail -f /dev/null`. Uygulama hata ayıklayıcı aracılığıyla başlatıldığında, uygulamayı çalıştırmanın (yani, `dotnet webapp.dll`) sorumlu olan hata ayıklayıcısıdır. Hata ayıklama olmadan başlatılmışsa, araç, uygulamayı çalıştırmak için bir `docker exec -i {containerId} dotnet webapp.dll` çalıştırır.|
| **Windows kapsayıcıları**| Giriş noktası, hata ayıklayıcıyı çalıştıran `C:\remote_debugger\x64\msvsmon.exe /noauth /anyuser /silent /nostatus` benzer bir şeydir, bu nedenle bağlantıları dinler. Aynı durum, hata ayıklayıcının uygulamayı çalıştırması ve hata ayıklama olmadan başlatıldığında bir `docker exec` komutu için geçerlidir. .NET Framework Web uygulamaları için giriş noktası, `ServiceMonitor`, komuta eklendiği biraz farklıdır.|
  
> [!NOTE]
> Kapsayıcı giriş noktası yalnızca Docker-Compose projelerinde değiştirilebilir, tek Kapsayıcılı projelerde kullanılamaz.

## <a name="next-steps"></a>Sonraki adımlar

Proje dosyalarınızda ek MSBuild özellikleri ayarlayarak derlemelerinizi nasıl özelleştireceğinizi öğrenin. Bkz. [kapsayıcı projeleri Için MSBuild özellikleri](container-msbuild-properties.md).

## <a name="see-also"></a>Ayrıca bkz.

[Windows 'da windows
Linux kapsayıcılarında](/virtualization/windowscontainers/deploy-containers/linux-containers)
[Dockerfile](/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile) [MSBuild](../msbuild/msbuild.md)
