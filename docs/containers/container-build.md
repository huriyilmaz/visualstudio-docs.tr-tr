---
title: Visual Studio kapsayıcı araçları derleme ve hata ayıklamasına genel bakış
author: ghogen
description: Kapsayıcı araçları derleme ve hata ayıklama işlemine genel bakış
ms.author: ghogen
ms.date: 11/20/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: 004427ced7d18d9a5af5c863172416fd8637aa69
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85536870"
---
# <a name="how-visual-studio-builds-containerized-apps"></a>Visual Studio’nun kapsayıcılı uygulama oluşturma şekli

Visual Studio IDE 'den oluşturuluyor veya bir komut satırı derlemesi ayarlıyoruz, Visual Studio 'Nun projelerinizi oluşturmak için Dockerfile 'ı nasıl kullandığını bilmeniz gerekir.  Performans nedenleriyle, Visual Studio Kapsayıcılı uygulamalar için özel bir işlem izler. Visual Studio 'Nun projelerinizi nasıl derlemediğini anlamak, Dockerfile dosyasını değiştirerek yapı işleminizi özelleştirirken özellikle önemlidir.

Visual Studio, Docker Kapsayıcıları kullanmayan bir proje oluşturduğunda, yerel makinede MSBuild 'i çağırır ve çıkış dosyalarını `bin` yerel çözüm klasörünüzün altında bir klasörde (genellikle) oluşturur. Bununla birlikte, kapsayıcılı bir proje için yapı işlemi, Dockerfile 'ın Kapsayıcılı uygulama oluşturma yönergelerinin bir hesabını alır. Visual Studio 'Nun kullandığı Dockerfile birden çok aşamaya bölünmüştür. Bu işlem Docker 'ın *çok aşamalı derleme* özelliğini kullanır.

## <a name="multistage-build"></a>Çok aşamalı derleme

Çoklu aşama oluşturma özelliği, kapsayıcıları oluşturma işleminin daha verimli olmasına yardımcı olur ve yalnızca uygulamanızın çalışma zamanında ihtiyaç duyacağı bitleri içermesine izin vererek kapsayıcıları daha küçük hale getirir. MultiStage derlemesi, .NET Framework projeleri değil .NET Core projeleri için kullanılır.

Hatlarında derlemesi, ara görüntü üreten aşamalarda kapsayıcı görüntülerinin oluşturulmasına izin verir. Örnek olarak, Visual Studio tarafından oluşturulan tipik bir Dockerfile 'ı düşünün; ilk aşama `base` :

```
FROM mcr.microsoft.com/dotnet/core/aspnet:2.2-stretch-slim AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443
```

Dockerfile 'daki çizgiler, Microsoft Container Registry (mcr.microsoft.com) ' dan Delinlü görüntüyle başlar ve `base` 80 ve 443 bağlantı noktalarını kullanıma sunan bir ara görüntü oluşturur ve çalışma dizinini olarak ayarlar `/app` .

Sonraki aşama `build` aşağıdaki gibi görünür:

```
FROM mcr.microsoft.com/dotnet/core/sdk:2.2-stretch AS build
WORKDIR /src
COPY ["WebApplication43/WebApplication43.csproj", "WebApplication43/"]
RUN dotnet restore "WebApplication43/WebApplication43.csproj"
COPY . .
WORKDIR "/src/WebApplication43"
RUN dotnet build "WebApplication43.csproj" -c Release -o /app
```

Aşamanın, temelden `build` `sdk` `aspnet` devam etmek yerine, kayıt defterinden (yerine) farklı bir orijinal görüntüden başlatıldığını görebilirsiniz.  `sdk`Görüntüde tüm derleme araçları bulunur ve bu nedenle yalnızca çalışma zamanı bileşenleri içeren ASPNET görüntüsünden çok daha büyük bir büyük olur. Dockerfile ' ın geri kalanına göz atadığınızda ayrı bir görüntü kullanmanın nedeni açık olur:

```
FROM build AS publish
RUN dotnet publish "WebApplication43.csproj" -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "WebApplication43.dll"]
```

Son aşama öğesinden bir kez daha başlar `base` ve `COPY --from=publish` yayımlanan çıktıyı son görüntüye kopyalamak için içerir. Bu işlem, görüntüde bulunan tüm derleme araçlarını içermesi gerekmiyorsa nihai görüntünün çok daha küçük olmasını mümkün kılar `sdk` .

## <a name="building-from-the-command-line"></a>Komut satırından oluşturma

Visual Studio dışında oluşturmak istiyorsanız, `docker build` veya kullanarak `MSBuild` komut satırından oluşturabilirsiniz.

### <a name="docker-build"></a>docker build

Komut satırından kapsayıcılı bir çözüm oluşturmak için, genellikle komutunu `docker build <context>` çözümdeki her proje için kullanabilirsiniz. *Yapı bağlamı* bağımsız değişkenini sağlarsınız. Dockerfile için *derleme bağlamı* , yerel makinedeki, görüntüyü oluşturmak için çalışma klasörü olarak kullanılan klasördür. Örneğin, kapsayıcıya kopyaladığınız sırada dosyaları kopyaladığınız klasördür.  .NET Core projelerinde, çözüm dosyasını (. sln) içeren klasörü kullanın.  Göreli yol olarak ifade edilen bu bağımsız değişken, genellikle proje klasöründeki bir Dockerfile ve onun üst klasöründeki çözüm dosyası için ".." olur.  .NET Framework projeleri için, yapı bağlamı çözüm klasörü değil, proje klasörüdür.

```cmd
docker build -f Dockerfile ..
```

### <a name="msbuild"></a>MSBuild

.NET Framework projeleri için Visual Studio tarafından oluşturulan dockerfiles (ve Visual Studio 2017 güncelleştirme 4 ' ten önceki Visual Studio sürümleriyle oluşturulan .NET Core projeleri için) çok aşamalı Dockerfiles değildir.  Bu Dockerfiles içindeki adımlar kodunuzu derlemez.  Bunun yerine, Visual Studio .NET Framework Dockerfile oluşturduğunda, öncelikle projenizi MSBuild kullanarak derler.  Bu başarılı olduğunda Visual Studio, yapı çıkışını MSBuild 'ten elde edilen Docker görüntüsüne kopyalayan Dockerfile öğesini oluşturur.  Kodunuzu derlemek için gereken adımlar Dockerfile 'a dahil edilmediğinden, komut satırından kullanarak .NET Framework Dockerfiles derlenemez `docker build` . Bu projeleri derlemek için MSBuild 'i kullanmanız gerekir.

Tek Docker kapsayıcı projesi için bir görüntü oluşturmak üzere, MSBuild 'i `/t:ContainerBuild` komut seçeneğiyle kullanabilirsiniz. Örneğin:

```cmd
MSBuild MyProject.csproj /t:ContainerBuild /p:Configuration=Release
```

Visual Studio IDE 'den Çözümünüzü oluştururken **Çıkış** penceresinde gördüklerinize benzer bir çıktı görürsünüz. Her zaman kullanın `/p:Configuration=Release` , Visual Studio 'nun çok aşamalı derleme iyileştirmesini kullandığı durumlarda, **hata ayıklama** yapılandırmasını oluştururken sonuçlar beklendiği gibi olmayabilir. Bkz. [hata ayıklama](#debugging).

Docker Compose projesi kullanıyorsanız, görüntü oluşturmak için bu komutu kullanın:

```cmd
msbuild /p:SolutionPath=<solution-name>.sln /p:Configuration=Release docker-compose.dcproj
```

## <a name="project-warmup"></a>Proje ısınma

*Proje ısınma* , bir proje için Docker profili seçildiğinde (yani, bir proje yüklendiğinde veya Docker desteği eklendiğinde), sonraki çalıştırmanın performansını artırmak için (**F5** veya **CTRL** + **F5**) oluşan bir dizi adımı ifade eder. Bu, **Araçlar**  >  **Seçenekler**  >  **kapsayıcı araçları**' nın altında yapılandırılabilir. Arka planda çalışan görevler şunlardır:

- Docker Desktop ' ın yüklü olduğundan ve çalıştığından emin olun.
- Docker Desktop ' ın, projeyle aynı işletim sistemine ayarlandığından emin olun.
- Resimleri Dockerfile 'ın ilk aşamasına ( `base` çoğu Dockerfiles içindeki aşama) çekin.  
- Dockerfile 'ı oluşturun ve kapsayıcıyı başlatın.

Warmup yalnızca **hızlı** modda gerçekleşecektir, bu nedenle çalışan kapsayıcıda birim takılmış uygulama klasörü olacaktır. Diğer bir deyişle, uygulamadaki tüm değişiklikler kapsayıcıyı geçersiz kılmaz. Bu nedenle, hata ayıklama performansı önemli ölçüde artar ve büyük görüntüleri çekme gibi uzun süre çalışan görevler için bekleme süresini azaltır.

## <a name="volume-mapping"></a>Birim eşleme

Kapsayıcılarda çalışan hata ayıklama için, Visual Studio hata ayıklayıcı ve NuGet klasörlerini konak makinesinden eşlemek için birim eşlemesi kullanır. Birim eşleme, [burada](https://docs.docker.com/storage/volumes/)Docker belgelerinde açıklanmıştır. Kapsayıcıda bağlanan birimler şunlardır:

|Birim|Description|
|-|-|
| **Uzaktan hata ayıklayıcı** | Proje türüne bağlı olarak kapsayıcıda hata ayıklayıcıyı çalıştırmak için gereken bitleri içerir. Bu konuda daha fazla bilgi açıklanmaktadır |[hata ayıklama](#debugging) bölümünde ayrıntılar.
| **Uygulama klasörü** | Dockerfile dosyasının bulunduğu proje klasörünü içerir.|
| **Kaynak klasör** | Docker komutlarına geçirilen yapı bağlamını içerir.|
| **NuGet paket klasörleri** | Projedeki *obj \{ projesi}. csproj. NuGet. g. props* dosyasından okunan NuGet paketlerini ve geri dönüş klasörlerini içerir. |

ASP.NET Core Web Apps için, SSL sertifikası ve Kullanıcı gizli dizileri için, sonraki bölümde daha ayrıntılı olarak açıklanan iki ek klasör olabilir.

## <a name="ssl-enabled-aspnet-core-apps"></a>SSL özellikli ASP.NET Core uygulamalar

Visual Studio 'daki kapsayıcı araçları, bir geliştirme sertifikasıyla SSL özellikli ASP.NET Core uygulamasında hata ayıklamayı destekler, bu sayede kapsayıcı olmadan çalışmayı beklemeniz gerekir. Bu işlemi gerçekleştirmek için, Visual Studio sertifikayı dışarı aktarmak ve kapsayıcı için kullanılabilir hale getirmek için birkaç adım daha ekler. Kapsayıcıda hata ayıklarken Visual Studio 'nun sizin için işlediği akış aşağıdadır:

1. Yerel geliştirme sertifikasının, araç aracılığıyla konak makinede mevcut ve güvenilir olmasını sağlar `dev-certs` .
2. Sertifikayı, bu belirli uygulama için Kullanıcı gizli dizileri deposunda depolanan güvenli bir parolayla%APPDATA%\ASP.NET\Https 'e aktarır.
3. Volume-aşağıdaki dizinleri takar:

   - *%AppData%\microsoft\usergizlilikler*
   - *%APPDATA%\ASP.NET\Https*

ASP.NET Core, *https* klasörü altındaki derleme adıyla eşleşen bir sertifika arar. Bu, neden bu yoldaki kapsayıcıya eşlendiğine ilişkin bir sertifikadır. Sertifika yolu ve parolası alternatif olarak, ortam değişkenleri (yani, `ASPNETCORE_Kestrel__Certificates__Default__Path` ve `ASPNETCORE_Kestrel__Certificates__Default__Password` ) kullanılarak veya Kullanıcı gizli dizileri JSON dosyasında tanımlanabilir, örneğin:

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

Yapılandırmanız Kapsayıcılı ve kapsayıcısız yapıları destekliyorsa, yollar kapsayıcı ortamına özgü olduğundan ortam değişkenlerini kullanmanız gerekir.

Kapsayıcılarda ASP.NET Core uygulamalarla SSL kullanma hakkında daha fazla bilgi için bkz. [https üzerinden Docker Ile barındırma ASP.NET Core görüntüleri](/aspnet/core/security/docker-https).

## <a name="debugging"></a>Hata Ayıklama

**Hata ayıklama** yapılandırmasında oluştururken, Visual Studio 'nun Kapsayıcılı projelere yönelik yapı sürecinin performansına yardımcı olan birkaç iyileştirmesi vardır. Kapsayıcılı uygulamalar için derleme işlemi, Dockerfile içinde özetlenen adımları takip etmek kadar basit değildir. Kapsayıcıda derleme, yerel makinede oluşturmaktan çok daha yavaştır.  Bu nedenle, **hata ayıklama** yapılandırmasında derleme yaparken, Visual Studio projelerinizi gerçekten yerel makinede oluşturur ve ardından çıkış klasörünü birim bağlama kullanarak kapsayıcınıza paylaşır. Bu iyileştirme etkin olan bir yapıya *hızlı* mod oluşturma denir.

**Hızlı** modda, Visual Studio, `docker build` Docker 'ın yalnızca aşamayı oluşturmasını söyleyen bir bağımsız değişkenle çağırır `base` .  Visual Studio, Dockerfile içeriğiyle ilgili olarak işlemin geri kalanını işler. Bu nedenle, kapsayıcı ortamını özelleştirmek veya ek bağımlılıklar yüklemek gibi Dockerfile 'ı değiştirdiğinizde, değişikliklerinizi ilk aşamada koymanız gerekir.  Dockerfile 'ın `build` , veya aşamalarına yerleştirilmiş özel adımlar `publish` `final` yürütülmez.

Bu performans iyileştirmesi yalnızca **hata ayıklama** yapılandırmasında derleme yaparken oluşur. **Yayın** yapılandırmasında, yapı, Dockerfile içinde belirtildiği gibi kapsayıcıda oluşur.

Dockerfile tarafından belirtildiği gibi performans iyileştirmesini ve derlemeyi devre dışı bırakmak istiyorsanız, proje dosyasında şu şekilde **Containerdevelopmentmode** özelliğini **normal** olarak ayarlayın:

```xml
<PropertyGroup>
   <ContainerDevelopmentMode>Regular</ContainerDevelopmentMode>
</PropertyGroup>
```

Performans iyileştirmesini geri yüklemek için, özelliği proje dosyasından kaldırın.

 Hata ayıklamayı başlattığınızda (**F5**), mümkünse daha önce başlatılmış bir kapsayıcı yeniden kullanılır. Önceki kapsayıcıyı yeniden kullanmak istemiyorsanız, Visual Studio 'Nun yeni bir kapsayıcı kullanmasını zorlamak için Visual Studio 'da **yeniden oluşturma** veya **Temizleme** komutlarını kullanabilirsiniz.

Hata ayıklayıcıyı çalıştırma işlemi proje ve kapsayıcı işletim sisteminin türüne bağlıdır:

|Senaryo|Hata ayıklayıcı işlemi|
|-|-|
| **.NET Core Uygulamaları (Linux kapsayıcıları)**| Visual Studio indirir `vsdbg` ve kapsayıcıya eşler, ardından program ve bağımsız değişkenler (yani) ile çağırılır `dotnet webapp.dll` ve sonra hata ayıklayıcı işleme iliştirir. |
| **.NET Core Uygulamaları (Windows kapsayıcıları)**| Visual Studio tarafından kullanılır `onecoremsvsmon` ve kapsayıcıya eşlenir, giriş noktası olarak çalışır ve ardından Visual Studio buna bağlanır ve programınıza ekler. Bu, normalde uzak hata ayıklamayı başka bir bilgisayarda veya sanal makinede ayarlamaya benzer.|
| **.NET Framework uygulamalar** | Visual Studio tarafından kullanılır `msvsmon` ve kapsayıcıya eşlenir, Visual Studio 'nun buna bağlanabildiği giriş noktasının bir parçası olarak çalışır ve programınıza iliştirir.|

Hakkında bilgi için `vsdbg.exe` bkz. [Visual Studio 'dan Linux ve OSX üzerinde .NET Core 'da hata ayıklama](https://github.com/Microsoft/MIEngine/wiki/Offroad-Debugging-of-.NET-Core-on-Linux---OSX-from-Visual-Studio).

## <a name="container-entry-point"></a>Kapsayıcı giriş noktası

Visual Studio, proje türüne ve kapsayıcı işletim sistemine bağlı olarak özel bir kapsayıcı giriş noktası kullanır, farklı birleşimler şunlardır:

|Kapsayıcı türü|Giriş noktası|
|-|-|
| **Linux kapsayıcıları** | Giriş noktası `tail -f /dev/null` , kapsayıcının çalışır durumda tutulması için sonsuz bir bekleme olur. Uygulama hata ayıklayıcı aracılığıyla başlatıldığında, uygulamayı çalıştırmaktan sorumlu olan hata ayıklayıcısıdır (yani, `dotnet webapp.dll` ). Hata ayıklama olmadan başlatıldığında araç, `docker exec -i {containerId} dotnet webapp.dll` uygulamayı çalıştırmak için bir çalıştırır.|
| **Windows kapsayıcıları**| Giriş noktası, `C:\remote_debugger\x64\msvsmon.exe /noauth /anyuser /silent /nostatus` hata ayıklayıcıyı çalıştıran benzer bir şeydir, bu nedenle bağlantıları dinler. Aynı durum, hata ayıklayıcının uygulamayı çalıştırması ve `docker exec` hata ayıklama olmadan başlatıldığında bir komut için geçerlidir. .NET Framework Web uygulamaları için giriş noktası, `ServiceMonitor` komuta eklenen biraz farklıdır.|

Kapsayıcı giriş noktası yalnızca Docker-Compose projelerinde değiştirilebilir, tek Kapsayıcılı projelerde kullanılamaz.

## <a name="next-steps"></a>Sonraki adımlar

Proje dosyalarınızda ek MSBuild özellikleri ayarlayarak derlemelerinizi nasıl özelleştireceğinizi öğrenin. Bkz. [kapsayıcı projeleri Için MSBuild özellikleri](container-msbuild-properties.md).

## <a name="see-also"></a>Ayrıca bkz.

[MSBuild](../msbuild/msbuild.md) 
 Windows üzerinde Dockerfile [Dockerfile on Windows](/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile) 
 [Windows 'Da Linux kapsayıcıları](/virtualization/windowscontainers/deploy-containers/linux-containers)
