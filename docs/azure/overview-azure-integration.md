---
title: Azure tümleştirmesi
description: Şirket içinde Azure uygulamaları ve hizmetleri geliştirmeyi ve Visual Studio buluta dağıtmayı öğrenin.
author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: overview
ms.date: 10/19/2021
ms.author: ghogen
monikerRange: '>=vs-2019'
ms.openlocfilehash: 6d03b18236c46f4130312839e8c84bac4716a5d2
ms.sourcegitcommit: 32fa8ec0b469a7a9a87de25ff769d8d21d9f30d2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/06/2021
ms.locfileid: "131898151"
---
# <a name="overview-azure-integration"></a>Genel bakış: Azure tümleştirmesi

Azure'a geliştirmeyi ve Visual Studio kolaylaştırmak için tasarlanmış birçok özelliği kullanarak azure'da azure ile çalışabilirsiniz.

## <a name="provision-azure-resources"></a>Azure kaynaklarını sağlama

Bu, mevcut Azure Visual Studio göz atarak arayabilirsiniz. Mevcut kaynakların listesinin üzerinde yenilerini sağlamayı sağlayan bir düğme vardır:

:::moniker range="vs-2019"
![Azure kaynağı seçmeyi gösteren ekran görüntüsü.](./media/select-azure-resource.png)
:::moniker-end
:::moniker range=">=vs-2022"
![Azure kaynağı seçmeyi gösteren ekran görüntüsü.](./media/vs-2022/select-azure-resource.png)
:::moniker-end

> [!NOTE]
> Bu örnekte örnek örnek Azure App Service, ancak desteklemektedir tüm Azure hizmetleri için benzer Visual Studio vardır.

## <a name="browse-and-search-existing-azure-resources"></a>Mevcut Azure kaynaklarına göz atma ve kaynakları arama

Aşağıdaki ekran görüntüsünde, mevcut Azure Visual Studio göz atarak arama gerçekleştirebilirsiniz.

1. Açılan listeyle Azure aboneliğine göre filtreleme
2. Bulunan örnekleri Kaynak Grubu veya Kaynak Türüne göre gruplandırabilirsiniz (bu da size düz bir liste sağlar)
3. Kaynak adına göre arama

:::moniker range="vs-2019"
![Azure kaynaklarına göz atma ve aramayı gösteren ekran görüntüsü](./media/browse-search-azure-resource.png)
:::moniker-end
:::moniker range=">=vs-2022"
![Azure kaynaklarına göz atma ve aramayı gösteren ekran görüntüsü](./media/vs-2022/browse-search-azure-resource.png)
:::moniker-end

> [!NOTE]
> Bu örnekte örnek örnek Azure App Service, ancak desteklemektedir tüm Azure hizmetleri için benzer Visual Studio vardır.

## <a name="deploy-an-application-to-azure-using-publish-or-github-actions"></a>Yayımlama veya Yayımlama Eylemlerini kullanarak Azure'GitHub dağıtma

Projenize sağ tıklayın ve [Çözüm Gezgini](../ide/use-solution-explorer.md) **menüsünden Yayımla'yı** seçin. Yayımla sihirbazı deneyim boyunca size yol sağlar ve projeniz GitHub.com'da barındırılırsa, size otomatik olarak GitHub Actions kullanarak CI/CD yapılandırma fırsatı verilir.

## <a name="configure-azure-dependencies-to-be-emulated-locally-and-connect-to-real-services-at-deployment-time"></a>Azure bağımlılıklarını yerel olarak öykünülacak şekilde yapılandırma ve dağıtım zamanında gerçek hizmetlere bağlanma

Bağlı Hizmetler'i kullanarak uygulamalarınızı yerel öykünücülere ve diğer yerel alternatiflere Azure hizmetleriyle bağlama. Kullanmaya başlayın'da Bağlı Hizmetler düğümüne **sağ** tıklar ve Çözüm Gezgini Hizmetleri **Yönet'i seçin.**

:::moniker range="vs-2019"
![Yerel Azure öykünücülerini gösteren ekran görüntüsü.](./media/local-azure-emulators.png)
:::moniker-end
:::moniker range=">=vs-2022"
![Yerel Azure öykünücülerini gösteren ekran görüntüsü.](./media/vs-2022/local-azure-emulators.png)
:::moniker-end

## <a name="debug-azure-function-projects-offline-without-cost"></a>Azure İşlevi projelerinde maliyet olmadan çevrimdışı hata ayıklama

Visual Studio hata ayıklamaya başlarken Azure İşlevleri hizmetine sorunsuz bir şekilde öykünebilirsiniz. Azure aboneliğiyle oturum alasınız bile.

## <a name="remote-debug-azure-hosting-services-like-azure-app-service"></a>Azure App Service gibi Azure barındırma hizmetlerinden uzaktan hata ayıklama

Bkz. [Visual Studio hata ayıklayıcısı ile çalışan işlemlere ekleme](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md#attach-to-a-net-core-process-running-on-azure-app-service-windows)
