---
title: Özel Azure bulutlarına erişme
description: Visual Studio kullanarak özel bulut kaynaklarına nasıl erişebileceğinizi öğrenin.
author: ghogen
manager: jillfra
assetId: 9d733c8d-703b-44e7-a210-bb75874c45c8
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/13/2017
ms.author: ghogen
ms.openlocfilehash: ab0b6167a91f6cf6f5aecdcbcfb03bab62b96b6b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62964189"
---
# <a name="accessing-private-azure-clouds-with-visual-studio"></a>Visual Studio ile özel Azure bulutlarına erişme

Varsayılan olarak, Visual Studio Azure bulut REST uç noktalarını destekler. Bu makalede, Visual Studio 'dan özel buluta erişmek ve bunlarla etkileşim kurmak için özel bulutunuzun sertifikasını nasıl kullanacağınızı öğreneceksiniz.

1. Özel bulutun Azure portal, yayımlama ayarları dosyanızı indirin veya bir yayımlama ayarları dosyası için yöneticinize başvurun. (Dosyanın uzantısı vardır `.publishsettings` .)

1. Visual Studio **Sunucu Gezgini**' de **Azure** düğümüne sağ tıklayın ve **abonelikleri Yönet ve filtrele**' yi seçin.

    ![Abonelikleri Yönet komutu](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/IC790778.png)

1. **Microsoft Azure Aboneliklerini Yönet** iletişim kutusunda, **Sertifikalar** sekmesini seçin ve ardından **içeri aktar**' ı seçin.

    ![Azure sertifikalarını içeri aktarma](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/IC790779.png)

1. **Microsoft Azure abonelikleri Içeri aktar** iletişim kutusunda, **Araştır**' ı seçin.

    ![Microsoft Azure abonelikleri Içeri aktarma iletişim kutusunda tarama düğmesi](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/browse-button.png)

1. **Aç** iletişim kutusunda, yayınlama ayarları dosyasını kaydettiğiniz dizine gidin, dosyayı seçin ve **Aç**' ı seçin.

    ![Yayımla-ayarlar dosyasını seçin](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/select-publish-settings-file.png)

1. **Microsoft Azure abonelikleri Içeri aktar** iletişim kutusuna döndürüldüğünde **içeri aktar**' ı seçin.

    ![Yayımlama ayarları dosyasını içeri aktarma](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/IC790780.png)

    Sertifikalar, yayımlama ayarları dosyasından Visual Studio 'ya alınır ve artık özel bulut kaynaklarınızla etkileşime geçebilirsiniz.
