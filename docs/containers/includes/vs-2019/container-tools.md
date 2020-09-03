---
title: ASP.NET ile Docker için Visual Studio Araçları
author: ghogen
description: Visual Studio 2019 araçları 'nı ve Docker for Windows kullanmayı öğrenin
ms.author: ghogen
ms.date: 02/01/2019
ms.prod: visual-studio-dev16
ms.technology: vs-azure
ms.topic: include
ms.openlocfilehash: fc549951e9c6b6d208c478f37126238e91f6f039
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "88186267"
---
Visual Studio ile Kapsayıcılı .NET, ASP.NET ve ASP.NET Core uygulamalarını kolayca oluşturabilir, ayıklayabilir ve çalıştırabilir ve bunları Azure Container Registry (ACR), Docker Hub, Azure App Service veya kendi kapsayıcı kayıt defterinizde yayımlayabilirsiniz. Bu makalede, ACR 'ye bir ASP.NET Core uygulaması yayımlayacağız.

## <a name="prerequisites"></a>Ön koşullar

* [Docker Masaüstü](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* **Web geliştirme**, **Azure Araçları** iş yükü ve/veya **.NET Core platformlar arası geliştirme** iş yükü yüklü olan [Visual Studio 2019](https://visualstudio.microsoft.com/downloads)
* .NET Core ile geliştirme için [.NET Core geliştirme araçları](https://dotnet.microsoft.com/download/dotnet-core/)
* Bir Azure aboneliği Azure Container Registry yayımlamak için. [Ücretsiz deneme Için kaydolun](https://azure.microsoft.com/free/dotnet/).

## <a name="installation-and-setup"></a>Yükleme ve kurulum

Docker yüklemesi için ilk olarak [Windows Için Docker Desktop](https://docs.docker.com/docker-for-windows/install/#what-to-know-before-you-install)'taki bilgileri gözden geçirin: yüklemeden önce bilmeniz gerekenler. Sonra [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)'ı yükler.

## <a name="add-a-project-to-a-docker-container"></a>Docker kapsayıcısına proje ekleme

1. **ASP.NET Core Web uygulaması** şablonunu kullanarak yeni bir proje oluşturun veya .NET Core yerine .NET Framework kullanmak Istiyorsanız **ASP.NET Web uygulaması (.NET Framework)** öğesini seçin.
1. **Web uygulaması**' nı seçin ve **Docker desteğini etkinleştir** onay kutusunun seçili olduğundan emin olun.

   ![Docker desteğini etkinleştir onay kutusu](../../media/container-tools/vs-2019/create-new-web-application.PNG)

   Ekran görüntüsünde .NET Core gösterilir; .NET Framework kullanıyorsanız, biraz farklı görünür.

1. İstediğiniz kapsayıcı türünü (Windows veya Linux) seçin ve **Oluştur**' a tıklayın.

## <a name="dockerfile-overview"></a>Dockerfile genel bakış

Bir *Dockerfile*, son bir Docker görüntüsü oluşturmaya yönelik tarif, projede oluşturulur. İçindeki komutları anlamak için [Dockerfile başvurusuna](https://docs.docker.com/engine/reference/builder/) bakın.

```dockerfile
FROM mcr.microsoft.com/dotnet/core/aspnet:3.1-nanoserver-1903 AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM mcr.microsoft.com/dotnet/core/sdk:3.1-nanoserver-1903 AS build
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

Yukarıdaki *Dockerfile* , [Microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) görüntüsünü temel alır ve projenizi oluşturup kapsayıcıya ekleyerek temel görüntüyü değiştirmeye yönelik yönergeler içerir. .NET Framework kullanıyorsanız, temel görüntü farklı olur.

Yeni proje iletişim kutusunun **https Için Yapılandır** onay kutusu Işaretlendiğinde, *dockerfile* iki bağlantı noktasını kullanıma sunar. HTTP trafiği için bir bağlantı noktası kullanılır; diğer bağlantı noktası HTTPS için kullanılır. Onay kutusu işaretli değilse, HTTP trafiği için tek bir bağlantı noktası (80) gösterilir.

## <a name="debug"></a>Hata ayıklama

Araç çubuğundaki hata ayıklama açılır listesinden **Docker** ' ı seçin ve uygulamada hata ayıklamayı başlatın. Bir sertifikaya güvenmek üzere bir istem içeren bir ileti görebilirsiniz. devam etmek için sertifikaya güvenmeyi seçin.

**Çıkış** penceresinde **kapsayıcı araçları** seçeneği hangi eylemlerin gerçekleştireceğinizi gösterir. İlk kez, temel görüntünün indirilmesi biraz zaman alabilir, ancak sonraki çalışmalarda çok daha hızlıdır.

>[!NOTE]
> Hata ayıklama için bağlantı noktalarını değiştirmeniz gerekiyorsa, bunu dosyada *launchSettings.js* yapabilirsiniz. Bkz. [kapsayıcı başlatma ayarları](../../container-launch-settings.md).

## <a name="containers-window"></a>Kapsayıcılar penceresi

Visual Studio 2019 sürüm 16,4 veya üzeri bir sürüme sahipseniz, makinenizde çalışan kapsayıcıları ve ayrıca kullanılabilir olan görüntüleri görüntülemek için **kapsayıcılar** penceresini kullanabilirsiniz.

IDE 'deki arama kutusunu kullanarak **kapsayıcılar** penceresini açın (kullanmak için **CTRL** + **Q** tuşlarına basın), yazın `container` ve listeden **kapsayıcılar** penceresini seçin.

**Kapsayıcılar** penceresini, düzenleyicinin altına ve pencere yerleştirme kılavuzlarını izleyerek, uygun bir yerde bağlayabilirsiniz.

Pencerede, kapsayıcınızı bulun ve ortam değişkenlerini, bağlantı noktası eşlemelerini, günlükleri ve dosya sistemini görüntülemek için her bir sekmede adım adım ilerleyin.

![Kapsayıcılar penceresinin ekran görüntüsü](../../media/overview/vs-2019/container-tools-window.png)

Daha fazla bilgi için bkz. [Visual Studio 'da kapsayıcıları ve görüntüleri görüntüleme ve tanılama](../../view-and-diagnose-containers.md).

## <a name="publish-docker-images"></a>Docker görüntülerini yayımlama

Uygulamanın geliştirme ve hata ayıklama döngüsünü tamamladıktan sonra uygulamanın üretim görüntüsünü oluşturabilirsiniz.

1. Yapılandırma açılır öğesini değiştirerek uygulamayı **serbest bırakın** ve oluşturun.
1. **Çözüm Gezgini** ' de projenize sağ tıklayın ve **Yayımla**' yı seçin.
1. **Yayımla** Iletişim kutusunda **Docker Container Registry** sekmesini seçin.

   ![Yayımla iletişim kutusunun ekran görüntüsü-Docker Container Registry seçin](../../media/container-tools/vs-2019/docker-container-registry.png)

1. **Yeni Azure Container Registry oluştur**öğesini seçin.

   ![Yayımla iletişim kutusunun ekran görüntüsü-yeni Azure Container Registry oluştur seçeneğini belirleyin](../../media/container-tools/vs-2019/select-existing-or-create-new-azure-container-registry.png)

1. **Yeni Azure Container Registry oluştur ' a**istediğiniz değerleri girin.

    | Ayar      | Önerilen değer  | Açıklama                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **DNS Ön Eki** | Genel olarak benzersiz bir ad | Kapsayıcı kayıt defterinizi benzersiz bir şekilde tanımlayan ad. |
    | **Abonelik** | Aboneliğinizi seçin | Kullanılacak Azure aboneliği. |
    | **[Kaynak grubu](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  Kapsayıcı kayıt defterinizin oluşturulacağı kaynak grubunun adı. Yeni kaynak grubu oluşturmak **Yeni**'yi seçin.|
    | **[SKU](/azure/container-registry/container-registry-skus)** | Standart | Kapsayıcı kayıt defterinin hizmet katmanı  |
    | **Kayıt Defteri Konumu** | Size yakın bir konum | Size yakın bir [bölgede](https://azure.microsoft.com/regions/) veya kapsayıcı kayıt defterinizi kullanacak diğer hizmetlerin yakınında bir konum seçin. |

    ![Visual Studio 'nun Azure Container Registry oluştur iletişim kutusu][0]

1. **Oluştur**’a tıklayın. **Yayımla** iletişim kutusunda artık oluşturulan kayıt defteri görüntülenir.

   ![Azure Container Registry oluşturulduğunu gösteren Yayımla iletişim kutusunun ekran görüntüsü](../../media/container-tools/vs-2019/created-azure-container-registry.png)

1. Kapsayıcı görüntünüzü Azure 'daki yeni oluşturulan kayıt defterine yayımlama işlemini gerçekleştirmek için **son** ' a tıklayın.

   ![Başarılı yayımlamayı gösteren ekran görüntüsü](../../media/container-tools/vs-2019/publish-succeeded.png)

## <a name="next-steps"></a>Sonraki Adımlar

Artık kapsayıcıyı, kayıt defterinden Docker görüntülerini çalıştırabilen herhangi bir konağa çekebilirsiniz, örneğin [Azure Container Instances](/azure/container-instances/container-instances-tutorial-deploy-app).

[0]:../../media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog-2019.png
