---
title: Docker için Visual Studio Araçları ile ASP.NET
author: ghogen
description: Visual Studio 2019 ve Docker for Windows
ms.author: ghogen
ms.date: 03/08/2021
ms.technology: vs-container-tools
ms.topic: include
ms.openlocfilehash: 91ca214fe8a90a9d999763f0099a3e9634c44824
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122147393"
---
Visual Studio ile kapsayıcılı .NET, ASP.NET ve ASP.NET Core uygulamalarını kolayca derleme, hata ayıklama ve çalıştırma ve bunları Azure Container Registry (ACR), Docker Hub, Azure App Service veya kendi kapsayıcı kayıt defterinize yayımlayabilirsiniz. Bu makalede, ACR'de ASP.NET Core bir uygulama yayımlayaz.

## <a name="prerequisites"></a>Önkoşullar

* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* Visual Studio Geliştirme, **Azure** Araçları iş yükü ve/veya **.NET Core** platformlar arası geliştirme iş yükünün yüklü olduğu [2019](https://visualstudio.microsoft.com/downloads) sürümü
* [.NET Core ile geliştirme](https://dotnet.microsoft.com/download/dotnet-core/) için .NET Core Geliştirme Araçları
* Azure aboneliği olan Azure Container Registry yayımlamak için. [Ücretsiz deneme sürümüne kaydolma.](https://azure.microsoft.com/free/dotnet/)

## <a name="installation-and-setup"></a>Yükleme ve kurulum

Docker yüklemesi için önce [Docker Desktop for Windows: Yüklemeden önce neleri bilmek gerekir? bağlantısında yer alan bilgileri gözden geçirebilirsiniz.](https://docs.docker.com/docker-for-windows/install/#what-to-know-before-you-install) Ardından [Docker Desktop'ı yükleyin.](https://hub.docker.com/editions/community/docker-ce-desktop-windows)

## <a name="add-a-project-to-a-docker-container"></a>Docker kapsayıcısı için proje ekleme

1. **ASP.NET Core Web Uygulaması** şablonunu kullanarak yeni bir proje oluşturun veya .NET Core yerine .NET Framework'yi kullanmak için ASP.NET Web Uygulaması **(.NET Framework) seçin.**
1. Yeni **web uygulaması oluştur ekranında** **Docker** Desteğini Etkinleştir onay kutusunun seçili olduğundan emin olun.

   ![Docker Desteğini Etkinleştir onay kutusu](../../media/container-tools/vs-2019/webapp-additional-information-31-docker.png)

   Ekran görüntüsünde .NET Core; .NET Framework kullanıyorsanız, biraz farklı görünüyor.

1. İstediğiniz kapsayıcı türünü seçin (Windows Veya Linux) ve **Oluştur'a tıklayın.**

## <a name="dockerfile-overview"></a>Dockerfile'a genel bakış

Projede son bir Docker görüntüsü oluşturma tarifi olan *Dockerfile* oluşturulur. Içindeki komutları [anlamak için Dockerfile](https://docs.docker.com/engine/reference/builder/) başvurusuna bakın:

```dockerfile
FROM mcr.microsoft.com/dotnet/core/aspnet:3.1 AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM mcr.microsoft.com/dotnet/core/sdk:3.1 AS build
WORKDIR /src
COPY ["WebApplication1/WebApplication1.csproj", "WebApplication1/"]
RUN dotnet restore "WebApplication1/WebApplication1.csproj"
COPY . .
WORKDIR "/src/WebApplication1"
RUN dotnet build "WebApplication1.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "WebApplication1.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "WebApplication1.dll"]
```

Yukarıdaki *Dockerfile* [dosyası microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) görüntüsünü temel almaktadır ve projenizi oluşturma ve kapsayıcıya ekleyerek temel görüntüyü değiştirme yönergelerini içerir. .NET Framework kullanıyorsanız temel görüntü farklı olur.

Yeni proje iletişim kutusunun HTTPS için **yapılandır** onay kutusu işaretli olduğunda *Dockerfile iki bağlantı* noktasını kullanıma sağlar. HTTP trafiği için bir bağlantı noktası kullanılır; diğer bağlantı noktası HTTPS için kullanılır. Onay kutusu işaretli değilse, HTTP trafiği için tek bir bağlantı noktası (80) kullanıma hazır olur.

## <a name="debug"></a>Hata Ayıklama

Araç çubuğundaki hata ayıklama açılan **menüsünden Docker'ı** seçin ve uygulamada hata ayıklamaya başlayabilirsiniz. Bir sertifikaya güvenme hakkında bir istem ile bir ileti alabilirsiniz; devam etmek için sertifikaya güvenmeyi seçin.

Çıkış **penceresindeki** Kapsayıcı **Araçları seçeneği** hangi eylemlerin gerçekleştir olduğunu gösterir. İlk kez, temel görüntüyü indirmek biraz zaman alsa da sonraki çalıştırmalarda çok daha hızlıdır.

>[!NOTE]
> Hata ayıklama için bağlantı noktalarını değiştirmek gerekirse, bunu dosyanınlaunchSettings.js *kullanabilirsiniz.* Bkz. [Kapsayıcı Başlatma Ayarlar.](../../container-launch-settings.md)

## <a name="containers-window"></a>Kapsayıcılar penceresi

2019 Visual Studio 16.4 veya sonraki bir sürümü kullanıyorsanız, hem makineniz üzerinde çalışan kapsayıcıları hem de kullanabileceğiniz görüntüleri görüntülemek için Kapsayıcılar penceresini kullanabilirsiniz. 

**IDE'de** arama kutusunu kullanarak Kapsayıcılar penceresini açın (kullanmak için **Ctrl** Q tuşlarına basın), yazın ve listeden +  `container` **Kapsayıcılar** penceresini seçin.

Kapsayıcılar penceresini **düzenleyicinin** altında olduğu gibi kullanışlı bir yere, pencere yerleştirme kılavuzlarını kullanarak indirebilirsiniz.

Pencerede kapsayıcınızı bulun ve ortam değişkenlerini, bağlantı noktası eşlemelerini, günlükleri ve dosya sistemi görüntülemek için her sekmede adım adım gidin.

![Kapsayıcılar penceresinin ekran görüntüsü](../../media/overview/vs-2019/container-tools-window.png)

Daha fazla bilgi için [bkz. Kapsayıcıları ve görüntüleri görüntüleme ve tanılama Visual Studio.](../../view-and-diagnose-containers.md)

## <a name="publish-docker-images"></a>Docker görüntülerini yayımlama

Uygulamanın geliştirme ve hata ayıklama döngüsü tamamlandıktan sonra, uygulamanın üretim görüntüsünü oluşturabilirsiniz.

1. Yapılandırma açılan listesinde Yayın'a **ve** uygulamayı derlemeye devam edin.
1. Içinde projenize sağ tıklayın ve **Çözüm Gezgini'yi** **seçin.**
1. Yayımla **iletişim** kutusunda **Docker Container Registry** seçin.

   ![Yayımla iletişim kutusunun ekran görüntüsü - Docker'ı Container Registry](../../media/container-tools/vs-2019/docker-container-registry.png)

1. Yeni **Oluştur'Azure Container Registry.**

   ![Yayımla iletişim kutusunun ekran görüntüsü - Yeni bir kullanıcı oluştur'Azure Container Registry](../../media/container-tools/vs-2019/select-existing-or-create-new-azure-container-registry.png)

1. Yeni bir dosya oluşturma içinde **istediğiniz değerleri Azure Container Registry.**

    | Ayar      | Önerilen değer  | Açıklama                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **DNS Ön Eki** | Genel olarak benzersiz bir ad | Kapsayıcı kayıt defterinizi benzersiz olarak tanımlayan ad. |
    | **Abonelik** | Aboneliğinizi seçin | Kullanılacak Azure aboneliği. |
    | **[Kaynak Grubu](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  Kapsayıcı kayıt defterinizin oluşturulacak kaynak grubunun adı. Yeni kaynak grubu oluşturmak **Yeni**'yi seçin.|
    | **[SKU](/azure/container-registry/container-registry-skus)** | Standart | Kapsayıcı kayıt defterinin hizmet katmanı  |
    | **Kayıt Defteri Konumu** | Size yakın bir konum | Size veya kapsayıcı kayıt [defterinizi](https://azure.microsoft.com/regions/) kullanan diğer hizmetlere yakın bir bölgede konum seçin. |

    ![Visual Studio oluştur iletişim Azure Container Registry oluştur][0]

1. **Oluştur**’a tıklayın. Yayımla **iletişim** kutusunda artık oluşturulan kayıt defteri görüntülenir.

   ![Oluşturulan ayarları gösteren Yayımla iletişim Azure Container Registry görüntüsü](../../media/container-tools/vs-2019/created-azure-container-registry.png)

1. Kapsayıcı **görüntülerinizi** Azure'da yeni oluşturulan kayıt defterinde yayımlama işlemini tamamlamak için Son'a tıklayın.

   ![Başarılı yayımlamayı gösteren ekran görüntüsü](../../media/container-tools/vs-2019/publish-succeeded.png)

## <a name="next-steps"></a>Sonraki Adımlar

Artık kapsayıcıyı kayıt defterinden Docker görüntülerini çalıştırabilen herhangi bir ana bilgisayar [örneğine](/azure/container-instances/container-instances-tutorial-deploy-app)Azure Container Instances.

[0]:../../media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog-2019.png
