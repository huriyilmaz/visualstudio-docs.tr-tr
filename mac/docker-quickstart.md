---
title: Docker 'ı kullanmaya başlama
description: Mac için Visual Studio, projelerinize docker ekleme hakkında bilgi edinin
author: jmatthiesen
ms.author: jomatthi
manager: dominicn
ms.date: 11/09/2020
ms.topic: how-to
ms.openlocfilehash: 6174cea678ad9f4f2f7285e1b4469ee811c182fc
ms.sourcegitcommit: 965372ad0d75f015403c1af508080bf799914ce3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "135804408"
---
# <a name="get-started-with-docker-in-visual-studio-for-mac"></a>Mac için Visual Studio docker ile çalışmaya başlama

Mac için Visual Studio, kapsayıcılı ASP.NET Core uygulamaları kolayca oluşturabilir, ayıklayabilir ve çalıştırabilir ve bunları Azure 'da yayımlayabilirsiniz.

## <a name="prerequisites"></a>Önkoşullar

* [Docker Masaüstü](https://hub.docker.com/editions/community/docker-ce-desktop-mac)
* [Mac için Visual Studio 2019](https://visualstudio.microsoft.com/vs/mac)

## <a name="installation-and-setup"></a>Yükleme ve Kurulum

Docker yüklemesi için, [Mac Için Docker Desktop 'ı yükleme](https://docs.docker.com/docker-for-mac/install/)bölümündeki bilgileri gözden geçirin ve izleyin.

## <a name="creating-an-aspnet-core-web-application-and-adding-docker-support"></a>ASP.NET Core Web uygulaması oluşturma ve docker desteği ekleme

1. **Yeni çözüm > dosyaya** giderek yeni bir çözüm oluşturun.
1. **.net Core > uygulama** altında **Web uygulaması** şablonunu seçin: ![ yeni bir ASP.NET uygulaması oluşturun](media/docker-quickstart-1.png)
1. Hedef çerçeveyi seçin. Bu örnekte, .NET Core 2,2: ![ Target Framework 'ü ayarla ' yı kullanacağız](media/docker-quickstart-2.png)
1. Ad (Bu örnekteki _Dockerdemo_ ) gibi proje ayrıntılarını girin. oluşturulan proje, bir ASP.NET Core web sitesi derlemek ve çalıştırmak için ihtiyacınız olan tüm temel bilgileri içerir.
1. Çözüm penceresinde DockerDemo projesine sağ tıklayın ve **ekle > Docker desteği** Ekle ' yi seçin: ![ Docker desteği ekle](media/docker-quickstart-3.png)

Mac için Visual Studio, çözümünüze **docker-compose** adlı otomatik olarak yeni bir proje ekleyecek ve mevcut projenize bir **dockerfile** ekleyecek.

![Oluşturulan Docker destek dosyaları](media/docker-quickstart-4.png)

## <a name="dockerfile-overview"></a>Dockerfile genel bakış

Dockerfile, son bir Docker görüntüsü oluşturmaya yönelik tarif eden bir dosyadır. İçindeki komutları anlamak için [Dockerfile başvurusuna](https://docs.docker.com/engine/reference/builder/) bakın.

```
FROM mcr.microsoft.com/dotnet/core/aspnet:2.2-stretch-slim AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM mcr.microsoft.com/dotnet/core/sdk:2.2-stretch AS build
WORKDIR /src
COPY DockerDemo/DockerDemo.csproj DockerDemo/
RUN dotnet restore "DockerDemo/DockerDemo.csproj"
COPY . .
WORKDIR "/src/DockerDemo"
RUN dotnet build "DockerDemo.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "DockerDemo.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "DockerDemo.dll"]
```

Yukarıdaki *Dockerfile* , [Microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) görüntüsünü temel alır ve projenizi oluşturup kapsayıcıya ekleyerek temel görüntüyü değiştirmeye yönelik yönergeler içerir.

> [!NOTE]
> Mac için Visual Studio tarafından oluşturulan varsayılan dockerfile, HTTP trafiği için 80 numaralı bağlantı noktasını kullanıma sunar. HTTPS trafiğini etkinleştirmek için `Expose 443` Dockerfile dosyasına ekleyin.

## <a name="debugging"></a>Hata Ayıklama

`docker-compose`başlangıç Project olarak projeyi seçin ve hata ayıklamayı başlatın (**hata ayıklamayı başlatmak > çalıştırın**). bu işlem bir kapsayıcıda ASP.NET projesi oluşturur, dağıtır ve başlatır.

> [!TIP]
> Docker Desktop 'ı yükledikten sonra ilk çalıştırmada, hata ayıklamaya çalışırken şu hatayı alabilirsiniz: `Cannot start service dockerdemo: Mounts denied`
>
> `/usr/local/share/dotnet/sdk/NuGetFallbackFolder`Docker Desktop 'Ta dosya paylaşma sekmesine ekleyin:
>
> ![Dosya paylaşımına NuGetFallbackFolder klasörü ekleniyor](media/docker-quickstart-5.png)

Derleme tamamlandığında uygulama Safari 'de başlatılır:

![Safari 'de çalışan varsayılan Docker projesi](media/docker-quickstart-6.png)

Kapsayıcının bir bağlantı noktasını dinlediğini, `http://localhost:32768` Örneğin, ve bu bağlantı noktasının değişebileceğini unutmayın.

Çalışan kapsayıcıların listesini görmek için `docker ps` terminalde komutunu kullanın.

Aşağıdaki ekran görüntüsünde bağlantı noktası geçişine ( **bağlantı noktaları** altında) göz önünde edin. Bu, kapsayıcının yukarıda Safari 'de gördüğdiğimiz bağlantı noktasını dinlediği ve bağlantı noktası 80 ' deki iç Web sunucusuna (Dockerfile içinde tanımlandığı gibi) istek geçirdiğini gösterir. Uygulamanın perspektifinden, 80 numaralı bağlantı noktasını dinler:

![Docker kapsayıcı listesi](media/docker-quickstart-7.png)
