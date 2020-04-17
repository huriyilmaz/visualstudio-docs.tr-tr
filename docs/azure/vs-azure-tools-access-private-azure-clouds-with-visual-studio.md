---
title: Özel Azure bulutları erişim
description: Visual Studio'u kullanarak özel bulut kaynaklarına nasıl erişince gerektiğini öğrenin.
author: ghogen
manager: jillfra
assetId: 9d733c8d-703b-44e7-a210-bb75874c45c8
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/13/2017
ms.author: ghogen
ms.openlocfilehash: 57f92aa797e589bd48cc52296b710617cbe8d732
ms.sourcegitcommit: eef26de3d7a5c971baedbecf3b4941fb683ddb2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/17/2020
ms.locfileid: "81544373"
---
# <a name="accessing-private-azure-clouds-with-visual-studio"></a>Visual Studio ile özel Azure bulutları erişim

Varsayılan olarak Visual Studio, Azure bulutU REST uç noktalarını destekler. Bu makalede, Visual Studio'dan özel buluta erişmek ve onlarla etkileşimde kalmak için özel bulutunuzun sertifikasını nasıl kullanacağınızı öğreneceksiniz.

1. Özel bulut için Azure portalında yayımlama ayarları dosyanızı indirin veya yayımlama ayarları dosyası için yöneticinize başvurun. (Dosya uzantısı `.publishsettings`vardır.)

1. Visual Studio **Server Explorer'da** **Azure** düğümüne sağ tıklayın ve **Abonelikleri Yönet ve Filtrele'yi**seçin.

    ![Abonelikleri yönetme komutu](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/IC790778.png)

1. Microsoft **Azure Aboneliklerini Yönet** iletişim **kutusunda, Sertifikalar** sekmesini seçin ve ardından **İçe Aktar'ı**seçin.

    ![Azure sertifikalarını alma](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/IC790779.png)

1. Microsoft **Azure Aboneliklerini İçe Aktar** iletişim kutusunda **Gözat'ı**seçin.

    ![Microsoft Azure Aboneliklerini İçe Aktar iletişim kutusundaki gözatma düğmesine göz atın](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/browse-button.png)

1. **Aç** iletişim kutusunda, yayımlama ayarları dosyasını kaydettiğiniz dizine göz atın, dosyayı seçin ve sonra **Aç'ı**seçin.

    ![Yayımlama ayarları dosyasını seçin](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/select-publish-settings-file.png)

1. Microsoft Azure **Abonelikleri İçe Aktar** iletişim kutusuna döndürüldüğünde, **İçe Aktar'ı**seçin.

    ![Yayımlama ayarları dosyasını alma](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/IC790780.png)

    Sertifikalar yayımlama ayarları dosyasından Visual Studio'ya aktarılır ve artık özel bulut kaynaklarınız ile etkileşim kurabilirsiniz.
