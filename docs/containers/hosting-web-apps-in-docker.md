---
title: ACR kayıt defterine ASP.NET Docker kapsayıcısı dağıtma
description: Bir kapsayıcı kayıt defterine ASP.NET veya ASP.NET Core Web uygulaması dağıtmak için Visual Studio kapsayıcı araçları 'nı nasıl kullanacağınızı öğrenin
author: ghogen
manager: jillfra
ms.assetid: e5e81c5e-dd18-4d5a-a24d-a932036e78b9
ms.devlang: dotnet
ms.topic: how-to
ms.technology: vs-azure
ms.date: 03/14/2019
ms.author: ghogen
ms.openlocfilehash: 4626b64f5e733fec049d56dfe53407cc0fe31566
ms.sourcegitcommit: 2c26d6e6f2a5c56ae5102cdded7b02f2d0fd686c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2020
ms.locfileid: "88168714"
---
# <a name="deploy-an-aspnet-container-to-a-container-registry-using-visual-studio"></a>Visual Studio kullanarak kapsayıcı kayıt defterine ASP.NET kapsayıcısı dağıtma

## <a name="overview"></a>Genel Bakış

Docker, uygulamaları ve Hizmetleri barındırmak için kullanabileceğiniz bir sanal makineye bazı yollarla benzer bir basit kapsayıcı altyapısıdır.
Bu öğretici, Kapsayıcılı uygulamanızı bir [Azure Container Registry](https://azure.microsoft.com/services/container-registry)yayımlamak Için Visual Studio 'yu kullanma konusunda size kılavuzluk eder.

Azure aboneliğiniz yoksa başlamadan önce [ücretsiz bir hesap](https://azure.microsoft.com/free/dotnet/?utm_source=acr-publish-doc&utm_medium=docs&utm_campaign=docs) oluşturun.

## <a name="prerequisites"></a>Ön koşullar

Bu öğreticiyi tamamlamak için:

::: moniker range="vs-2017"
* "ASP.NET and Web Development" iş yüküne sahip [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)' in en son sürümünü yükler
::: moniker-end
::: moniker range=">=vs-2019"
* "ASP.NET and Web Development" iş yüküne sahip [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) ' in en son sürümünü yükler
::: moniker-end
* [Docker for Windows](https://docs.docker.com/docker-for-windows/install/) yüklensin

## <a name="create-an-aspnet-core-web-app"></a>ASP.NET Core web uygulaması oluşturma

Aşağıdaki adımlar, bu öğreticide kullanılacak temel bir ASP.NET Core uygulaması oluştururken size rehberlik eder. Zaten bir projeniz varsa, bu bölümü atlayabilirsiniz.

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
4. **Yeni Azure Container Registry oluştur ' a**istediğiniz değerleri girin.

    | Ayar      | Önerilen değer  | Açıklama                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **DNS Ön Eki** | Genel olarak benzersiz bir ad | Kapsayıcı kayıt defterinizi benzersiz bir şekilde tanımlayan ad. |
    | **Abonelik** | Aboneliğinizi seçin | Kullanılacak Azure aboneliği. |
    | **[Kaynak grubu](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  Kapsayıcı kayıt defterinizin oluşturulacağı kaynak grubunun adı. Yeni kaynak grubu oluşturmak **Yeni**'yi seçin.|
    | **[SKU](/azure/container-registry/container-registry-skus)** | Standart | Kapsayıcı kayıt defterinin hizmet katmanı  |
    | **Kayıt Defteri Konumu** | Size yakın bir konum | Size yakın bir [bölgede](https://azure.microsoft.com/regions/) veya kapsayıcı kayıt defterinizi kullanacak diğer hizmetlerin yakınında bir konum seçin. |

    ![Visual Studio 'nun Azure Container Registry oluştur iletişim kutusu](media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog.png)

5. **Oluştur** seçeneğine tıklayın
::: moniker-end

::: moniker range=">=vs-2019"
## <a name="publish-your-container-to-azure-container-registry"></a>Kapsayıcınızı Azure Container Registry yayımlayın
1. **Çözüm Gezgini** ' de projenize sağ tıklayın ve **Yayımla**' yı seçin.
2. **Yayımla** Iletişim kutusunda **Docker Container Registry**öğesini seçin.

   ![Yayımla iletişim kutusunun ekran görüntüsü-Docker Container Registry seçin](media/container-tools/vs-2019/docker-container-registry.png)

3. **Yeni Azure Container Registry oluştur**öğesini seçin.
 
   ![Yayımla iletişim kutusunun ekran görüntüsü-yeni oluştur Azure Container Registry seçin](media/container-tools/vs-2019/select-existing-or-create-new-azure-container-registry.png)

4. **Azure Container Registry** ekranında istediğiniz değerleri girin.

    | Ayar      | Önerilen değer  | Açıklama                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **DNS Ön Eki** | Genel olarak benzersiz bir ad | Kapsayıcı kayıt defterinizi benzersiz bir şekilde tanımlayan ad. |
    | **Abonelik** | Aboneliğinizi seçin | Kullanılacak Azure aboneliği. |
    | **[Kaynak grubu](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  Kapsayıcı kayıt defterinizin oluşturulacağı kaynak grubunun adı. Yeni kaynak grubu oluşturmak **Yeni**'yi seçin.|
    | **[SKU](/azure/container-registry/container-registry-skus)** | Standart | Kapsayıcı kayıt defterinin hizmet katmanı  |
    | **Kayıt Defteri Konumu** | Size yakın bir konum | Size yakın bir [bölgede](https://azure.microsoft.com/regions/) veya kapsayıcı kayıt defterinizi kullanacak diğer hizmetlerin yakınında bir konum seçin. |

    ![Visual Studio 'nun Azure Container Registry oluştur iletişim kutusu](media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog-2019.png)

5. **Oluştur**’a tıklayın.

6. İşlemi gerçekleştirmek için **son** ' a tıklayın.
::: moniker-end

Artık kapsayıcıyı, kayıt defterinden Docker görüntülerini çalıştırabilen herhangi bir konağa çekebilirsiniz, örneğin [Azure Container Instances](/azure/container-instances/container-instances-tutorial-deploy-app).

## <a name="see-also"></a>Ayrıca bkz.

[Hızlı başlangıç: Azure CLı kullanarak Azure 'da kapsayıcı örneği dağıtma](/azure/container-instances/container-instances-quickstart)
