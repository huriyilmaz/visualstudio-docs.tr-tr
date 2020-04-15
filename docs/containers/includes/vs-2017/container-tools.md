---
title: ASP.NET Core ile Visual Studio Konteyner Araçları
author: ghogen
description: Visual Studio 2017 araç ve Docker windows için nasıl kullanılacağını öğrenin
ms.author: ghogen
ms.date: 02/01/2019
ms.technology: vs-azure
ms.topic: include
ms.openlocfilehash: 627b0b1260a3ccdd401dbb170f8e2dfffadea2dc
ms.sourcegitcommit: cc58ca7ceae783b972ca25af69f17c9f92a29fc2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389952"
---
Visual Studio ile, konteynırlaştırılmış ASP.NET Core uygulamaları oluşturabilir, hata ayıklayabilir ve çalıştırabilir ve bunları Azure Konteyner Kayıt Defteri 'nde (ACR), Docker Hub'a, Azure Uygulama Hizmeti'ne veya kendi konteyner kayıt defterinize yayınlayabilirsiniz. Bu makalede, ACR'de yayınlayacağız.

## <a name="prerequisites"></a>Ön koşullar

* [Docker Masaüstü](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) Web **Geliştirme,** **Azure Araçları** iş yükü ve/veya **.NET Core çapraz platform geliştirme** iş yükü yüklü
* Azure Kapsayıcı Kayıt Defteri'nde yayımlamak için bir Azure aboneliği. [Ücretsiz deneme sürümü için kaydolun.](https://azure.microsoft.com/free/dotnet/)

## <a name="installation-and-setup"></a>Kurulum ve kurulum

Docker yüklemesi için, windows için Docker Desktop'daki bilgileri ilk olarak gözden [geçirin: Yüklemeden önce bilinmesi gerekenler.](https://docs.docker.com/docker-for-windows/install/#what-to-know-before-you-install) Ardından, [Docker Desktop'ı](https://hub.docker.com/editions/community/docker-ce-desktop-windows)yükleyin.

## <a name="add-a-project-to-a-docker-container"></a>Docker kapsayıcısına proje ekleme

1. Visual Studio menüsünden **Dosya > Yeni > Projesi'ni**seçin.
1. **Yeni Proje** iletişim kutusunun **Şablonlar** bölümünde Visual **C# > Web'i**seçin.
1. **Core Web ApplicationASP.NET** seçin veya .NET Core yerine .NET Framework'ü kullanmak istiyorsanız, **Web Uygulaması ASP.NET**seçin.
1. Yeni uygulamanıza bir ad verin (veya varsayılanı alın) ve **Tamam'ı**seçin.
1. **Web Uygulamasını**Seçin.
1. Docker **Destek'i Etkinleştir** onay kutusunu işaretleyin.

   ![Docker Destek onay kutusunu etkinleştir](../../media/container-tools/enable-docker-support.PNG)

   Ekran görüntüsü .NET Core'u gösterir; .NET Framework kullanıyorsanız, biraz farklı görünüyor.

1. İstediğiniz kapsayıcı türünü seçin (Windows veya Linux) ve **Tamam'ı**tıklatın.

## <a name="dockerfile-overview"></a>Dockerfile'a genel bakış

Bir *Dockerfile*, son docker görüntü oluşturmak için tarifi, projeoluşturulur. İçindeki komutların anlaşılması için [Dockerfile başvurusuna](https://docs.docker.com/engine/reference/builder/) bakın.:

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

Önceki *Dockerfile* [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) resmine dayanır ve projenizi oluşturarak ve kapsayıcıya ekleyerek temel görüntüyü değiştirmek için yönergeler içerir. .NET Framework kullanıyorsanız, temel görüntü farklı olacaktır.

Yeni proje iletişim kutusunun HTTPS için **Yapılandırma** onay kutusu işaretlendiğinde, *Dockerfile* iki bağlantı noktasını ortaya çıkarır. Bir bağlantı noktası HTTP trafiği için kullanılır; diğer bağlantı noktası HTTPS için kullanılır. Onay kutusu işaretlenmezse, HTTP trafiği için tek bir bağlantı noktası (80) açığa çıkarır.

## <a name="debug"></a>Hata ayıklama

Araç çubuğundaki hata ayıklama açılır tarihinden **Docker'ı** seçin ve uygulamayı hata ayıklamaya başlayın. Bir sertifikaya güvenme yle ilgili bir istem içeren bir ileti görebilirsiniz; devam edecek sertifikaya güvenmeyi seçin.

**Çıktı** penceresi hangi eylemlerin gerçekleştiğini gösterir.

Paket **Yöneticisi Konsolu** 'nuGet Package Manager, Package Manager Console> **menüden** Paket **Yöneticisi Konsolu'nu**(PMC) açın.

Uygulamanın ortaya çıkan Docker görüntüsü *dev*olarak etiketlenir. Görüntü, *microsoft/dotnet* taban görüntüsünün *2.1-aspnetcore-runtime* etiketine dayanmaktadır. Paketi `docker images` **Yöneticisi Konsolu** (PMC) penceresinde komutu çalıştırın. Makinedeki görüntüler görüntülenir:

```console
REPOSITORY        TAG                     IMAGE ID      CREATED         SIZE
hellodockertools  dev                     d72ce0f1dfe7  30 seconds ago  255MB
microsoft/dotnet  2.1-aspnetcore-runtime  fcc3887985bb  6 days ago      255MB
```

> [!NOTE]
> **Hata ayıklama** yapılandırmaları yinelemeli düzenleme ve hata ayıklama deneyimini sağlamak için ses montajını kullandığından, **dev** görüntüsü uygulama ikililerini ve diğer içerikleri içermez. Tüm içerikleri içeren bir üretim görüntüsü oluşturmak için **Release** yapılandırmasını kullanın.

PMC'de komutu çalıştırın. `docker ps` Uygulamanın kapsayıcıyı kullanarak çalıştığını fark edin:

```console
CONTAINER ID        IMAGE                  COMMAND                   CREATED             STATUS              PORTS                   NAMES
baf9a678c88d        hellodockertools:dev   "C:\\remote_debugge..."   21 seconds ago      Up 19 seconds       0.0.0.0:37630->80/tcp   dockercompose4642749010770307127_hellodockertools_1
```

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

## <a name="next-steps"></a>Sonraki adımlar

Artık kapsayıcıyı kayıt defterinden Docker görüntülerini çalıştırabilen herhangi bir ana bilgisayara çekebilirsiniz (örneğin [Azure Kapsayıcı Örnekleri).](/azure/container-instances/container-instances-tutorial-deploy-app)

[0]:../../media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog.png
