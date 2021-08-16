---
title: Azure bulut hizmeti projesi yapılandırma
description: Bu proje için gereksinimlerinize bağlı olarak azure Visual Studio azure bulut hizmeti projesini yapılandırmayı öğrenin.
author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.workload: azure-vs
ms.topic: how-to
ms.date: 03/06/2017
ms.author: ghogen
ms.openlocfilehash: 72a4f1db0fcd3564dda3b90fe957675e9ed60e099c7ecd56b06b6c07d928e6c9
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121363965"
---
# <a name="configure-an-azure-cloud-service-project-with-visual-studio"></a>Visual Studio ile Azure bulut hizmeti projesini yapılandırma
Bir Azure bulut hizmeti projesini, bu proje için gereksinimlerinize bağlı olarak yapılandırabilirsiniz. Projenin özelliklerini aşağıdaki kategoriler için ayarlayabilirsiniz:

- **Azure'da bulut hizmeti yayımlama** - Azure'a dağıtılan mevcut bir bulut hizmetinin yanlışlıkla silinmey olduğundan emin olmak için bir özellik oluşturabilirsiniz.
- **Yerel bilgisayarda bir bulut hizmetini çalıştırma** veya hata ayıklama - Kullanmak üzere bir hizmet yapılandırması seçin ve Azure hizmet hizmetini başlatmak isteyip Depolama Emulator.
- **Bir bulut hizmeti paketini oluşturulduğunda doğrulama** - Bulut hizmeti paketinin herhangi bir sorun olmadan dağıtılablandırılaması için uyarıları hata olarak ele aabilirsiniz.

## <a name="steps-to-configure-an-azure-cloud-service-project"></a>Azure bulut hizmeti projesini yapılandırma adımları
1. Visual Studio'de bulut hizmeti projesini açma veya oluşturma

1. Bu **Çözüm Gezgini** projesine sağ tıklayın ve bağlam menüsünden Özellikler'i **seçin.**

1. Projenin özellikler sayfasında Geliştirme **sekmesini** seçin.

    ![Project özellikleri menüsü](./media/vs-azure-tools-configuring-an-azure-project/solution-explorer-project-properties-menu.png)

1. Mevcut **bir dağıtımı silmeden önce İstem'i** True olarak **ayarlayın.** Bu ayar, Azure'daki mevcut bir dağıtımı yanlışlıkla silmemenizi sağlar

1. Bulut hizmetinizi **yerel olarak** çalıştırarak veya hata ayıklarken kullanmak istediğiniz hizmet yapılandırmasını belirtmek için istediğiniz Hizmet yapılandırmasını seçin. Bir rol için hizmet yapılandırmasını değiştirme hakkında daha fazla bilgi için bkz. [Azure](./vs-azure-tools-configure-roles-for-cloud-service.md)bulut hizmetinin rollerini Visual Studio.

1. Bulut **hizmetinizi yerel olarak Depolama Emulator** veya **hata** ayıklaması Depolama Emulator Azure hizmetini başlatmak için Azure Depolama Emulator'i True olarak ayarlayın.

1. Paket **doğrulama hataları varsa yayımlanamadık** emin olmak için Uyarıları hata olarak kabul edin'i **True** olarak ayarlayın.

1. Web **rolünüz her yerel olarak** yerel **olarak** başlatıldığında aynı bağlantı noktasını kullandığından emin olmak için Web projesi bağlantı noktalarını kullan'IIS Express.

1. Araç çubuğundan Visual Studio'yi **seçin.**

## <a name="next-steps"></a>Sonraki adımlar
- [Birden çok hizmet yapılandırması kullanarak Bir Azure projesini yapılandırma](vs-azure-tools-multiple-services-project-configurations.md)
