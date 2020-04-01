---
title: ASP.NET docker için Görsel Stüdyo Araçları
author: ghogen
description: Visual Studio 2019 araç ve Docker windows için nasıl kullanılacağını öğrenin
ms.author: ghogen
ms.date: 02/01/2019
ms.prod: visual-studio-dev16
ms.technology: vs-azure
ms.topic: include
ms.openlocfilehash: bd9ac1bda9cb5f5d9cc5d84248200434426307c8
ms.sourcegitcommit: ce3d0728ec1063ab548dac71c8eaf26d20450acc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/01/2020
ms.locfileid: "80502365"
---
Visual Studio ile konteynerleştirilmiş .NET, ASP.NET ve ASP.NET Core uygulamalarını kolayca oluşturabilir, hata ayıklayabilir ve çalıştırabilir ve bunları Azure Konteyner Kayıt Defteri (ACR), Docker Hub, Azure Uygulama Hizmeti veya kendi konteyner kayıt defterinizde yayınlayabilirsiniz. Bu makalede, ACR için bir ASP.NET Core uygulaması yayınlayacağız.

## <a name="prerequisites"></a>Ön koşullar

* [Docker Masaüstü](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) Web **Geliştirme,** **Azure Araçları** iş yükü ve/veya **.NET Core çapraz platform geliştirme** iş yükü yüklü
* [.NET Core](https://dotnet.microsoft.com/download/dotnet-core/) ile geliştirme için .NET Çekirdek Geliştirme Araçları
* Azure Kapsayıcı Kayıt Defteri'nde yayımlamak için bir Azure aboneliği. [Ücretsiz deneme sürümü için kaydolun.](https://azure.microsoft.com/offers/ms-azr-0044p/)

## <a name="installation-and-setup"></a>Kurulum ve kurulum

Docker yüklemesi için, windows için Docker Desktop'daki bilgileri ilk olarak gözden [geçirin: Yüklemeden önce bilinmesi gerekenler.](https://docs.docker.com/docker-for-windows/install/#what-to-know-before-you-install) Ardından, [Docker Desktop'ı](https://hub.docker.com/editions/community/docker-ce-desktop-windows)yükleyin.

## <a name="add-a-project-to-a-docker-container"></a>Docker kapsayıcısına proje ekleme

1. ASP.NET Çekirdek Web **Uygulaması** şablonu kullanarak yeni bir proje oluşturun veya .NET Core yerine .NET Framework'ü kullanmak istiyorsanız, ASP.NET **Web Uygulaması (.NET Framework) seçeneğini belirleyin.**
1. **Web Uygulaması'nı**seçin ve Docker Destek onay kutusunu **etkinleştir'in** seçildiğinden emin olun.

   ![Docker Destek onay kutusunu etkinleştir](../../media/container-tools/vs-2019/create-new-web-application.PNG)

   Ekran görüntüsü .NET Core'u gösterir; .NET Framework kullanıyorsanız, biraz farklı görünüyor.

1. İstediğiniz kapsayıcı türünü seçin (Windows veya Linux) ve **Oluştur'u**tıklatın.

## <a name="dockerfile-overview"></a>Dockerfile'a genel bakış

Bir *Dockerfile*, son docker görüntü oluşturmak için tarifi, projeoluşturulur. İçindeki komutların anlaşılması için [Dockerfile başvurusuna](https://docs.docker.com/engine/reference/builder/) bakın.:

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

Önceki *Dockerfile* [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) resmine dayanır ve projenizi oluşturarak ve kapsayıcıya ekleyerek temel görüntüyü değiştirmek için yönergeler içerir. .NET Framework kullanıyorsanız, temel görüntü farklı olacaktır.

Yeni proje iletişim kutusunun HTTPS için **Yapılandırma** onay kutusu işaretlendiğinde, *Dockerfile* iki bağlantı noktasını ortaya çıkarır. Bir bağlantı noktası HTTP trafiği için kullanılır; diğer bağlantı noktası HTTPS için kullanılır. Onay kutusu işaretlenmezse, HTTP trafiği için tek bir bağlantı noktası (80) açığa çıkarır.

## <a name="debug"></a>Hata ayıklama

Araç çubuğundaki hata ayıklama açılır tarihinden **Docker'ı** seçin ve uygulamayı hata ayıklamaya başlayın. Bir sertifikaya güvenme yle ilgili bir istem içeren bir ileti görebilirsiniz; devam edecek sertifikaya güvenmeyi seçin.

**Çıktı** penceresindeki **Kapsayıcı Araçları** seçeneği, hangi eylemlerin gerçekleştiğini gösterir. İlk seferinde, temel görüntüyü indirmek biraz zaman alabilir, ancak sonraki çalıştırmalarda çok daha hızlıdır.

>[!NOTE]
> Hata ayıklama için bağlantı noktalarını değiştirmeniz gerekiyorsa, bunu *launchSettings.json* dosyasında yapabilirsiniz. [Bkz. Konteyner Başlatma Ayarları](../../container-launch-settings.md).

## <a name="containers-window"></a>Kapsayıcılar penceresi

Visual Studio 2019 sürüm 16.4 veya daha sonranız varsa, makinenizde çalışan kapsayıcıları ve mevcut görüntüleri görüntülemek için **Kapsayıcılar** penceresini kullanabilirsiniz.

IDE'deki arama kutusunu kullanarak **Kapsayıcılar** penceresini açın (kullanmak için `container` **Ctrl**+**Q** tuşuna basın), listeden Kapsayıcılar penceresini yazın ve **Kapsayıcılar** penceresini seçin.

**Kapsayıcılar** penceresini, düzenleyicinin altındaki gibi uygun bir yere, hareket ettirerek ve pencere yerleştirme kılavuzlarını izleyerek monte edebilirsiniz.

Pencerede, kapsayıcınızı bulun ve ortam değişkenlerini, bağlantı noktası eşlemelerini, günlükleri ve dosya sistemini görüntülemek için her sekmeden geçin.

![Kapsayıcılar penceresinin ekran görüntüsü](../../media/overview/vs-2019/container-tools-window.png)

Daha fazla bilgi için [Visual Studio'da görünüm ve tanı lama kapları tanılayın.](../../view-and-diagnose-containers.md)

## <a name="publish-docker-images"></a>Docker resimlerini yayımla

Uygulamanın geliştirme ve hata ayıklama döngüsü tamamlandıktan sonra, uygulamanın üretim görüntüsünü oluşturabilirsiniz.

1. Yapılandırma açılır düşüşünü **Release** olarak değiştirin ve uygulamayı oluşturun.
1. **Çözüm Gezgini'nde** projenize sağ tıklayın ve **Yayımla'yı**seçin.
1. Yayımlama hedef iletişim **kutusunda, Kapsayıcı Kayıt Defteri** sekmesini seçin.
1. **Yeni Azure Kapsayıcı Kayıt Defteri Oluştur'u** seçin ve **Yayımla'yı**tıklatın.
1. **Yeni bir Azure Kapsayıcı Kayıt Defteri Oluştur'da**istediğiniz değerleri doldurun.

    | Ayar      | Önerilen değer  | Açıklama                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **DNS Ön Eki** | Genel olarak benzersiz bir ad | Konteyner kayıt defterinizi benzersiz olarak tanımlayan ad. |
    | **Abonelik** | Aboneliğinizi seçin | Kullanılacak Azure aboneliği. |
    | **[Kaynak Grubu](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  Kapsayıcı kayıt defterinizi oluşturacak kaynak grubunun adı. Yeni kaynak grubu oluşturmak **Yeni**'yi seçin.|
    | **[Sku](/azure/container-registry/container-registry-skus)** | Standart | Konteyner kayıt defterinin hizmet katmanı  |
    | **Kayıt Defteri Konumu** | Size yakın bir konum | Size yakın bir [bölgede](https://azure.microsoft.com/regions/) veya konteyner kayıt defterinizi kullanacak diğer hizmetlerin yakınında bir Konum seçin. |

    ![Visual Studio's oluşturmak Azure Konteyner Kayıt Defteri iletişim kutusu][0]

1. **Oluştur'u** tıklatın

   ![Başarılı yayımlamayı gösteren ekran görüntüsü](../../media/container-tools/publish-succeeded.png)

## <a name="next-steps"></a>Sonraki Adımlar

Artık kapsayıcıyı kayıt defterinden Docker görüntülerini çalıştırabilen herhangi bir ana bilgisayara çekebilirsiniz (örneğin [Azure Kapsayıcı Örnekleri).](/azure/container-instances/container-instances-tutorial-deploy-app)

[0]:../../media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog-2019.png
