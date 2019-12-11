---
title: Docker 'ı kullanmaya başlama
description: Mac için Visual Studio, projelerinize Docker ekleme hakkında bilgi edinin
author: heiligerdankgesang
ms.author: dominicn
ms.date: 06/17/2019
ms.openlocfilehash: 2c6bdd7d0b2c939ed9db9be962e89d9ee423e1d4
ms.sourcegitcommit: 370cc7fd2e11ede6d8215c8d81963a8307614550
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74984120"
---
# <a name="get-started-with-docker-in-visual-studio-for-mac"></a>Mac için Visual Studio Docker ile çalışmaya başlama

Mac için Visual Studio, Kapsayıcılı ASP.NET Core uygulamaları kolayca oluşturabilir, ayıklayabilir ve çalıştırabilir ve bunları Azure 'da yayımlayabilirsiniz.

## <a name="prerequisites"></a>Prerequisites

* [Docker Masaüstü](https://hub.docker.com/editions/community/docker-ce-desktop-mac)
* [Mac için Visual Studio 2019](https://visualstudio.microsoft.com/vs/mac)

## <a name="installation-and-setup"></a>Yükleme ve Kurulum

Docker yüklemesi için, [Mac Için Docker Desktop 'ı yükleme](https://docs.docker.com/docker-for-mac/install/)bölümündeki bilgileri gözden geçirin ve izleyin.

## <a name="creating-an-aspnet-core-web-application-and-adding-docker-support"></a>ASP.NET Core Web uygulaması oluşturma ve Docker desteği ekleme

1. **Yeni çözüm > dosyaya**giderek yeni bir çözüm oluşturun.
1. **.NET Core > uygulama** altında **Web uygulaması** şablonunu seçin: ![yeni bir ASP.NET uygulaması oluşturun](media/docker-quickstart-1.png)
1. Hedef çerçeveyi seçin. Bu örnekte, .NET Core 2,2: ![Target Framework 'ü kullanacak şekilde kullanacağız](media/docker-quickstart-2.png)
1. Ad (Bu örnekteki_Dockerdemo_ ) gibi proje ayrıntılarını girin. Oluşturulan proje, bir ASP.NET Core Web sitesi derlemek ve çalıştırmak için ihtiyacınız olan tüm temel bilgileri içerir.
1. Çözüm Bölmesi DockerDemo projesine sağ tıklayın ve **ekle > Docker desteği**Ekle ' yi seçin: ![Docker desteği ekleyin](media/docker-quickstart-3.png)

Mac için Visual Studio, çözümünüze **Docker-Compose** adlı otomatik olarak yeni bir proje ekleyecek ve mevcut projenize bir **dockerfile** ekleyecek.

![Oluşturulan Docker destek dosyaları](media/docker-quickstart-4.png)

## <a name="dockerfile-overview"></a>Dockerfile genel bakış

Dockerfile, son bir Docker görüntüsü oluşturmaya yönelik tarif eden bir dosyadır. İçindeki komutları anlamak için [Dockerfile başvurusuna](https://docs.docker.com/engine/reference/builder/) bakın.

```
FROM microsoft/dotnet:2.2-aspnetcore-runtime AS base
WORKDIR /app
EXPOSE 80

FROM microsoft/dotnet:2.2-sdk AS build
WORKDIR /src
COPY DockerDemo/DockerDemo.csproj DockerDemo/
RUN dotnet restore DockerDemo/DockerDemo.csproj
COPY . .
WORKDIR /src/DockerDemo
RUN dotnet build DockerDemo.csproj -c Release -o /app

FROM build AS publish
RUN dotnet publish DockerDemo.csproj -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "DockerDemo.dll"]
```

Yukarıdaki *Dockerfile* , [Microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) görüntüsünü temel alır ve projenizi oluşturup kapsayıcıya ekleyerek temel görüntüyü değiştirmeye yönelik yönergeler içerir.

> [!NOTE]
> Mac için Visual Studio tarafından oluşturulan varsayılan Dockerfile, HTTP trafiği için 80 numaralı bağlantı noktasını kullanıma sunar. HTTPS trafiğini etkinleştirmek için Dockerfile dosyasına `Expose 443` ekleyin.

## <a name="debugging"></a>Hata Ayıklama

Başlangıç projesi olarak `docker-compose` projesi seçin ve hata ayıklamayı başlatın (**hata ayıklamayı başlatmak > çalıştırın**). Bu işlem, ASP.NET projesini bir kapsayıcıda oluşturur, dağıtır ve başlatır.

> [!TIP]
> Docker Desktop 'ı yükledikten sonra ilk çalıştırmada, hata ayıklamaya çalışırken şu hatayı alabilirsiniz: `Cannot start service dockerdemo: Mounts denied`
>
> Docker Desktop ' ta dosya paylaşma sekmesine `/usr/local/share/dotnet/sdk/NuGetFallbackFolder` ekleyin:
>
> ![Dosya paylaşımına NuGetFallbackFolder klasörü ekleniyor](media/docker-quickstart-5.png)

Derleme tamamlandığında uygulama Safari 'de başlatılır:

![Safari 'de çalışan varsayılan Docker projesi](media/docker-quickstart-6.png)

Kapsayıcının bir bağlantı noktasını dinlediğini, örneğin `http://localhost:32768`, ve bu bağlantı noktasının değişebileceğini unutmayın.

Çalışan kapsayıcıların listesini görmek için terminalde `docker ps` komutunu kullanın.

Aşağıdaki ekran görüntüsünde bağlantı noktası geçişine ( **bağlantı noktaları**altında) göz önünde edin. Bu, kapsayıcının yukarıda Safari 'de gördüğdiğimiz bağlantı noktasını dinlediği ve bağlantı noktası 80 ' deki iç Web sunucusuna (Dockerfile içinde tanımlandığı gibi) istek geçirdiğini gösterir. Uygulamanın perspektifinden, 80 numaralı bağlantı noktasını dinler:

![Docker kapsayıcı listesi](media/docker-quickstart-7.png)
