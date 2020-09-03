---
title: ASP.NET Core ile Visual Studio kapsayıcı araçları
author: ghogen
description: Visual Studio 2017 araçları 'nı ve Docker for Windows kullanmayı öğrenin
ms.author: ghogen
ms.date: 02/01/2019
ms.technology: vs-azure
ms.topic: include
ms.openlocfilehash: 627b0b1260a3ccdd401dbb170f8e2dfffadea2dc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "81389952"
---
Visual Studio ile Kapsayıcılı ASP.NET Core uygulamaları kolayca oluşturabilir, ayıklayabilir ve çalıştırabilir ve bunları Azure Container Registry (ACR), Docker Hub, Azure App Service veya kendi kapsayıcı kayıt defterinizde yayımlayabilirsiniz. Bu makalede ACR 'ye yayımlanacak.

## <a name="prerequisites"></a>Ön koşullar

* [Docker Masaüstü](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* **Web geliştirme**, **Azure Araçları** iş yükü ve/veya **.NET Core platformlar arası geliştirme** iş yükü yüklü olan [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)
* Bir Azure aboneliği Azure Container Registry yayımlamak için. [Ücretsiz deneme Için kaydolun](https://azure.microsoft.com/free/dotnet/).

## <a name="installation-and-setup"></a>Yükleme ve kurulum

Docker yüklemesi için ilk olarak [Windows Için Docker Desktop](https://docs.docker.com/docker-for-windows/install/#what-to-know-before-you-install)'taki bilgileri gözden geçirin: yüklemeden önce bilmeniz gerekenler. Sonra [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)'ı yükler.

## <a name="add-a-project-to-a-docker-container"></a>Docker kapsayıcısına proje ekleme

1. Visual Studio menüsünden **dosya > yeni > proje**' yi seçin.
1. **Yeni proje** Iletişim kutusunun **Şablonlar** bölümünde, **Visual C# > Web**' i seçin.
1. **ASP.NET Core Web uygulaması** ' nı seçin veya .NET Core yerine .NET Framework kullanmak Istiyorsanız **ASP.NET Web uygulaması**' nı seçin.
1. Yeni uygulamanıza bir ad verin (veya varsayılanı alın) ve **Tamam**' ı seçin.
1. **Web uygulaması**' nı seçin.
1. **Docker desteğini etkinleştir** onay kutusunu işaretleyin.

   ![Docker desteğini etkinleştir onay kutusu](../../media/container-tools/enable-docker-support.PNG)

   Ekran görüntüsünde .NET Core gösterilir; .NET Framework kullanıyorsanız, biraz farklı görünür.

1. İstediğiniz kapsayıcı türünü (Windows veya Linux) seçin ve **Tamam**' a tıklayın.

## <a name="dockerfile-overview"></a>Dockerfile genel bakış

Bir *Dockerfile*, son bir Docker görüntüsü oluşturmaya yönelik tarif, projede oluşturulur. İçindeki komutları anlamak için [Dockerfile başvurusuna](https://docs.docker.com/engine/reference/builder/) bakın.

```
FROM microsoft/dotnet:2.1-aspnetcore-runtime AS base
WORKDIR /app
EXPOSE 59518
EXPOSE 44364

FROM microsoft/dotnet:2.1-sdk AS build
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

Yukarıdaki *Dockerfile* , [Microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) görüntüsünü temel alır ve projenizi oluşturup kapsayıcıya ekleyerek temel görüntüyü değiştirmeye yönelik yönergeler içerir. .NET Framework kullanıyorsanız, temel görüntü farklı olur.

Yeni proje iletişim kutusunun **https Için Yapılandır** onay kutusu Işaretlendiğinde, *dockerfile* iki bağlantı noktasını kullanıma sunar. HTTP trafiği için bir bağlantı noktası kullanılır; diğer bağlantı noktası HTTPS için kullanılır. Onay kutusu işaretli değilse, HTTP trafiği için tek bir bağlantı noktası (80) gösterilir.

## <a name="debug"></a>Hata ayıklama

Araç çubuğundaki hata ayıklama açılır listesinden **Docker** ' ı seçin ve uygulamada hata ayıklamayı başlatın. Bir sertifikaya güvenmek üzere bir istem içeren bir ileti görebilirsiniz. devam etmek için sertifikaya güvenmeyi seçin.

**Çıkış** penceresinde hangi eylemlerin gerçekleştiği gösterilmektedir.

Menü **araçları**> NuGet Paket Yöneticisi, **Paket Yöneticisi konsolu**' ndan **Paket Yöneticisi konsolu 'nu** (PMC) açın.

Uygulamanın elde edilen Docker görüntüsü *dev*olarak etiketlendi. Görüntü, *Microsoft/DotNet* temel görüntüsünün *2,1-aspnetcore-Runtime* etiketine dayalıdır. `docker images`Komutunu **Paket Yöneticisi konsolu** (PMC) penceresinde çalıştırın. Makinedeki görüntüler görüntülenir:

```console
REPOSITORY        TAG                     IMAGE ID      CREATED         SIZE
hellodockertools  dev                     d72ce0f1dfe7  30 seconds ago  255MB
microsoft/dotnet  2.1-aspnetcore-runtime  fcc3887985bb  6 days ago      255MB
```

> [!NOTE]
> **Geliştirme** görüntüsü, uygulama ikililerini ve diğer içerikleri Içermez. **hata ayıklama** yapılandırmalarında, yinelemeli düzenleme ve hata ayıklama deneyimi sağlamak için birim bağlama kullanılır. Tüm içerikleri içeren bir üretim görüntüsü oluşturmak için **yayın** yapılandırmasını kullanın.

`docker ps`Komutu PMC 'de çalıştırın. Uygulamanın, kapsayıcıyı kullanarak çalıştığını unutmayın:

```console
CONTAINER ID        IMAGE                  COMMAND                   CREATED             STATUS              PORTS                   NAMES
baf9a678c88d        hellodockertools:dev   "C:\\remote_debugge..."   21 seconds ago      Up 19 seconds       0.0.0.0:37630->80/tcp   dockercompose4642749010770307127_hellodockertools_1
```

## <a name="publish-docker-images"></a>Docker görüntülerini yayımlama

Uygulamanın geliştirme ve hata ayıklama döngüsünü tamamladıktan sonra uygulamanın üretim görüntüsünü oluşturabilirsiniz.

1. Yapılandırma açılır öğesini değiştirerek uygulamayı **serbest bırakın** ve oluşturun.
1. **Çözüm Gezgini** ' de projenize sağ tıklayın ve **Yayımla**' yı seçin.
1. Hedefi Yayımla iletişim kutusunda **Container Registry** sekmesini seçin.
1. **Yeni Azure Container Registry oluştur** ' u seçin ve **Yayımla**' ya tıklayın.
1. **Yeni Azure Container Registry oluştur ' a**istediğiniz değerleri girin.

    | Ayar      | Önerilen değer  | Açıklama                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **DNS Ön Eki** | Genel olarak benzersiz bir ad | Kapsayıcı kayıt defterinizi benzersiz bir şekilde tanımlayan ad. |
    | **Abonelik** | Aboneliğinizi seçin | Kullanılacak Azure aboneliği. |
    | **[Kaynak grubu](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  Kapsayıcı kayıt defterinizin oluşturulacağı kaynak grubunun adı. Yeni kaynak grubu oluşturmak **Yeni**'yi seçin.|
    | **[SKU](/azure/container-registry/container-registry-skus)** | Standart | Kapsayıcı kayıt defterinin hizmet katmanı  |
    | **Kayıt Defteri Konumu** | Size yakın bir konum | Size yakın bir [bölgede](https://azure.microsoft.com/regions/) veya kapsayıcı kayıt defterinizi kullanacak diğer hizmetlerin yakınında bir konum seçin. |

    ![Visual Studio 'nun Azure Container Registry oluştur iletişim kutusu][0]

1. **Oluştur** seçeneğine tıklayın

## <a name="next-steps"></a>Sonraki adımlar

Artık kapsayıcıyı, kayıt defterinden Docker görüntülerini çalıştırabilen herhangi bir konağa çekebilirsiniz, örneğin [Azure Container Instances](/azure/container-instances/container-instances-tutorial-deploy-app).

[0]:../../media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog.png
