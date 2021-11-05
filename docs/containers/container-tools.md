---
title: Visual Studio ASP.NET ile Kapsayıcı Araçları
author: ghogen
description: Visual Studio Container Tools ve Docker for Windows
ms.author: ghogen
ms.date: 10/27/2021
ms.technology: vs-container-tools
ms.topic: quickstart
ms.openlocfilehash: 99696d6c0a3b5603ce173a6e2c7a3171aac76a4b
ms.sourcegitcommit: aff49629012f4d5fa07c75ea0ca5bf53d28aa173
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/05/2021
ms.locfileid: "131662580"
---
# <a name="quickstart-docker-in-visual-studio"></a>Hızlı Başlangıç: Visual Studio'da Docker

::: moniker range="vs-2017"

[!include[Visual Studio Container Tools](includes/vs-2017/container-tools.md)]

::: moniker-end

::: moniker range="vs-2019"

[!include[Visual Studio Container Tools](includes/vs-2019/container-tools.md)]

::: moniker-end
::: moniker range=">=vs-2022"

Visual Studio ile kapsayıcılı .NET, ASP.NET ve ASP.NET Core uygulamalarını kolayca derleme, hata ayıklama ve çalıştırma ve bunları Azure Container Registry, Docker Hub, Azure App Service veya kendi kapsayıcı kayıt defterinize yayımlayabilirsiniz. Bu makalede, bir ASP.NET Core uygulamasını Azure Container Registry.

## <a name="prerequisites"></a>Önkoşullar

* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* Visual Studio Geliştirme, **Azure** Araçları iş yükü ve/veya **.NET Core platformlar** arası geliştirme iş yükü yüklü [2022 RC](https://visualstudio.microsoft.com/downloads)
* [.NET Core ile geliştirme](https://dotnet.microsoft.com/download/dotnet-core/) için .NET Core Geliştirme Araçları
* Azure aboneliği olan Azure Container Registry yayımlamak için. [Ücretsiz deneme sürümüne kaydolma.](https://azure.microsoft.com/free/dotnet/)

## <a name="installation-and-setup"></a>Yükleme ve kurulum

Docker yüklemesi için önce [Docker Desktop for Windows: Yüklemeden önce neleri bilmek gerekir? bağlantısına bakın.](https://docs.docker.com/docker-for-windows/install/#what-to-know-before-you-install) Ardından [Docker Desktop'ı yükleyin.](https://hub.docker.com/editions/community/docker-ce-desktop-windows)

## <a name="add-a-project-to-a-docker-container"></a>Docker kapsayıcısı için proje ekleme

1. **ASP.NET Core Web Uygulaması** şablonunu kullanarak yeni bir proje oluşturun veya .NET Core yerine .NET Framework'yi kullanmak için ASP.NET Web Uygulaması **(.NET Framework) seçin.**
1. Yeni **web uygulaması oluştur ekranında** **Docker** Desteğini Etkinleştir onay kutusunun seçili olduğundan emin olun.

   ![Docker Desteğini Etkinleştir onay kutusunun ekran görüntüsü.](media/container-tools/vs-2022/web-app-additional-information-6-docker.png)

   Ekran görüntüsünde .NET 6.0; .NET Framework kullanıyorsanız, biraz farklı görünüyor.

1. İstediğiniz kapsayıcı türünü seçin (Windows Veya Linux) ve **Oluştur'a tıklayın.**

## <a name="dockerfile-overview"></a>Dockerfile'a genel bakış

Projede son bir Docker görüntüsü oluşturma tarifi olan *Dockerfile* oluşturulur. Içindeki komutları [anlamak için Dockerfile](https://docs.docker.com/engine/reference/builder/) başvurusuna bakın:

```dockerfile
#See https://aka.ms/containerfastmode to understand how Visual Studio uses this Dockerfile to build your images for faster debugging.

FROM mcr.microsoft.com/dotnet/aspnet:6.0 AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build
WORKDIR /src
COPY ["WebApplication3/WebApplication3.csproj", "WebApplication3/"]
RUN dotnet restore "WebApplication3/WebApplication3.csproj"
COPY . .
WORKDIR "/src/WebApplication3"
RUN dotnet build "WebApplication3.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "WebApplication3.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "WebApplication3.dll"]
```

Yukarıdaki *Dockerfile,* Microsoft Container Registry [(MCR)](https://azure.microsoft.com/blog/microsoft-syndicates-container-catalog/) .NET 6 görüntü görüntüsünü temel almaktadır ve projenizi oluşturma ve kapsayıcıya ekleyerek temel görüntüyü değiştirme yönergelerini içerir. Temel görüntüyü .NET Framework görüntü farklı olur.

Yeni proje iletişim kutusunun HTTPS için **yapılandır onay** kutusu işaretlendiğinde *Dockerfile iki bağlantı* noktasını kullanıma sağlar. HTTP trafiği için bir bağlantı noktası kullanılır; diğer bağlantı noktası HTTPS için kullanılır. Onay kutusu işaretli değilse, HTTP trafiği için tek bir bağlantı noktası (80) kullanıma hazır olur.

## <a name="debug"></a>Hata Ayıklama

Araç çubuğundaki hata ayıklama açılan **menüsünden Docker'ı** seçin ve uygulamada hata ayıklamaya başlayabilirsiniz. Bir sertifikaya güvenme hakkında bir istem ile bir ileti alabilirsiniz; devam etmek için sertifikaya güvenmeyi seçin.

Çıkış **penceresindeki** Kapsayıcı **Araçları seçeneği** hangi eylemlerin gerçekleştir olduğunu gösterir. İlk kez, temel görüntüyü indirmek biraz zaman alsa da sonraki çalıştırmalarda çok daha hızlıdır.

Bina yapıldıktan sonra tarayıcı açılır ve uygulamanın giriş sayfası gösterilir. Tarayıcının adres çubuğunda, hata ayıklama için localhost URL'sini ve bağlantı noktası numarasını görüntüleyebilirsiniz.

>[!NOTE]
> Hata ayıklama için bağlantı noktalarını değiştirmek gerekirse bunu *launchSettings.json dosyasından da kullanabilirsiniz.* Bkz. [Kapsayıcı Başlatma Ayarlar.](container-launch-settings.md)

## <a name="containers-window"></a>Kapsayıcılar penceresi

Kapsayıcılar penceresini **kullanarak** makineniz üzerinde çalışan kapsayıcıların yanı sıra kullanabileceğiniz görüntüleri görüntüebilirsiniz.

**IDE'de** arama kutusunu kullanarak Kapsayıcılar penceresini açın (kullanmak için **Ctrl** Q tuşlarına basın), yazın ve listeden +  `container` **Kapsayıcılar** penceresini seçin.

Kapsayıcılar penceresini **düzenleyicinin** altında olduğu gibi kullanışlı bir yere, pencere yerleştirme kılavuzlarını kullanarak indirebilirsiniz.

Pencerede kapsayıcınızı bulun ve ortam değişkenlerini, bağlantı noktası eşlemelerini, günlükleri ve dosya sistemi görüntülemek için her sekmede adım adım gidin.

![Kapsayıcılar penceresinin ekran görüntüsü.](media/container-tools/vs-2022/container-tools-window.png)

Daha fazla bilgi için [bkz. Kapsayıcılar penceresini kullanma.](view-and-diagnose-containers.md)

## <a name="publish-docker-images"></a>Docker görüntülerini yayımlama

Uygulamanın geliştirme ve hata ayıklama döngüsü tamamlandıktan sonra, uygulamanın üretim görüntüsünü oluşturabilirsiniz.

1. Yapılandırma açılan listesinde Yayın'a **ve** uygulamayı derlemeye devam edin.
1. Içinde projenize sağ tıklayın ve **Çözüm Gezgini'yi** **seçin.**
1. Yayımla **iletişim** kutusunda **Docker Container Registry** seçin.

   ![Yayımla iletişim kutusunun ekran görüntüsü - Docker Container Registry.](media/container-tools/vs-2022/docker-container-registry.png)

1. Yeni **Oluştur'Azure Container Registry.**

   ![Yayımla iletişim kutusunun ekran görüntüsü - Yeni bir dosya oluştur'Azure Container Registry.](media/container-tools/vs-2022/select-existing-or-create-new-azure-container-registry.png)

1. Yeni bir dosya oluştur içinde **istediğiniz değerleri Azure Container Registry.**

    | Ayar      | Önerilen değer  | Açıklama                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **DNS Ön Eki** | Genel olarak benzersiz bir ad | Kapsayıcı kayıt defterinizi benzersiz olarak tanımlayan ad. |
    | **Abonelik** | Aboneliğinizi seçin | Kullanılacak Azure aboneliği. |
    | **[Kaynak Grubu](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  Kapsayıcı kayıt defterinizin oluşturulacak kaynak grubunun adı. Yeni kaynak grubu oluşturmak **Yeni**'yi seçin.|
    | **[SKU](/azure/container-registry/container-registry-skus)** | Standart | Kapsayıcı kayıt defterinin hizmet katmanı  |
    | **Kayıt Defteri Konumu** | Size yakın bir konum | Size veya kapsayıcı kayıt [defterinizi](https://azure.microsoft.com/regions/) kullanan diğer hizmetlere yakın bir bölgede konum seçin. |

    ![Visual Studio oluştur iletişim kutusunun Azure Container Registry görüntüsü.](media/container-tools/vs-2022/vs-azure-container-registry-provisioning-dialog.png)

1. **Oluştur**’a tıklayın. Yayımla **iletişim** kutusunda artık oluşturulan kayıt defteri görüntülenir.

   ![Oluşturulan ayarları gösteren Yayımla iletişim Azure Container Registry görüntüsü.](media/container-tools/vs-2022/created-azure-container-registry.png)

1. Kapsayıcı **görüntülerinizi** Azure'da yeni oluşturulan kayıt defterinde yayımlama işlemini tamamlamak için Son'a tıklayın.

   :::image type="content" source="media/container-tools/vs-2022/publish-succeeded.png" alt-text="Başarılı yayımlama işlemini gösteren ekran görüntüsü." lightbox="media/container-tools/vs-2022/publish-succeeded.png" :::

## <a name="next-steps"></a>Sonraki adımlar

Artık kapsayıcıyı kayıt defterinden Docker görüntülerini çalıştırabilen herhangi bir ana bilgisayar [örneğine](/azure/container-instances/container-instances-tutorial-deploy-app)Azure Container Instances.

::: moniker-end

## <a name="additional-resources"></a>Ek kaynaklar

* [Visual Studio ile kapsayıcı geliştirme](./index.yml)
* [Docker ile Visual Studio geliştirme sorunlarını giderme](troubleshooting-docker-errors.md)
* [Visual Studio Kapsayıcı Araçları GitHub deposu](https://github.com/Microsoft/DockerTools)
