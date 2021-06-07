---
title: ASP.NET Core ile Visual Studio Kapsayıcı Araçları
author: ghogen
description: Visual Studio 2017 araç ve araç kullanımını Docker for Windows
ms.author: ghogen
ms.date: 02/01/2019
ms.technology: vs-azure
ms.topic: include
ms.openlocfilehash: 53bf0d559d9737494567b079621879b97a403a95
ms.sourcegitcommit: fc05a763b59e212c86350d117a1900a1f2686ec8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/07/2021
ms.locfileid: "111564978"
---
Visual Studio ile kolayca kapsayıcılı ASP.NET Core uygulamaları derleme, hata ayıklama ve çalıştırma ve bunları Azure Container Registry (ACR), Docker Hub, Azure App Service veya kendi kapsayıcı kayıt defterinize yayımlayabilirsiniz. Bu makalede, ACR'de yayımlayız.

## <a name="prerequisites"></a>Önkoşullar

* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* Visual Studio Geliştirme, **Azure** Araçları iş yükü ve/veya **.NET Core platformlar** arası geliştirme iş yükünün yüklü olduğu [2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) sürümü
* Azure aboneliği olan Azure Container Registry yayımlamak için. [Ücretsiz deneme sürümüne kaydolma.](https://azure.microsoft.com/free/dotnet/)

## <a name="installation-and-setup"></a>Yükleme ve kurulum

Docker yüklemesi için önce Windows için Docker Desktop: Yüklemeden [önce neleri bilmek gerekir? bağlantısında yer alan bilgileri gözden geçirebilirsiniz.](https://docs.docker.com/docker-for-windows/install/#what-to-know-before-you-install) Ardından [Docker Desktop'ı yükleyin.](https://hub.docker.com/editions/community/docker-ce-desktop-windows)

## <a name="add-a-project-to-a-docker-container"></a>Docker kapsayıcısı için proje ekleme

1. Yeni Visual Studio Menüsünden Dosya'> **Yeni > Projesi'> seçin.**
1. Yeni Proje **iletişim kutusunun** Şablonlar **bölümünde Visual** C# ve **Web'> seçin.**
1. ASP.NET **Core Web Uygulaması'ı** seçin veya .NET Core yerine .NET Framework kullanmak için Web **Uygulaması'ASP.NET seçin.**
1. Yeni uygulamanıza bir ad girin (veya varsayılan değeri alır) ve Tamam'ı **seçin.**
1. **Web Uygulaması'ı seçin.**
1. **Docker Desteğini Etkinleştir onay** kutusunu işaretleyin.

   ![Docker Desteğini Etkinleştir onay kutusu](../../media/container-tools/enable-docker-support.PNG)

   Ekran görüntüsünde .NET Core; .NET Framework kullanıyorsanız, biraz farklı görünüyor.

1. İstediğiniz kapsayıcı türünü seçin (Windows veya Linux) ve Tamam'a **tıklayın.**

## <a name="dockerfile-overview"></a>Dockerfile'a genel bakış

Projede son bir Docker görüntüsü oluşturma tarifi olan *Dockerfile* oluşturulur. Içindeki komutları [anlamak için Dockerfile](https://docs.docker.com/engine/reference/builder/) başvurusuna bakın:

```
FROM mcr.microsoft.com/dotnet/aspnet:2.1 AS base
WORKDIR /app
EXPOSE 59518
EXPOSE 44364

FROM mcr.microsoft.com/dotnet/sdk:2.1 AS build
WORKDIR /src
COPY HelloDockerTools/HelloDockerTools.csproj HelloDockerTools/
RUN dotnet restore HelloDockerTools/HelloDockerTools.csproj
COPY . .
WORKDIR /src/HelloDockerTools
RUN dotnet build HelloDockerTools.csproj -c Release -o /app

FROM build AS publish
RUN dotnet publish HelloDockerTools.csproj -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "HelloDockerTools.dll"]
```

Yukarıdaki *Dockerfile* [dosyası microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) görüntüsünü temel almaktadır ve projenizi oluşturma ve kapsayıcıya ekleyerek temel görüntüyü değiştirme yönergelerini içerir. .NET Framework kullanıyorsanız temel görüntü farklı olur.

Yeni proje iletişim kutusunun HTTPS için **yapılandır** onay kutusu işaretli olduğunda *Dockerfile iki bağlantı* noktasını kullanıma sağlar. HTTP trafiği için bir bağlantı noktası kullanılır; diğer bağlantı noktası HTTPS için kullanılır. Onay kutusu işaretli değilse, HTTP trafiği için tek bir bağlantı noktası (80) kullanıma hazır olur.

## <a name="debug"></a>Hata Ayıklama

Araç çubuğundaki hata ayıklama açılan **menüsünden Docker'ı** seçin ve uygulamada hata ayıklamaya başlayabilirsiniz. Bir sertifikaya güvenme hakkında bir istem ile bir ileti alabilirsiniz; devam etmek için sertifikaya güvenmeyi seçin.

Çıkış **penceresi** hangi eylemlerin gerçekleştir olduğunu gösterir.

NuGet **Paket Yöneticisi, Konsol'da** Araçlar menüsünden Paket Yöneticisi **Konsolu'>** nu Paket Yöneticisi (PMC) **Paket Yöneticisi açın.**

Uygulamanın sonuçta elde edilen Docker görüntüsü geliştirme olarak *etiketlenir.* Görüntü, *microsoft/dotnet* temel *görüntüsünün 2.1-aspnetcore-runtime* etiketine dayalıdır. Paket Yöneticisi `docker images` **Console** (PMC) penceresinde komutunu çalıştırın. Makinede görüntüler görüntülenir:

```console
REPOSITORY        TAG                     IMAGE ID      CREATED         SIZE
hellodockertools  dev                     d72ce0f1dfe7  30 seconds ago  255MB
microsoft/dotnet  2.1-aspnetcore-runtime  fcc3887985bb  6 days ago      255MB
```

> [!NOTE]
> Geliştirme **görüntüsü** uygulama ikililerini ve diğer içeriği içermez çünkü **Hata** ayıklama yapılandırmaları, birim bağlamayı kullanarak yeniden düzenleme ve hata ayıklama deneyimi sağlar. Tüm içerikleri içeren bir üretim görüntüsü oluşturmak için Yayın **yapılandırmasını** kullanın.

`docker ps`PMC'de komutunu çalıştırın. Uygulamanın kapsayıcıyı kullanarak çalıştır):

```console
CONTAINER ID        IMAGE                  COMMAND                   CREATED             STATUS              PORTS                   NAMES
baf9a678c88d        hellodockertools:dev   "C:\\remote_debugge..."   21 seconds ago      Up 19 seconds       0.0.0.0:37630->80/tcp   dockercompose4642749010770307127_hellodockertools_1
```

## <a name="publish-docker-images"></a>Docker görüntülerini yayımlama

Uygulamanın geliştirme ve hata ayıklama döngüsü tamamlandıktan sonra, uygulamanın üretim görüntüsünü oluşturabilirsiniz.

1. Yapılandırma açılan listesinde Yayın'a **ve** uygulamayı derlemeye devam edin.
1. Içinde projenize sağ tıklayın ve **Çözüm Gezgini'yi** **seçin.**
1. Hedefi yayımla iletişim kutusunda Container Registry **seçin.**
1. Yeni **Oluştur'u Azure Container Registry** yayımla'ya **tıklayın.**
1. Yeni bir dosya oluştur içinde **istediğiniz değerleri Azure Container Registry.**

    | Ayar      | Önerilen değer  | Açıklama                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **DNS Ön Eki** | Genel olarak benzersiz bir ad | Kapsayıcı kayıt defterinizi benzersiz olarak tanımlayan ad. |
    | **Abonelik** | Aboneliğinizi seçin | Kullanılacak Azure aboneliği. |
    | **[Kaynak Grubu](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  Kapsayıcı kayıt defterinizin oluşturulacak kaynak grubunun adı. Yeni kaynak grubu oluşturmak **Yeni**'yi seçin.|
    | **[SKU](/azure/container-registry/container-registry-skus)** | Standart | Kapsayıcı kayıt defterinin hizmet katmanı  |
    | **Kayıt Defteri Konumu** | Size yakın bir konum | Size veya kapsayıcı kayıt [defterinizi](https://azure.microsoft.com/regions/) kullanan diğer hizmetlere yakın bir bölgede konum seçin. |

    ![Visual Studio oluştur iletişim Azure Container Registry oluştur][0]

1. **Oluştur** seçeneğine tıklayın

## <a name="next-steps"></a>Sonraki adımlar

Artık kapsayıcıyı kayıt defterinden Docker görüntülerini çalıştırabilen herhangi bir ana bilgisayar [örneğine](/azure/container-instances/container-instances-tutorial-deploy-app)Azure Container Instances.

[0]:../../media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog.png
