---
title: Docker kapsayıcısını ASP.NET ACR kayıt defterine dağıtma
description: Bir ASP.NET veya ASP.NET Core web uygulamasını konteyner kayıt defterine dağıtmak için Visual Studio Container Tools'u nasıl kullanacağınızı öğrenin
author: ghogen
manager: jillfra
ms.assetid: e5e81c5e-dd18-4d5a-a24d-a932036e78b9
ms.devlang: dotnet
ms.topic: conceptual
ms.technology: vs-azure
ms.date: 03/14/2019
ms.author: ghogen
ms.openlocfilehash: cfed918633f62700f464ee5f9911fbbfc6463c36
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75916909"
---
# <a name="deploy-an-aspnet-container-to-a-container-registry-using-visual-studio"></a>Visual Studio kullanarak kapsayıcı kayıt defterine ASP.NET kapsayıcısı dağıtma

## <a name="overview"></a>Genel Bakış

Docker hafif bir konteyner motoru, uygulamaları ve hizmetleri barındırmak için kullanabileceğiniz sanal bir makine, bazı şekillerde benzer.
Bu öğretici, konteynerleştirilmiş uygulamanızı azure [konteyner kayıt defterine](https://azure.microsoft.com/services/container-registry)yayınlamak için Visual Studio'yu kullanmanızı kolaylaştırır.

Azure aboneliğiniz yoksa, başlamadan önce [ücretsiz](https://azure.microsoft.com/free/dotnet/?utm_source=acr-publish-doc&utm_medium=docs&utm_campaign=docs) bir hesap oluşturun.

## <a name="prerequisites"></a>Önkoşullar

Bu öğreticiyi tamamlamak için:

::: moniker range="vs-2017"
* [Visual Studio 2017'nin](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)en son sürümünü "ASP.NET ve web geliştirme" iş yüküyle yükleyin
::: moniker-end
::: moniker range=">=vs-2019"
* [Visual Studio 2019'un](https://visualstudio.microsoft.com/downloads) en son sürümünü "ASP.NET ve web geliştirme" iş yüküyle yükleyin
::: moniker-end
* [Windows için Docker'ı](https://docs.docker.com/docker-for-windows/install/) yükleme

## <a name="create-an-aspnet-core-web-app"></a>ASP.NET Core web uygulaması oluşturma
Aşağıdaki adımlar, bu öğreticide kullanılacak temel bir ASP.NET Core uygulaması oluşturmada size yol gösterecektir. Zaten bir projeniz varsa, bu bölümü atlayabilirsiniz.

::: moniker range="vs-2017"
[!INCLUDE [create-aspnet5-app](../azure/includes/create-aspnet5-app.md)]
::: moniker-end
::: moniker range=">=vs-2019"
[!INCLUDE [create-aspnet5-app](../azure/includes/vs-2019/create-aspnet5-app-2019.md)]
::: moniker-end

## <a name="publish-your-container-to-azure-container-registry"></a>Kapsayıcınızı Azure Kapsayıcı Kayıt Defteri'nde yayımlayın
1. **Çözüm Gezgini'nde** projenize sağ tıklayın ve **Yayımla'yı**seçin.
2. Yayımlama hedef iletişim **kutusunda, Kapsayıcı Kayıt Defteri** sekmesini seçin.
3. **Yeni Azure Kapsayıcı Kayıt Defteri'ni** seçin ve **Yayımla'yı**tıklatın.
4. **Yeni bir Azure Kapsayıcı Kayıt Defteri Oluştur'da**istediğiniz değerleri doldurun.

    | Ayar      | Önerilen değer  | Açıklama                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **DNS Ön Eki** | Genel olarak benzersiz bir ad | Konteyner kayıt defterinizi benzersiz olarak tanımlayan ad. |
    | **Abonelik** | Aboneliğinizi seçin | Kullanılacak Azure aboneliği. |
    | **[Kaynak Grubu](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  Kapsayıcı kayıt defterinizi oluşturacak kaynak grubunun adı. Yeni kaynak grubu oluşturmak **Yeni**'yi seçin.|
    | **[Sku](/azure/container-registry/container-registry-skus)** | Standart | Konteyner kayıt defterinin hizmet katmanı  |
    | **Kayıt Defteri Konumu** | Size yakın bir konum | Size yakın bir [bölgede](https://azure.microsoft.com/regions/) veya konteyner kayıt defterinizi kullanacak diğer hizmetlerin yakınında bir Konum seçin. |

    ![Visual Studio's oluşturmak Azure Konteyner Kayıt Defteri iletişim kutusu](media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog.png)

5. **Oluştur'u** tıklatın

Artık kapsayıcıyı kayıt defterinden Docker görüntülerini çalıştırabilen herhangi bir ana bilgisayara çekebilirsiniz (örneğin [Azure Kapsayıcı Örnekleri).](/azure/container-instances/container-instances-tutorial-deploy-app)

## <a name="see-also"></a>Ayrıca bkz.

[Hızlı başlatma: Azure CLI'yi kullanarak Azure'da bir kapsayıcı örneğini dağıtma](/azure/container-instances/container-instances-quickstart)
