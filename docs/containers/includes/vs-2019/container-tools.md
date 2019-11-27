---
title: ASP.NET Core Docker için Visual Studio Araçları
author: ghogen
description: Visual Studio 2019 araçları 'nı ve Docker for Windows kullanmayı öğrenin
ms.author: ghogen
ms.date: 02/01/2019
ms.prod: visual-studio-dev16
ms.technology: vs-azure
ms.topic: include
ms.openlocfilehash: 0232b37d08901bcc04c9d66facfe6850a9852e88
ms.sourcegitcommit: e825d1223579b44ee2deb62baf4de0153f99242a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2019
ms.locfileid: "74485458"
---
Visual Studio ile Kapsayıcılı .NET, ASP.NET ve ASP.NET Core uygulamalarını kolayca oluşturabilir, ayıklayabilir ve çalıştırabilir ve bunları Azure Container Registry (ACR), Docker Hub, Azure App Service veya kendi kapsayıcı kayıt defterinizde yayımlayabilirsiniz. Bu makalede, ACR 'ye bir ASP.NET Core uygulaması yayımlayacağız.

## <a name="prerequisites"></a>Önkoşullar

* [Docker Masaüstü](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* **Web geliştirme**, **Azure Araçları** iş yükü ve/veya **.NET Core platformlar arası geliştirme** iş yükü yüklü olan [Visual Studio 2019](https://visualstudio.microsoft.com/downloads)
* .NET Core 2,2 ile geliştirme için [.net core 2,2 geliştirme araçları](https://dotnet.microsoft.com/download/dotnet-core/2.2)
* Bir Azure aboneliği Azure Container Registry yayımlamak için. [Ücretsiz deneme Için kaydolun](https://azure.microsoft.com/offers/ms-azr-0044p/).

## <a name="installation-and-setup"></a>Yükleme ve kurulum

Docker yüklemesi için ilk olarak [Windows Için Docker Desktop](https://docs.docker.com/docker-for-windows/install/#what-to-know-before-you-install)'taki bilgileri gözden geçirin: yüklemeden önce bilmeniz gerekenler. Sonra [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)'ı yükler.

## <a name="add-a-project-to-a-docker-container"></a>Docker kapsayıcısına proje ekleme

1. **ASP.NET Core Web uygulaması** şablonunu kullanarak yeni bir proje oluşturun.
1. **Web uygulaması**' nı seçin ve **Docker desteğini etkinleştir** onay kutusunun seçili olduğundan emin olun.

   ![Docker desteğini etkinleştir onay kutusu](../../media/container-tools/vs-2019/create-new-web-application.PNG)

1. İstediğiniz kapsayıcı türünü (Windows veya Linux) seçin ve **Oluştur**' a tıklayın.

## <a name="dockerfile-overview"></a>Dockerfile genel bakış

Bir *Dockerfile*, son bir Docker görüntüsü oluşturmaya yönelik tarif, projede oluşturulur. İçindeki komutları anlamak için [Dockerfile başvurusuna](https://docs.docker.com/engine/reference/builder/) bakın.

```
FROM microsoft/dotnet:2.2-aspnetcore-runtime-stretch-slim AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM microsoft/dotnet:2.2-sdk-stretch AS build
WORKDIR /src
COPY ["HelloDockerTools/HelloDockerTools.csproj", "HelloDockerTools/"]
RUN dotnet restore "HelloDockerTools/HelloDockerTools.csproj"
COPY . .
WORKDIR "/src/HelloDockerTools"
RUN dotnet build "HelloDockerTools.csproj" -c Release -o /app

FROM build AS publish
RUN dotnet publish "HelloDockerTools.csproj" -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "HelloDockerTools.dll"]
```

Yukarıdaki *Dockerfile* , [Microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) görüntüsünü temel alır ve projenizi oluşturup kapsayıcıya ekleyerek temel görüntüyü değiştirmeye yönelik yönergeler içerir.

Yeni proje iletişim kutusunun **https Için Yapılandır** onay kutusu Işaretlendiğinde, *dockerfile* iki bağlantı noktasını kullanıma sunar. HTTP trafiği için bir bağlantı noktası kullanılır; diğer bağlantı noktası HTTPS için kullanılır. Onay kutusu işaretli değilse, HTTP trafiği için tek bir bağlantı noktası (80) gösterilir.

## <a name="debug"></a>Hata ayıklama

Araç çubuğundaki hata ayıklama açılır listesinden **Docker** ' ı seçin ve uygulamada hata ayıklamayı başlatın. Bir sertifikaya güvenmek üzere bir istem içeren bir ileti görebilirsiniz. devam etmek için sertifikaya güvenmeyi seçin.

**Çıkış** penceresinde **kapsayıcı araçları** seçeneği hangi eylemlerin gerçekleştireceğinizi gösterir.

## <a name="containers-window"></a>Kapsayıcılar penceresi

Visual Studio 2019 sürüm 16,4 veya üzeri bir sürüme sahipseniz, makinenizde çalışan kapsayıcıları ve ayrıca kullanılabilir olan görüntüleri görüntülemek için **kapsayıcılar** penceresini kullanabilirsiniz.

IDE 'deki arama kutusunu kullanarak **kapsayıcılar** penceresini açın (kullanmak için **CTRL**+**Q** tuşlarına basın), `container`yazın ve listeden **kapsayıcılar** penceresini seçin.

**Kapsayıcılar** penceresini, düzenleyicinin altına ve pencere yerleştirme kılavuzlarını izleyerek, uygun bir yerde bağlayabilirsiniz.

Pencerede, kapsayıcınızı bulun ve ortam değişkenlerini, bağlantı noktası eşlemelerini, günlükleri ve dosya sistemini görüntülemek için her bir sekmede adım adım ilerleyin.

![Kapsayıcılar penceresinin ekran görüntüsü](../../media/overview/vs-2019/container-tools-window.png)

Daha fazla bilgi için bkz. [Visual Studio 'da kapsayıcıları ve görüntüleri görüntüleme ve tanılama](../../view-and-diagnose-containers.md).

## <a name="publish-docker-images"></a>Docker görüntülerini yayımlama

Uygulamanın geliştirme ve hata ayıklama döngüsünü tamamladıktan sonra uygulamanın üretim görüntüsünü oluşturabilirsiniz.

1. Yapılandırma açılır öğesini değiştirerek uygulamayı **serbest bırakın** ve oluşturun.
1. **Çözüm Gezgini** ' de projenize sağ tıklayın ve **Yayımla**' yı seçin.
1. Hedefi Yayımla iletişim kutusunda **Container Registry** sekmesini seçin.
1. **Yeni Azure Container Registry oluştur** ' u seçin ve **Yayımla**' ya tıklayın.
1. **Yeni Azure Container Registry oluştur ' a**istediğiniz değerleri girin.

    | Ayar      | Önerilen değer  | Açıklama                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **DNS ön eki** | Genel olarak benzersiz bir ad | Kapsayıcı kayıt defterinizi benzersiz bir şekilde tanımlayan ad. |
    | **Aboneliğiniz** | Aboneliğinizi seçin | Kullanılacak Azure aboneliği. |
    | **[Kaynak grubu](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  Kapsayıcı kayıt defterinizin oluşturulacağı kaynak grubunun adı. Yeni bir kaynak grubu oluşturmak için **Yeni** ' yi seçin.|
    | **[ISTEYIN](https://docs.microsoft.com/azure/container-registry/container-registry-skus)** | Standard | Kapsayıcı kayıt defterinin hizmet katmanı  |
    | **Kayıt defteri konumu** | Size yakın bir konum | Size yakın bir [bölgede](https://azure.microsoft.com/regions/) veya kapsayıcı kayıt defterinizi kullanacak diğer hizmetlerin yakınında bir konum seçin. |

    ![Visual Studio 'nun Azure Container Registry oluştur iletişim kutusu][0]

1. **Oluştur** 'a tıklayın

   ![Başarılı yayımlamayı gösteren ekran görüntüsü](../../media/container-tools/publish-succeeded.png)

## <a name="next-steps"></a>Sonraki Adımlar

Artık kapsayıcıyı, kayıt defterinden Docker görüntülerini çalıştırabilen herhangi bir konağa çekebilirsiniz, örneğin [Azure Container Instances](/azure/container-instances/container-instances-tutorial-deploy-app).

[0]:../../media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog-2019.png
