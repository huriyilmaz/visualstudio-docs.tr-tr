---
title: Visual Studio Kapsayıcı Araçları derleme ve hata ayıklamaya genel bakış
author: ghogen
description: Kapsayıcı Araçları derleme ve hata ayıklama sürecine genel bakış
ms.author: ghogen
ms.date: 03/15/2021
ms.technology: vs-container-tools
ms.topic: conceptual
ms.openlocfilehash: 80b7cbbb70cea593d770017bb50f8a69eeb13c38
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631790"
---
# <a name="how-visual-studio-builds-containerized-apps"></a>Visual Studio’nun kapsayıcılı uygulama oluşturma şekli

Visual Studio IDE'den derleme yapmak veya bir komut satırı derlemesi oluşturmak Visual Studio projelerinizi derlemek için Dockerfile'ı nasıl kullandığını bilmek gerekir.  Performans nedenleriyle, Visual Studio uygulamalar için özel bir işlem izlersiniz. Dockerfile Visual Studio ı değiştirerek derleme işleminizi özelleştirerek projelerinizi nasıl derlemeniz konusunda özellikle önemlidir.

Visual Studio Docker kapsayıcılarını kullanmayan bir proje derlemesi, yerel makinede MSBuild'i çağırır ve çıkış dosyalarını yerel çözüm klasörünüz altındaki bir klasörde (genellikle `bin` ) oluşturur. Ancak kapsayıcılı bir proje için derleme işlemi, Dockerfile'ın kapsayıcılı uygulamayı derleme yönergelerini dikkate alır. Uygulama tarafından Visual Studio Dockerfile birden çok aşamaya ayrılır. Bu işlem Docker'ın çok yönlü *derleme özelliğine* dayandırır.

## <a name="multistage-build"></a>Çok parçalı derleme

Çok hızlı derleme özelliği, kapsayıcı oluşturma işlemini daha verimli hale getirir ve kapsayıcıların yalnızca çalışma zamanında uygulamanıza gereken bitleri içermelerine olanak sağlayarak kapsayıcıları daha küçük hale getirir. Çok yönlü derleme, .NET Core projeleri için kullanılır, .NET Framework kullanılır.

Çok aşamalı derleme, kapsayıcı görüntülerinin ara görüntüler üreten aşamalarda oluşturularak oluşturulamalarını sağlar. Örneğin, Visual Studio tarafından oluşturulan tipik bir Dockerfile düşünün. İlk `base` aşama:

```
FROM mcr.microsoft.com/dotnet/aspnet:3.1-buster-slim AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443
```

Dockerfile'daki satırlar, Microsoft Container Registry'den (mcr.microsoft.com) Debian görüntüsüyle başlar ve 80 ve 443 bağlantı noktalarını ortaya çıkararak çalışma dizinini olarak ayaran bir ara görüntü `base` `/app` oluşturun.

Sonraki aşama, `build` aşağıdaki gibi görünen aşamasıdır:

```
FROM mcr.microsoft.com/dotnet/sdk:3.1-buster-slim AS build
WORKDIR /src
COPY ["WebApplication43/WebApplication43.csproj", "WebApplication43/"]
RUN dotnet restore "WebApplication43/WebApplication43.csproj"
COPY . .
WORKDIR "/src/WebApplication43"
RUN dotnet build "WebApplication43.csproj" -c Release -o /app/build
```

Aşamanın temelden devam etmek yerine kayıt defterinden farklı bir özgün görüntüden `build` ( yerine ) başlat olduğunu `sdk` `aspnet` görüyorsunuz.  Görüntüde tüm derleme araçları vardır ve bu nedenle yalnızca çalışma zamanı bileşenlerini içeren `sdk` aspnet görüntüsünden çok daha büyüktür. Dockerfile dosyasının geri kalanına bakarak ayrı bir görüntü kullanmanın nedeni netleşir:

```
FROM build AS publish
RUN dotnet publish "WebApplication43.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "WebApplication43.dll"]
```

Son aşama, 'den yeniden `base` başlar ve yayımlanan çıkışı son `COPY --from=publish` görüntüye kopyalamak için içerir. Bu işlem son görüntünün çok daha küçük olması için mümkün olur çünkü görüntüde yer alan tüm derleme araçlarını içermesi `sdk` gerekli değildir.

## <a name="building-from-the-command-line"></a>Komut satırdan bina

Komut satırı dışında derlemek Visual Studio, komut satırına `docker build` veya `MSBuild` kullanarak derlemek için kullanabilirsiniz.

### <a name="docker-build"></a>docker build

Komut satırdan kapsayıcılı bir çözüm oluşturmak için genellikle çözümde her `docker build <context>` proje için komutunu kullanabilirsiniz. Derleme bağlamı bağımsız *değişkenlerini sağlar.* *Dockerfile* için derleme bağlamı, görüntüyü oluşturmak için çalışma klasörü olarak kullanılan yerel makinedeki klasördür. Örneğin, kapsayıcıya kopyalayıp dosyaları kopyalayıp bu klasöre kopyalamanız gerekir.  .NET Core projelerinde çözüm dosyasını (.sln) içeren klasörü kullanın.  Göreli yol olarak ifade ifade eden bu bağımsız değişken genellikle bir proje klasöründeki Dockerfile için ".." ve üst klasöründeki çözüm dosyasıdır.  Bu .NET Framework için derleme bağlamı çözüm klasörü değil proje klasörüdür.

```cmd
docker build -f Dockerfile ..
```

### <a name="msbuild"></a>MSBuild

Visual Studio projeleri (.NET Framework 2017 Güncelleştirme 4'den önceki Visual Studio sürümleriyle oluşturulan .NET Core projeleri için) Visual Studio tarafından oluşturulan Dockerfile'lar çok yönlü Dockerfiles değildir.  Bu Dockerfile'larda yer alan adımlar kodunuzu derlemez.  Bunun yerine, Visual Studio dockerfile .NET Framework, önce projenizi derlemek için MSBuild.  Bu başarılı olduğunda, Visual Studio dockerfile'ı oluşturur ve bu da yalnızca MSBuild docker görüntüsüne kopyalar.  Kodunuzu derleme adımları Dockerfile içinde yer alamaysa da, komut .NET Framework kullanarak Dockerfiles'ı `docker build` derleyemezsiniz. Bu projeleri derlemek MSBuild için MSBuild gerekir.

Tek docker kapsayıcı projesine bir görüntü oluşturmak için MSBuild komutunu `/t:ContainerBuild` kullanabilirsiniz. Örnek:

```cmd
MSBuild MyProject.csproj /t:ContainerBuild /p:Configuration=Release
```

Çözümlerinizi IDE'den derlemek için **Çıkış** penceresinde gördüğünüze benzer bir Visual Studio görebilirsiniz. Her zaman kullanın çünkü çok Visual Studio derleme iyileştirmesi kullandığı durumlarda Hata Ayıklama yapılandırması oluşturma sonuçları `/p:Configuration=Release` beklendiği gibi  olmayacaktır. Bkz. [Hata Ayıklama.](#debugging)

Docker Compose projesini kullanıyorsanız, görüntü oluşturmak için şu komutu kullanın:

```cmd
msbuild /p:SolutionPath=<solution-name>.sln /p:Configuration=Release docker-compose.dcproj
```

## <a name="project-warmup"></a>Project sıcaklığı

*Project bir* proje için Docker profili seçildiğinde (bir proje yüklendiğinde veya Docker desteği ekleniyorsa) sonraki çalıştırmaların performansını geliştirmek için 2018'de 100'e kadar olan bir dizi adımı ifade eder (**F5** veya **Ctrl** + **F5**). Bu, Araçlar Seçenekler Kapsayıcı **Araçları**  >    >  **altında yapılandırılabilir.** Arka planda çalıştıracak görevler şu şekildedir:

- Docker Desktop'ın yüklü ve çalışıyor olup olduğunu kontrol edin.
- Docker Desktop'ın projeyle aynı işletim sistemine ayarlanmış olduğundan emin olmak.
- Dockerfile'ın ilk aşamasındaki (çoğu Dockerfile'daki `base` aşama) görüntüleri çekin.  
- Dockerfile'ı derleme ve kapsayıcıyı başlatma.

Isınma yalnızca Hızlı **modda** gerçekleşecektir, bu nedenle çalışan kapsayıcıda uygulama klasörü birimine bağlı olur. Bu, uygulamada yapılan tüm değişikliklerin kapsayıcıyı geçersiz kılınmay anlamına gelir. Bu sayede hata ayıklama performansı önemli ölçüde artar ve büyük görüntüleri çekme gibi uzun süre çalışan görevler için bekleme süresi kısalır.

## <a name="volume-mapping"></a>Birim eşleme

Hata ayıklamanın kapsayıcılarda çalışması için Visual Studio makineden hata ayıklayıcıyı eşlemek ve NuGet klasörlerini eşlemek için birim eşlemesi kullanır. Birim eşlemesi buradaki Docker belgelerinde [açıklanmıştır.](https://docs.docker.com/storage/volumes/) Kapsayıcılar penceresini kullanarak kapsayıcının birim eşlemelerini görüntü [Visual Studio.](view-and-diagnose-containers.md)

Kapsayıcınıza bağlanan birimler şu şekildedir:

|Birim|Description|
|-|-|
| **Uzaktan hata ayıklayıcı** | Proje türüne bağlı olarak kapsayıcıda hata ayıklayıcısını çalıştırmak için gereken bitleri içerir. Bu, Hata Ayıklama bölümünde daha ayrıntılı [olarak açıklanmıştır.](#debugging)|
| **Uygulama klasörü** | Dockerfile dosyasının bulunduğu proje klasörünü içerir.|
| **Kaynak klasör** | Docker komutlarına geçirilen derleme bağlamını içerir.|
| **NuGet klasörlerini oluşturma** | Projedeki NuGet *\{ proje}.csproj.nuget.g.props* dosyasından okunan uygulama paketlerini ve geri dönüş klasörlerini içerir. |

Temel ASP.NET web uygulamaları için SSL sertifikası ve kullanıcı gizli dizileri için iki ek klasör olabilir ve bu klasör sonraki bölümde daha ayrıntılı olarak açıklanmıştır.

## <a name="ssl-enabled-aspnet-core-apps"></a>SSL özellikli ASP.NET Core uygulamalar

Visual Studio'daki kapsayıcı araçları, ssl özellikli bir ASP.NET çekirdek uygulamasında, kapsayıcılar olmadan çalışması için beklediğiniz gibi geliştirme sertifikasıyla hata ayıklamayı destekler. Bunu yapmak için Visual Studio, sertifikayı dışarı aktarmaya ve kapsayıcının kullanılabilir olmasını silen birkaç adım daha ekler. Kapsayıcıda hata Visual Studio sizin için işleyen akış şu şekildedir:

1. Yerel geliştirme sertifikasının araç aracılığıyla konak makinede mevcut ve güvenilir olduğunu `dev-certs` sağlar.
2. Sertifikayı bu uygulama için kullanıcı gizli dizileri depolamada depolanan güvenli bir parolayla %APPDATA%\ASP.NET\Https klasörüne dışarı aktarıyor.
3. Birim aşağıdaki dizinleri bağlar:

   - *%APPDATA%\Microsoft\UserSecrets*
   - *%APPDATA%\ASP.NET\Https*

ASP.NET Core *Https* klasörünün altındaki derleme adıyla eşleşen bir sertifikayı aramanın nedeni bu yoldeki kapsayıcıyla eşlenmiş olmasıdır. Sertifika yolu ve parola alternatif olarak ortam değişkenleri (ve ) kullanılarak veya kullanıcı gizli `ASPNETCORE_Kestrel__Certificates__Default__Path` `ASPNETCORE_Kestrel__Certificates__Default__Password` dizileri json dosyasında tanımlanabilir, örneğin:

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

Yapılandırmanız hem kapsayıcılı hem de kapsayıcılı olmayan derlemeleri destekliyorsa, yollar kapsayıcı ortamına özgü olduğundan ortam değişkenlerini kullanmalıdır.

Kapsayıcılarda uygulamalarınızı kullanarak SSL ASP.NET Core daha fazla bilgi için bkz. [HTTPS üzerinden Docker ile](/aspnet/core/security/docker-https)ASP.NET Core görüntüleri barındırma).

## <a name="debugging"></a>Hata Ayıklama

Hata ayıklama **yapılandırmasında derleme** sırasında, kapsayıcılı projeler Visual Studio derleme işleminin performansına yardımcı olacak çeşitli iyileştirmeler vardır. Kapsayıcılı uygulamalar için derleme işlemi, Dockerfile dosyasında özetlenen adımları takip etmek kadar kolay değildir. Kapsayıcıda bina, yerel makinede yapılandan çok daha yavaştır.  Bu nedenle Hata Ayıklama  yapılandırmasında derleme Visual Studio projelerinizi yerel makinede oluşturur ve ardından birim bağlamayı kullanarak çıkış klasörünü kapsayıcıyla paylaştırır. Bu iyileştirme etkin bir derlemeye Hızlı mod *derlemesi* denir.

Hızlı **modda,** Visual Studio `docker build` Docker'a yalnızca aşamayı oluşturmasını söyleyen bir bağımsız değişkenle `base` çağrılar yapar.  Visual Studio, Dockerfile'ın içeriğine bakılmaksızın sürecin geri kalanını halleder. Bu nedenle, kapsayıcı ortamını özelleştirmek veya ek bağımlılıklar yüklemek gibi Dockerfile dosyanızı değiştirerek değişikliklerinizi ilk aşamaya koymanız gerekir.  Dockerfile'ın , veya aşamalarına `build` `publish` yerleştirilen özel adımlar `final` yürütülmez.

Bu performans iyileştirmesi yalnızca Hata Ayıklama yapılandırmasında **derlemeniz sırasında** gerçekleşir. Yayın **yapılandırmasında** derleme, Dockerfile dosyasında belirtildiği gibi kapsayıcıda gerçekleşir.

Performans iyileştirmesini devre dışı bırakmak ve Dockerfile'ın belirtildiği şekilde derlemek için, proje dosyasında **ContainerDevelopmentMode** özelliğini Aşağıdaki gibi **Normal** olarak ayarlayın:

```xml
<PropertyGroup>
   <ContainerDevelopmentMode>Regular</ContainerDevelopmentMode>
</PropertyGroup>
```

Performans iyileştirmesini geri yüklemek için proje dosyasından özelliğini kaldırın.

 Hata ayıklamaya başlarken (**F5),** mümkünse önceden başlatılan bir kapsayıcı yeniden kullanılır. Önceki kapsayıcıyı yeniden kullanmak istemiyorsanız, kapsayıcıyı  yeni  bir kapsayıcı kullanmaya zorlamak için Visual Studio yeniden Visual Studio veya Temizleme komutlarını kullanabilirsiniz.

Hata ayıklayıcısını çalıştırma işlemi, proje türüne ve kapsayıcı işletim sistemine bağlıdır:

|Senaryo|Hata ayıklayıcı işlemi|
|-|-|
| **.NET Core uygulamaları (Linux kapsayıcıları)**| Visual Studio kapsayıcıya indirilir ve eşler, ardından programınız ve bağımsız değişkenleriniz (yani) ile çağrılır ve ardından hata ayıklayıcı işleme `vsdbg` `dotnet webapp.dll` iliştirilir. |
| **.NET Core uygulamaları (Windows kapsayıcıları)**| Visual Studio kapsayıcıyı kullanır ve kapsayıcıyla eşler, giriş noktası olarak çalıştırır ve Visual Studio bağlanarak `onecoremsvsmon` programınıza bağlar. Bu, normalde başka bir bilgisayarda veya sanal makinede uzaktan hata ayıklamayı ayarlamaya benzer.|
| **.NET Framework uygulamaları kullanma** | Visual Studio kapsayıcıyı kullanır ve kapsayıcıyla eşler, kapsayıcıya bağlanacak Visual Studio bir parçası olarak çalıştırır ve `msvsmon` programınıza iliştirer.|

hakkında daha fazla bilgi için bkz. Linux ve `vsdbg.exe` [OSX üzerinde .NET Core'un](https://github.com/Microsoft/MIEngine/wiki/Offroad-Debugging-of-.NET-Core-on-Linux---OSX-from-Visual-Studio)hata ayıklamasını Visual Studio.

## <a name="container-entry-point"></a>Kapsayıcı giriş noktası

Visual Studio türüne ve kapsayıcı işletim sistemine bağlı olarak özel bir kapsayıcı giriş noktası kullanıyorsa, farklı bileşimler aşağıdaki gibidir:

|Kapsayıcı türü|Giriş noktası|
|-|-|
| **Linux kapsayıcıları** | Giriş noktası, `tail -f /dev/null` kapsayıcıyı çalıştırmaya devam etmek için sonsuz bir beklemedir. Uygulama hata ayıklayıcısı aracılığıyla başlatılanın, uygulamayı çalıştırmadan sorumlu olan hata ayıklayıcısıdır (başka bir `dotnet webapp.dll` ifadeyle). Hata ayıklama olmadan başlatıldı ise, araç uygulamayı çalıştırmak `docker exec -i {containerId} dotnet webapp.dll` için bir çalıştırır.|
| **Windows kapsayıcıları**| Giriş noktası, hata ayıklayıcıyı çalıştıran gibi bir şey `C:\remote_debugger\x64\msvsmon.exe /noauth /anyuser /silent /nostatus` olduğu için bağlantıları dinler. Aynı durum, hata ayıklayıcının uygulamayı çalıştırması ve hata ayıklama `docker exec` olmadan başlatılan bir komut için de geçerlidir. Web .NET Framework için giriş noktası komutuna ekli `ServiceMonitor` olduğu yerden biraz farklıdır.|

Kapsayıcı giriş noktası, tek kapsayıcılı projelerde değil yalnızca docker-compose projelerinde değiştirilebilir.

## <a name="next-steps"></a>Sonraki adımlar

Proje dosyalarınıza ek MSBuild ayar MSBuild daha fazla özelleştirmeyi öğrenin. Kapsayıcı [MSBuild özelliklerine bakın.](container-msbuild-properties.md)

## <a name="see-also"></a>Ayrıca bkz.

[MSBuild](../msbuild/msbuild.md) 
 Windows üzerinde [Dockerfile](/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile) 
 [Windows üzerinde Linux kapsayıcıları](/virtualization/windowscontainers/deploy-containers/linux-containers)
