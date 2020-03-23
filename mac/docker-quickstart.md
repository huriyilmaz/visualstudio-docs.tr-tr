---
title: Docker ile başlayın
description: Mac için Visual Studio'daki projelerinize Docker'ı nasıl ekleyeceğinizi öğrenin
author: heiligerdankgesang
ms.author: dominicn
ms.date: 06/17/2019
ms.openlocfilehash: 2c6bdd7d0b2c939ed9db9be962e89d9ee423e1d4
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "74984120"
---
# <a name="get-started-with-docker-in-visual-studio-for-mac"></a>Mac için Visual Studio'da Docker ile başlayın

Mac için Visual Studio ile, konteynerleştirilmiş ASP.NET Core uygulamaları oluşturabilir, hata ayıklayabilir ve çalıştırabilir ve Azure'da yayınlayabilirsiniz.

## <a name="prerequisites"></a>Önkoşullar

* [Docker Masaüstü](https://hub.docker.com/editions/community/docker-ce-desktop-mac)
* [Mac 2019 için Visual Studio](https://visualstudio.microsoft.com/vs/mac)

## <a name="installation-and-setup"></a>Yükleme ve Kurulum

Docker kurulumu [için, Mac için Docker Desktop'ı yükleyin](https://docs.docker.com/docker-for-mac/install/)ve bilgileri takip edin.

## <a name="creating-an-aspnet-core-web-application-and-adding-docker-support"></a>ASP.NET Çekirdek Web Uygulaması Oluşturma ve Docker Desteği Ekleme

1. **Yeni > Çözüm Dosya'ya**giderek yeni bir çözüm oluşturun.
1. **.NET Core > Uygulaması** altında Web ![ **Uygulaması** şablonu seçin: Yeni bir ASP.NET uygulama oluşturma](media/docker-quickstart-1.png)
1. Hedef çerçeveyi seçin. Bu örnekte .NET Core 2.2: ![Hedef çerçeve yi ayarlama](media/docker-quickstart-2.png)
1. Ad (Bu örnekte_DockerDemo)_ gibi proje ayrıntılarını girin. Oluşturulan proje, bir ASP.NET Core web sitesi oluşturmak ve çalıştırmak için ihtiyacınız olan tüm temel bilgileri içerir.
1. Çözüm Defteri'nde DockerDemo projesine sağ tıklayın ve Docker ![Desteği ekle > ekle seçeneğini seçin : **Docker**desteği ekle](media/docker-quickstart-3.png)

Mac için Visual Studio, **docker-compose** adlı çözümünüze otomatik olarak yeni bir proje ekler ve mevcut projenize bir **Dockerfile** ekler.

![Oluşturulan docker destek dosyaları](media/docker-quickstart-4.png)

## <a name="dockerfile-overview"></a>Dockerfile Genel Bakış

Dockerfile son docker görüntü oluşturmak için reçetedir. İçindeki komutların anlaşılması için [Dockerfile başvurusuna](https://docs.docker.com/engine/reference/builder/) bakın.

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

Önceki *Dockerfile* [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) resmine dayanır ve projenizi oluşturarak ve kapsayıcıya ekleyerek temel görüntüyü değiştirmek için yönergeler içerir.

> [!NOTE]
> Visual Studio for Mac tarafından oluşturulan varsayılan Dockerfile, HTTP trafiği için Port 80'i ortaya çıkarır. HTTPS trafiğini etkinleştirmek için Dockerfile'a ekleyin. `Expose 443`

## <a name="debugging"></a>Hata ayıklama

Projeyi `docker-compose` Başlangıç Projesi olarak seçin ve hata ayıklamaya başlayın **(Hata Ayıklama başlat> başlatın).** Bu, ASP.NET projesini bir kapsayıcıda oluşturur, dağıtır ve başlatacaktır.

> [!TIP]
> Docker Desktop'ı yükledikten sonraki ilk çalıştırmada hata ayıklamaya çalışırken aşağıdaki hatayı alabilirsiniz:`Cannot start service dockerdemo: Mounts denied`
>
> Docker `/usr/local/share/dotnet/sdk/NuGetFallbackFolder` Desktop'da Dosya Paylaşımı sekmesine ekleyin:
>
> ![Dosya Paylaşımına NuGetFallbackFolder klasörünü ekleme](media/docker-quickstart-5.png)

Yapı tamamlandığında, uygulama Safari'de başlatılacaktır:

![Safari'de çalışan Varsayılan Docker projesi](media/docker-quickstart-6.png)

Örneğin, kapsayıcının bir bağlantı noktasında `http://localhost:32768` dinleyeceğini ve bu bağlantı noktasının farklılık gösterebileceğini unutmayın.

Çalışan kapsayıcıların listesini görmek için `docker ps` Terminal'deki komutu kullanın.

Aşağıdaki ekran görüntüsündeki bağlantı noktası rölesini not edin **(PORTS**altında). Bu, konteynerin yukarıda Safari'de gördüğümüz bağlantı noktasını dinlediğini ve istekleri 80 no'daki bağlantı noktası (Dockerfile'da tanımlandığı şekilde) dahili web sunucusuna ilettiğini gösterir. Uygulamanın bakış açısından, port 80 dinliyor:

![Docker konteyner listesi](media/docker-quickstart-7.png)
