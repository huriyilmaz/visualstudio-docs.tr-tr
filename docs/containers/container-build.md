---
title: Visual Studio Kapsayıcı araçları derleme ve hata ayıklamasına genel bakış
author: ghogen
description: Kapsayıcı araçları derleme ve hata ayıklama işlemine genel bakış
ms.author: ghogen
ms.date: 03/15/2021
ms.technology: vs-container-tools
ms.topic: conceptual
ms.openlocfilehash: 7e7b80aa144dfb1cbef88c27a3fe09478c91c268ca6b8f9dea6390148b3a2e0d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121347941"
---
# <a name="how-visual-studio-builds-containerized-apps"></a>Visual Studio’nun kapsayıcılı uygulama oluşturma şekli

Visual Studio ıde 'den oluşturuluyor veya bir komut satırı derlemesi ayarlıyoruz, projelerinizi oluşturmak için Visual Studio dockerfile 'ı nasıl kullandığını bilmeniz gerekir.  performans nedenleriyle, kapsayıcılı uygulamalar için özel bir işlem takip Visual Studio. Visual Studio projenizin nasıl oluşturulduğunu anlamak, dockerfile 'ı değiştirerek yapı işleminizi özelleştirirken özellikle önemlidir.

Visual Studio docker kapsayıcıları kullanmayan bir proje oluşturduğunda, yerel makinede MSBuild çağırır ve çıkış dosyalarını `bin` yerel çözüm klasörünüzün altında bir klasörde (genellikle) oluşturur. Bununla birlikte, kapsayıcılı bir proje için yapı işlemi, Dockerfile 'ın Kapsayıcılı uygulama oluşturma yönergelerinin bir hesabını alır. Visual Studio kullanılan dockerfile birden çok aşamaya ayrılmıştır. Bu işlem Docker 'ın *çok aşamalı derleme* özelliğini kullanır.

## <a name="multistage-build"></a>Çok aşamalı derleme

Çoklu aşama oluşturma özelliği, kapsayıcıları oluşturma işleminin daha verimli olmasına yardımcı olur ve yalnızca uygulamanızın çalışma zamanında ihtiyaç duyacağı bitleri içermesine izin vererek kapsayıcıları daha küçük hale getirir. multistage derlemesi, .NET Framework projeleri değil .net Core projeleri için kullanılır.

Hatlarında derlemesi, ara görüntü üreten aşamalarda kapsayıcı görüntülerinin oluşturulmasına izin verir. örnek olarak, Visual Studio tarafından oluşturulan tipik bir dockerfile 'ı düşünün; ilk aşama `base` :

```
FROM mcr.microsoft.com/dotnet/aspnet:3.1-buster-slim AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443
```

dockerfile 'daki çizgiler, Microsoft Container Registry (mcr.microsoft.com) ' dan delinlü görüntüyle başlar ve `base` 80 ve 443 bağlantı noktalarını kullanıma sunan bir ara görüntü oluşturur ve çalışma dizinini olarak ayarlar `/app` .

Sonraki aşama `build` aşağıdaki gibi görünür:

```
FROM mcr.microsoft.com/dotnet/sdk:3.1-buster-slim AS build
WORKDIR /src
COPY ["WebApplication43/WebApplication43.csproj", "WebApplication43/"]
RUN dotnet restore "WebApplication43/WebApplication43.csproj"
COPY . .
WORKDIR "/src/WebApplication43"
RUN dotnet build "WebApplication43.csproj" -c Release -o /app/build
```

Aşamanın, temelden `build` `sdk` `aspnet` devam etmek yerine, kayıt defterinden (yerine) farklı bir orijinal görüntüden başlatıldığını görebilirsiniz.  `sdk`Görüntüde tüm derleme araçları bulunur ve bu nedenle yalnızca çalışma zamanı bileşenleri içeren ASPNET görüntüsünden çok daha büyük bir büyük olur. Dockerfile ' ın geri kalanına göz atadığınızda ayrı bir görüntü kullanmanın nedeni açık olur:

```
FROM build AS publish
RUN dotnet publish "WebApplication43.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "WebApplication43.dll"]
```

Son aşama öğesinden bir kez daha başlar `base` ve `COPY --from=publish` yayımlanan çıktıyı son görüntüye kopyalamak için içerir. Bu işlem, görüntüde bulunan tüm derleme araçlarını içermesi gerekmiyorsa nihai görüntünün çok daha küçük olmasını mümkün kılar `sdk` .

## <a name="building-from-the-command-line"></a>Komut satırından oluşturma

Visual Studio dışında oluşturmak istiyorsanız, `docker build` `MSBuild` komut satırından oluşturmak için veya kullanabilirsiniz.

### <a name="docker-build"></a>docker build

Komut satırından kapsayıcılı bir çözüm oluşturmak için, genellikle komutunu `docker build <context>` çözümdeki her proje için kullanabilirsiniz. *Yapı bağlamı* bağımsız değişkenini sağlarsınız. Dockerfile için *derleme bağlamı* , yerel makinedeki, görüntüyü oluşturmak için çalışma klasörü olarak kullanılan klasördür. Örneğin, kapsayıcıya kopyaladığınız sırada dosyaları kopyaladığınız klasördür.  .NET Core projelerinde, çözüm dosyasını (. sln) içeren klasörü kullanın.  Göreli yol olarak ifade edilen bu bağımsız değişken, genellikle proje klasöründeki bir Dockerfile ve onun üst klasöründeki çözüm dosyası için ".." olur.  .NET Framework projeleri için, yapı bağlamı çözüm klasörü değil, proje klasörüdür.

```cmd
docker build -f Dockerfile ..
```

### <a name="msbuild"></a>MSBuild

.NET Framework projeleri için Visual Studio tarafından oluşturulan dockerfiles (ve Visual Studio 2017 güncelleştirme 4 ' ten önce Visual Studio sürümleriyle oluşturulan .net Core projeleri için) çok aşamalı dockerfiles değildir.  Bu Dockerfiles içindeki adımlar kodunuzu derlemez.  bunun yerine, Visual Studio bir .NET Framework dockerfile oluşturduğunda, önce projenizi MSBuild kullanarak derler.  bu başarılı olduğunda Visual Studio daha sonra dockerfile 'ı oluşturur. bu, derleme çıkışını MSBuild oluşturulan docker görüntüsüne kopyalamaktır.  kodunuzu derlemek için gereken adımlar dockerfile 'a dahil edilmediğinden, komut satırından kullanarak .NET Framework dockerfiles derlenemez `docker build` . bu projeleri derlemek için MSBuild kullanmanız gerekir.

tek docker kapsayıcı projesi için bir görüntü oluşturmak üzere `/t:ContainerBuild` komut seçeneğiyle MSBuild kullanabilirsiniz. Örnek:

```cmd
MSBuild MyProject.csproj /t:ContainerBuild /p:Configuration=Release
```

çözümünüzü Visual Studio ıde 'den oluştururken **çıkış** penceresinde gördüklerinize benzer bir çıktı görürsünüz. her zaman kullan `/p:Configuration=Release` , Visual Studio çok aşamalı derleme iyileştirmesini kullandığı durumlarda, **hata ayıklama** yapılandırmasını oluştururken sonuçlar beklendiği gibi olmayabilir. Bkz. [hata ayıklama](#debugging).

Docker Compose projesi kullanıyorsanız, görüntü oluşturmak için bu komutu kullanın:

```cmd
msbuild /p:SolutionPath=<solution-name>.sln /p:Configuration=Release docker-compose.dcproj
```

## <a name="project-warmup"></a>Project ısınma

*Project ısınma* , bir proje için docker profili seçildiğinde (yani, bir proje yüklendiğinde veya docker desteği eklendiğinde), sonraki çalıştırmanın performansını artırmak için (**f5** veya **Ctrl** + **f5**) oluşan bir dizi adımı ifade eder. Bu, **Araçlar**  >  **Seçenekler**  >  **kapsayıcı araçları**' nın altında yapılandırılabilir. Arka planda çalışan görevler şunlardır:

- Docker Desktop ' ın yüklü olduğundan ve çalıştığından emin olun.
- Docker Desktop ' ın, projeyle aynı işletim sistemine ayarlandığından emin olun.
- Resimleri Dockerfile 'ın ilk aşamasına ( `base` çoğu Dockerfiles içindeki aşama) çekin.  
- Dockerfile 'ı oluşturun ve kapsayıcıyı başlatın.

Warmup yalnızca **hızlı** modda gerçekleşecektir, bu nedenle çalışan kapsayıcıda birim takılmış uygulama klasörü olacaktır. Diğer bir deyişle, uygulamadaki tüm değişiklikler kapsayıcıyı geçersiz kılmaz. Bu nedenle, hata ayıklama performansı önemli ölçüde artar ve büyük görüntüleri çekme gibi uzun süre çalışan görevler için bekleme süresini azaltır.

## <a name="volume-mapping"></a>Birim eşleme

kapsayıcılarda çalışırken hata ayıklama için Visual Studio, konak makinesinden hata ayıklayıcı ve NuGet klasörlerini eşlemek için birim eşlemesi kullanır. Birim eşleme, [burada](https://docs.docker.com/storage/volumes/)Docker belgelerinde açıklanmıştır. Kapsayıcıda bağlanan birimler şunlardır:

|Birim|Açıklama|
|-|-|
| **Uzaktan hata ayıklayıcı** | Proje türüne bağlı olarak kapsayıcıda hata ayıklayıcıyı çalıştırmak için gereken bitleri içerir. Bu, [hata ayıklama](#debugging) bölümünde daha ayrıntılı olarak açıklanmıştır.|
| **Uygulama klasörü** | Dockerfile dosyasının bulunduğu proje klasörünü içerir.|
| **Kaynak klasör** | Docker komutlarına geçirilen yapı bağlamını içerir.|
| **NuGet paket klasörleri** | projedeki *obj \{ projesi}. csproj. NuGet. g. props* dosyasından okunan NuGet paketlerini ve geri dönüş klasörlerini içerir. |

ASP.NET çekirdek web uygulamaları için, SSL sertifikası ve kullanıcı gizli dizileri için, sonraki bölümde daha ayrıntılı olarak açıklanan iki ek klasör olabilir.

## <a name="ssl-enabled-aspnet-core-apps"></a>SSL özellikli ASP.NET Core uygulamalar

Visual Studio kapsayıcı araçları, bir geliştirme sertifikasıyla SSL özellikli ASP.NET çekirdek uygulamasında hata ayıklamayı destekler, bu sayede kapsayıcı olmadan çalışmayı beklemeniz gerekir. bunu yapmak için Visual Studio sertifikayı dışarı aktarmak ve kapsayıcı için kullanılabilir hale getirmek için birkaç adım daha ekler. kapsayıcıda hata ayıklarken Visual Studio işleyen akış aşağıda verilmiştir:

1. Yerel geliştirme sertifikasının, araç aracılığıyla konak makinede mevcut ve güvenilir olmasını sağlar `dev-certs` .
2. sertifikayı bu belirli uygulama için kullanıcı gizli dizileri deposunda depolanan güvenli bir parolayla% APPDATA% \ ASP.NET \https öğesine dışarı aktarır.
3. Volume-aşağıdaki dizinleri takar:

   - *%AppData%\microsoft\usergizlilikler*
   - *% APPDATA% \ ASP.NET \https*

ASP.NET Core, *Https* klasörü altındaki derleme adıyla eşleşen bir sertifika arar. bu, neden bu yoldaki kapsayıcıya eşlendiğine ilişkin bir sertifikadır. Sertifika yolu ve parolası alternatif olarak, ortam değişkenleri (yani, `ASPNETCORE_Kestrel__Certificates__Default__Path` ve `ASPNETCORE_Kestrel__Certificates__Default__Password` ) kullanılarak veya Kullanıcı gizli dizileri JSON dosyasında tanımlanabilir, örneğin:

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

kapsayıcılarda ASP.NET Core uygulamalarla SSL kullanma hakkında daha fazla bilgi için bkz. [HTTPS üzerinden docker ile barındırma ASP.NET Core görüntüleri](/aspnet/core/security/docker-https).

## <a name="debugging"></a>Hata Ayıklama

**hata ayıklama** yapılandırmasında oluştururken, kapsayıcılı projelere yönelik yapı sürecinin performansına yardımcı olan Visual Studio birkaç iyileştirme vardır. Kapsayıcılı uygulamalar için derleme işlemi, Dockerfile içinde özetlenen adımları takip etmek kadar basit değildir. Kapsayıcıda derleme, yerel makinede oluşturmaktan çok daha yavaştır.  bu nedenle, **hata ayıklama** yapılandırmasında derleme yaptığınızda Visual Studio, projenizi yerel makinede oluşturur ve ardından çıkış klasörünü birim bağlama kullanarak kapsayıcıya paylaşır. Bu iyileştirme etkin olan bir yapıya *hızlı* mod oluşturma denir.

**hızlı** modda, `docker build` docker 'ın yalnızca aşamayı oluşturmasını söyleyen bir bağımsız değişkenle çağrılar Visual Studio `base` .  Visual Studio, dockerfile içeriğiyle ilgili olarak işlemin geri kalanını işler. Bu nedenle, kapsayıcı ortamını özelleştirmek veya ek bağımlılıklar yüklemek gibi Dockerfile 'ı değiştirdiğinizde, değişikliklerinizi ilk aşamada koymanız gerekir.  Dockerfile 'ın `build` , veya aşamalarına yerleştirilmiş özel adımlar `publish` `final` yürütülmez.

Bu performans iyileştirmesi yalnızca **hata ayıklama** yapılandırmasında derleme yaparken oluşur. **Yayın** yapılandırmasında, yapı, Dockerfile içinde belirtildiği gibi kapsayıcıda oluşur.

Dockerfile tarafından belirtildiği gibi performans iyileştirmesini ve derlemeyi devre dışı bırakmak istiyorsanız, proje dosyasında şu şekilde **Containerdevelopmentmode** özelliğini **normal** olarak ayarlayın:

```xml
<PropertyGroup>
   <ContainerDevelopmentMode>Regular</ContainerDevelopmentMode>
</PropertyGroup>
```

Performans iyileştirmesini geri yüklemek için, özelliği proje dosyasından kaldırın.

 Hata ayıklamayı başlattığınızda (**F5**), mümkünse daha önce başlatılmış bir kapsayıcı yeniden kullanılır. önceki kapsayıcıyı yeniden kullanmak istemiyorsanız, Visual Studio yeni bir kapsayıcı kullanmaya zorlamak için Visual Studio **yeniden oluşturma** veya **temizleme** komutlarını kullanabilirsiniz.

Hata ayıklayıcıyı çalıştırma işlemi proje ve kapsayıcı işletim sisteminin türüne bağlıdır:

|Senaryo|Hata ayıklayıcı işlemi|
|-|-|
| **.NET Core Uygulamaları (Linux kapsayıcıları)**| Visual Studio indirir `vsdbg` ve kapsayıcıya eşler, ardından program ve bağımsız değişkenler (yani) ile çağırılır `dotnet webapp.dll` ve sonra hata ayıklayıcı işleme iliştirir. |
| **.net Core uygulamaları (Windows kapsayıcılar)**| Visual Studio kullanır `onecoremsvsmon` ve kapsayıcıya eşler, bunu giriş noktası olarak çalıştırır ve sonra Visual Studio ve programınıza ekler. Bu, normalde uzak hata ayıklamayı başka bir bilgisayarda veya sanal makinede ayarlamaya benzer.|
| **.NET Framework uygulamalar** | Visual Studio kullanır `msvsmon` ve kapsayıcıya eşler, bunu Visual Studio bağlanabileceği giriş noktasının bir parçası olarak çalıştırır ve programınıza iliştirir.|

Hakkında bilgi için `vsdbg.exe` bkz. [Linux ve OSX üzerinde .NET Core 'da Visual Studio hata ayıklama](https://github.com/Microsoft/MIEngine/wiki/Offroad-Debugging-of-.NET-Core-on-Linux---OSX-from-Visual-Studio).

## <a name="container-entry-point"></a>Kapsayıcı giriş noktası

Visual Studio, proje türüne ve kapsayıcı işletim sistemine bağlı olarak özel bir kapsayıcı giriş noktası kullanır, farklı birleşimler şunlardır:

|Kapsayıcı türü|Giriş noktası|
|-|-|
| **Linux kapsayıcıları** | Giriş noktası `tail -f /dev/null` , kapsayıcının çalışır durumda tutulması için sonsuz bir bekleme olur. Uygulama hata ayıklayıcı aracılığıyla başlatıldığında, uygulamayı çalıştırmaktan sorumlu olan hata ayıklayıcısıdır (yani, `dotnet webapp.dll` ). Hata ayıklama olmadan başlatıldığında araç, `docker exec -i {containerId} dotnet webapp.dll` uygulamayı çalıştırmak için bir çalıştırır.|
| **Windows kapsayıcıları**| Giriş noktası, `C:\remote_debugger\x64\msvsmon.exe /noauth /anyuser /silent /nostatus` hata ayıklayıcıyı çalıştıran benzer bir şeydir, bu nedenle bağlantıları dinler. Aynı durum, hata ayıklayıcının uygulamayı çalıştırması ve `docker exec` hata ayıklama olmadan başlatıldığında bir komut için geçerlidir. .NET Framework web uygulamaları için giriş noktası, `ServiceMonitor` komuta eklenen biraz farklıdır.|

Kapsayıcı giriş noktası yalnızca Docker-Compose projelerinde değiştirilebilir, tek Kapsayıcılı projelerde kullanılamaz.

## <a name="next-steps"></a>Sonraki adımlar

proje dosyalarınızda ek MSBuild özellikler ayarlayarak derlemelerinizi nasıl özelleştireceğinizi öğrenin. bkz. [kapsayıcı projeleri için MSBuild özellikleri](container-msbuild-properties.md).

## <a name="see-also"></a>Ayrıca bkz.

[MSBuild](../msbuild/msbuild.md) 
 Windows Dockerfile [](/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile) 
 [Windows Linux kapsayıcıları](/virtualization/windowscontainers/deploy-containers/linux-containers)
