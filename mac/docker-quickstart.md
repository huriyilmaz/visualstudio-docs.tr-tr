---
title: Docker Kullanmaya başlayın ile birlikte
description: Mac için Visual Studio'da projelerinize Docker ekleme hakkında Mac için Visual Studio
author: heiligerdankgesang
ms.author: dominicn
ms.date: 11/09/2020
ms.topic: how-to
ms.openlocfilehash: 4ddb15c8bc5bf90663c5431d2379af61b43e73a6
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2021
ms.locfileid: "123964768"
---
# <a name="get-started-with-docker-in-visual-studio-for-mac"></a>Kullanmaya başlayın Docker ile Mac için Visual Studio

Bu Mac için Visual Studio kolayca kapsayıcılı uygulama derleme, hata ayıklama ve ASP.NET Core azure'da yayımlayabilirsiniz.

## <a name="prerequisites"></a>Önkoşullar

* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-mac)
* [Mac için Visual Studio 2019](https://visualstudio.microsoft.com/vs/mac)

## <a name="installation-and-setup"></a>Yükleme ve Kurulum

Docker yüklemesi için Mac için [Docker Desktop'ı yükleme bağlantısında yer alan bilgileri gözden geçirin ve izleyin.](https://docs.docker.com/docker-for-mac/install/)

## <a name="creating-an-aspnet-core-web-application-and-adding-docker-support"></a>ASP.NET Core Web Uygulaması Oluşturma ve Docker Desteği Ekleme

1. Dosya Yeni Çözüm'e gidip **yeni > oluşturun.**
1. **.NET Core > Uygulaması altında** **Web** Uygulaması şablonunu seçin: Yeni bir ASP.NET ![ oluşturma](media/docker-quickstart-1.png)
1. Hedef çerçeveyi seçin. Bu örnekte .NET Core 2.2: ![ Set target framework (Hedef çerçeveyi ayarla)](media/docker-quickstart-2.png)
1. Ad gibi proje ayrıntılarını girin _(bu örnekte DockerDemo)._ Oluşturulan proje, bir web sitesi oluşturmak ve çalıştırmak için ihtiyacınız olan tüm ASP.NET Core içerir.
1. Çözüm Penceresinde DockerDemo projesine sağ tıklayın ve Docker Desteği **>** Ekle: ![ Docker desteği ekle'yi seçin](media/docker-quickstart-3.png)

Mac için Visual Studio otomatik olarak **çözümünüze docker-compose** adlı yeni bir proje ekler ve mevcut projenize **bir Dockerfile** ekler.

![Oluşturulan docker destek dosyaları](media/docker-quickstart-4.png)

## <a name="dockerfile-overview"></a>Dockerfile'a Genel Bakış

Dockerfile, son bir Docker görüntüsü oluşturma tarifidir. Içindeki komutları [anlamak için Dockerfile](https://docs.docker.com/engine/reference/builder/) başvurusuna bakın.

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

Yukarıdaki *Dockerfile,* [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) görüntüsünü temel almaktadır ve projenizi yapılandırarak ve kapsayıcıya ekleyerek temel görüntüyü değiştirmeye ilişkin yönergeler içerir.

> [!NOTE]
> Mac için Visual Studio tarafından oluşturulan varsayılan Dockerfile, HTTP trafiği için 80 bağlantı noktasını gösterir. HTTPS trafiğini etkinleştirmek için `Expose 443` Dockerfile'a ekleyin.

## <a name="debugging"></a>Hata Ayıklama

Başlangıç programı `docker-compose` olarak projeyi seçin Project hata ayıklamayı başlat ( Hata **Ayıklamayı > Çalıştır**). Bu, kapsayıcıda ASP.NET, dağıtır ve başlatır.

> [!TIP]
> Docker Desktop'ı yükledikten sonraki ilk çalıştırmada hata ayıklamaya çalışırken aşağıdaki hatayı alabilirsiniz: `Cannot start service dockerdemo: Mounts denied`
>
> `/usr/local/share/dotnet/sdk/NuGetFallbackFolder`Docker Desktop'ta Dosya Paylaşımı sekmesine ekleyin:
>
> ![NuGetFallbackFolder klasörünü Dosya Paylaşımına ekleme](media/docker-quickstart-5.png)

Derleme tamamlandığında uygulama Safari'de başlat:

![Safari'de çalışan varsayılan Docker projesi](media/docker-quickstart-6.png)

Kapsayıcının örneğin bir bağlantı noktası üzerinde dinlediğini `http://localhost:32768` ve bu bağlantı noktasının farklılık gösterdiğini unutmayın.

Çalışan kapsayıcıların listesini görmek için `docker ps` Terminal'de komutunu kullanın.

Aşağıdaki ekran görüntüsünde yer alan bağlantı noktası geçişlerini not edin **(PORT'LAR altında).** Bu, kapsayıcının yukarıda Safari'de gördüğümüz bağlantı noktasını dinlediğini ve istekleri 80 bağlantı noktası üzerindeki iç web sunucusuna (Dockerfile içinde tanımlandığı şekilde) iletdiğini gösterir. Uygulamanın perspektifinden bakıldığında, 80 bağlantı noktasını dinler:

![Docker kapsayıcı listesi](media/docker-quickstart-7.png)
