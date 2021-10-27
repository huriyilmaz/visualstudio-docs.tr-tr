---
title: Docker ASP.NET'ı Azure Container Registry
description: Visual Studio Container Tools'ASP.NET veya web ASP.NET Core kapsayıcı kayıt defterine dağıtmayı öğrenin
author: ghogen
manager: jmartens
ms.assetid: e5e81c5e-dd18-4d5a-a24d-a932036e78b9
ms.devlang: dotnet
ms.topic: how-to
ms.technology: vs-container-tools
ms.date: 03/15/2021
ms.author: ghogen
ms.openlocfilehash: 5990f438e7c7f5043fc79154eb1546ed3bc3f740
ms.sourcegitcommit: 4efdab6a579b31927c42531bb3f7fdd92890e4ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/26/2021
ms.locfileid: "130351138"
---
# <a name="deploy-an-aspnet-container-to-a-container-registry-using-visual-studio"></a>Visual Studio kullanarak kapsayıcı kayıt defterine ASP.NET kapsayıcısı dağıtma

## <a name="overview"></a>Genel Bakış

Docker, uygulama ve hizmetleri barındırmak için kullanabileceğiniz bir sanal makineye benzer şekilde hafif bir kapsayıcı altyapısıdır.
Bu öğretici, kapsayıcılı uygulamanızı Visual Studio bir uygulama üzerinde yayımlamak için [Azure Container Registry.](https://azure.microsoft.com/services/container-registry)

Azure aboneliğiniz yoksa başlamadan önce [ücretsiz bir hesap](https://azure.microsoft.com/free/dotnet/?utm_source=acr-publish-doc&utm_medium=docs&utm_campaign=docs) oluşturun.

## <a name="prerequisites"></a>Önkoşullar

Bu öğreticiyi tamamlamak için:

::: moniker range="vs-2017"
* "ASP.NET ve web geliştirme" iş [yüküyle Visual Studio 2017'nin](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)en son sürümünü yükleyin
::: moniker-end
::: moniker range=">=vs-2019"
* "ASP.NET ve web geliştirme" iş yüküyle [Visual Studio 2019'un](https://visualstudio.microsoft.com/downloads) en son sürümünü yükleyin
::: moniker-end
* [Windows için Docker'ı yükleme](https://docs.docker.com/docker-for-windows/install/)

## <a name="create-an-aspnet-core-web-app"></a>ASP.NET Core web uygulaması oluşturma

Aşağıdaki adımlar, bu öğreticide kullanılacak temel ASP.NET Core uygulama oluşturma konusunda size yol sağlar. Zaten bir projeniz varsa bu bölümü atlayabilirsiniz.

::: moniker range="vs-2017"
[!INCLUDE [create-aspnet5-app](../azure/includes/create-aspnet5-app.md)]
::: moniker-end
::: moniker range=">=vs-2019"
[!INCLUDE [create-aspnet5-app](../azure/includes/vs-2019/create-aspnet5-app-2019.md)]
::: moniker-end

::: moniker range="vs-2017"

## <a name="publish-your-container-to-azure-container-registry"></a>Kapsayıcınızı Azure Container Registry

1. Içinde projenize sağ tıklayın ve **Çözüm Gezgini'yi** **seçin.**
2. Hedefi **yayımla iletişim** kutusunda Hedef'i **Container Registry.**
3. Yeni **Giriş'Azure Container Registry'yi** seçin ve Yayımla'ya **tıklayın.**
4. Yeni bir dosya oluştur içinde **istediğiniz değerleri Azure Container Registry.**

    | Ayar      | Önerilen değer  | Açıklama                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **DNS Ön Eki** | Genel olarak benzersiz bir ad | Kapsayıcı kayıt defterinizi benzersiz olarak tanımlayan ad. |
    | **Abonelik** | Aboneliğinizi seçin | Kullanılacak Azure aboneliği. |
    | **[Kaynak Grubu](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  Kapsayıcı kayıt defterinizin oluşturulacak kaynak grubunun adı. Yeni kaynak grubu oluşturmak **Yeni**'yi seçin.|
    | **[SKU](/azure/container-registry/container-registry-skus)** | Standart | Kapsayıcı kayıt defterinin hizmet katmanı  |
    | **Kayıt Defteri Konumu** | Size yakın bir konum | Size veya kapsayıcı kayıt [defterinizi](https://azure.microsoft.com/regions/) kullanan diğer hizmetlere yakın bir bölgede konum seçin. |

    ![Visual Studio oluştur iletişim kutusunu Azure Container Registry ekran görüntüsü.](media/hosting-web-apps-in-docker/vs-azure-container-registry-provisioning-dialog.png)

5. **Oluştur** seçeneğine tıklayın
::: moniker-end

::: moniker range=">=vs-2019"
## <a name="publish-your-container-to-azure-container-registry"></a>Kapsayıcınızı Azure Container Registry
1. Içinde projenize sağ tıklayın ve **Çözüm Gezgini'yi** **seçin.**
2. Yayımla **iletişim kutusunda** **Docker Container Registry.**

   ![Yayımla iletişim kutusunun ekran görüntüsü - Docker Container Registry.](media/container-tools/vs-2019/docker-container-registry.png)

3. Yeni **Oluştur'Azure Container Registry.**
 
   ![Yayımla iletişim kutusunun ekran görüntüsü - Yeni Oluştur'Azure Container Registry.](media/container-tools/vs-2019/select-existing-or-create-new-azure-container-registry.png)

4. İstediğiniz değerleri Azure Container Registry. 

    | Ayar      | Önerilen değer  | Açıklama                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **DNS Ön Eki** | Genel olarak benzersiz bir ad | Kapsayıcı kayıt defterinizi benzersiz olarak tanımlayan ad. |
    | **Abonelik** | Aboneliğinizi seçin | Kullanılacak Azure aboneliği. |
    | **[Kaynak Grubu](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  Kapsayıcı kayıt defterinizin oluşturulacak kaynak grubunun adı. Yeni kaynak grubu oluşturmak **Yeni**'yi seçin.|
    | **[SKU](/azure/container-registry/container-registry-skus)** | Standart | Kapsayıcı kayıt defterinin hizmet katmanı  |
    | **Kayıt Defteri Konumu** | Size yakın bir konum | Size veya kapsayıcı kayıt [defterinizi](https://azure.microsoft.com/regions/) kullanan diğer hizmetlere yakın bir bölgede konum seçin. |

    ![Visual Studio oluştur iletişim kutusunun Azure Container Registry görüntüsü.](media/hosting-web-apps-in-docker/vs-azure-container-registry-provisioning-dialog-2019.png)

5. **Oluştur**’a tıklayın.

6. Işlemi **tamamlamak** için Son'a seçin.
::: moniker-end

Artık kapsayıcıyı kayıt defterinden Docker görüntülerini çalıştırabilen herhangi bir ana bilgisayar örneğine [Azure Container Instances.](/azure/container-instances/container-instances-tutorial-deploy-app)

## <a name="see-also"></a>Ayrıca bkz.

[Hızlı Başlangıç: Azure CLI kullanarak Azure'da kapsayıcı örneği dağıtma](/azure/container-instances/container-instances-quickstart)
