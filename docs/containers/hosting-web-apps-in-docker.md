---
title: ASP.NET docker kapsayıcısını acr kayıt defterine dağıtma
description: bir kapsayıcı kayıt defterine ASP.NET veya ASP.NET Core web uygulaması dağıtmak için Visual Studio kapsayıcı araçlarını kullanmayı öğrenin
author: ghogen
manager: jmartens
ms.assetid: e5e81c5e-dd18-4d5a-a24d-a932036e78b9
ms.devlang: dotnet
ms.topic: how-to
ms.technology: vs-container-tools
ms.date: 03/15/2021
ms.author: ghogen
ms.openlocfilehash: eb1b22273a3fe946d7760bccae9583c4b1d6726c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122091246"
---
# <a name="deploy-an-aspnet-container-to-a-container-registry-using-visual-studio"></a>Visual Studio kullanarak kapsayıcı kayıt defterine ASP.NET kapsayıcısı dağıtma

## <a name="overview"></a>Genel Bakış

Docker, uygulamaları ve Hizmetleri barındırmak için kullanabileceğiniz bir sanal makineye bazı yollarla benzer bir basit kapsayıcı altyapısıdır.
bu öğretici, kapsayıcılı uygulamanızı bir [Azure Container Registry](https://azure.microsoft.com/services/container-registry)yayımlamak için Visual Studio kullanma konusunda size kılavuzluk eder.

Azure aboneliğiniz yoksa başlamadan önce [ücretsiz bir hesap](https://azure.microsoft.com/free/dotnet/?utm_source=acr-publish-doc&utm_medium=docs&utm_campaign=docs) oluşturun.

## <a name="prerequisites"></a>Önkoşullar

Bu öğreticiyi tamamlamak için:

::: moniker range="vs-2017"
* "ASP.NET ve web geliştirme" iş yüküyle [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)' nin en son sürümünü yükler
::: moniker-end
::: moniker range=">=vs-2019"
* "ASP.NET ve web geliştirme" iş yüküyle [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) ' nin en son sürümünü yükler
::: moniker-end
* [Docker for Windows](https://docs.docker.com/docker-for-windows/install/) yüklensin

## <a name="create-an-aspnet-core-web-app"></a>ASP.NET Core web uygulaması oluşturma

aşağıdaki adımlar, bu öğreticide kullanılacak temel bir ASP.NET Core uygulaması oluştururken size rehberlik eder. Zaten bir projeniz varsa, bu bölümü atlayabilirsiniz.

::: moniker range="vs-2017"
[!INCLUDE [create-aspnet5-app](../azure/includes/create-aspnet5-app.md)]
::: moniker-end
::: moniker range=">=vs-2019"
[!INCLUDE [create-aspnet5-app](../azure/includes/vs-2019/create-aspnet5-app-2019.md)]
::: moniker-end

::: moniker range="vs-2017"

## <a name="publish-your-container-to-azure-container-registry"></a>Kapsayıcınızı Azure Container Registry yayımlayın

1. **Çözüm Gezgini** ' de projenize sağ tıklayın ve **Yayımla**' yı seçin.
2. **Hedefi Yayımla** iletişim kutusunda **Container Registry**' yi seçin.
3. **Yeni Azure Container Registry** seçip **Yayımla**' ya tıklayın.
4. **Yeni Azure Container Registry oluştur ' a** istediğiniz değerleri girin.

    | Ayar      | Önerilen değer  | Açıklama                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **DNS Ön Eki** | Genel olarak benzersiz bir ad | Kapsayıcı kayıt defterinizi benzersiz bir şekilde tanımlayan ad. |
    | **Abonelik** | Aboneliğinizi seçin | Kullanılacak Azure aboneliği. |
    | **[Kaynak grubu](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  Kapsayıcı kayıt defterinizin oluşturulacağı kaynak grubunun adı. Yeni kaynak grubu oluşturmak **Yeni**'yi seçin.|
    | **[SKU](/azure/container-registry/container-registry-skus)** | Standart | Kapsayıcı kayıt defterinin hizmet katmanı  |
    | **Kayıt Defteri Konumu** | Size yakın bir konum | Size yakın bir [bölgede](https://azure.microsoft.com/regions/) veya kapsayıcı kayıt defterinizi kullanacak diğer hizmetlerin yakınında bir konum seçin. |

    ![Visual Studio Azure Container Registry oluştur iletişim kutusu](media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog.png)

5. **Oluştur** seçeneğine tıklayın
::: moniker-end

::: moniker range=">=vs-2019"
## <a name="publish-your-container-to-azure-container-registry"></a>Kapsayıcınızı Azure Container Registry yayımlayın
1. **Çözüm Gezgini** ' de projenize sağ tıklayın ve **Yayımla**' yı seçin.
2. **Yayımla** Iletişim kutusunda **Docker Container Registry** öğesini seçin.

   ![Yayımla iletişim kutusunun ekran görüntüsü-Docker Container Registry seçin](media/container-tools/vs-2019/docker-container-registry.png)

3. **Yeni Azure Container Registry oluştur** öğesini seçin.
 
   ![Yayımla iletişim kutusunun ekran görüntüsü-yeni oluştur Azure Container Registry seçin](media/container-tools/vs-2019/select-existing-or-create-new-azure-container-registry.png)

4. **Azure Container Registry** ekranında istediğiniz değerleri girin.

    | Ayar      | Önerilen değer  | Açıklama                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **DNS Ön Eki** | Genel olarak benzersiz bir ad | Kapsayıcı kayıt defterinizi benzersiz bir şekilde tanımlayan ad. |
    | **Abonelik** | Aboneliğinizi seçin | Kullanılacak Azure aboneliği. |
    | **[Kaynak grubu](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  Kapsayıcı kayıt defterinizin oluşturulacağı kaynak grubunun adı. Yeni kaynak grubu oluşturmak **Yeni**'yi seçin.|
    | **[SKU](/azure/container-registry/container-registry-skus)** | Standart | Kapsayıcı kayıt defterinin hizmet katmanı  |
    | **Kayıt Defteri Konumu** | Size yakın bir konum | Size yakın bir [bölgede](https://azure.microsoft.com/regions/) veya kapsayıcı kayıt defterinizi kullanacak diğer hizmetlerin yakınında bir konum seçin. |

    ![Visual Studio Azure Container Registry oluştur iletişim kutusu](media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog-2019.png)

5. **Oluştur**’a tıklayın.

6. İşlemi gerçekleştirmek için **son** ' a tıklayın.
::: moniker-end

Artık kapsayıcıyı, kayıt defterinden Docker görüntülerini çalıştırabilen herhangi bir konağa çekebilirsiniz, örneğin [Azure Container Instances](/azure/container-instances/container-instances-tutorial-deploy-app).

## <a name="see-also"></a>Ayrıca bkz.

[Hızlı başlangıç: Azure CLı kullanarak Azure 'da kapsayıcı örneği dağıtma](/azure/container-instances/container-instances-quickstart)
