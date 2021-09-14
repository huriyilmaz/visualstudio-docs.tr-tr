---
title: Azure bulut hizmeti projesi yapılandırma
description: bu projenin gereksinimlerine bağlı olarak Visual Studio bir Azure bulut hizmeti projesi yapılandırmayı öğrenin.
author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.workload: azure-vs
ms.topic: how-to
ms.date: 03/06/2017
ms.author: ghogen
ms.openlocfilehash: 59b4c08f0dfcc4a8712996f26ee9e4b7fcdb6771
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633177"
---
# <a name="configure-an-azure-cloud-service-project-with-visual-studio"></a>Visual Studio ile Azure bulut hizmeti projesini yapılandırma
Bu projenin gereksinimlerine bağlı olarak bir Azure bulut hizmeti projesi yapılandırabilirsiniz. Projenin özelliklerini aşağıdaki kategoriler için ayarlayabilirsiniz:

- **Azure 'da bir bulut hizmeti yayımlayın** -Azure 'a dağıtılan mevcut bir bulut hizmetinin yanlışlıkla silinmediğinden emin olmak için bir özellik ayarlayabilirsiniz.
- **yerel bilgisayarda bir bulut hizmeti çalıştırın veya hata ayıklayın** . kullanılacak bir hizmet yapılandırması seçebilir ve Azure Depolama Emulator başlatmak isteyip istemediğinizi belirtebilirsiniz.
- **Bir bulut hizmeti paketini doğrulama sırasında doğrulama** -bulut hizmeti paketinin herhangi bir sorun olmadan dağıtımını sağlamak için herhangi bir uyarıyı hata olarak değerlendirmeye karar verebilirsiniz.

## <a name="steps-to-configure-an-azure-cloud-service-project"></a>Azure bulut hizmeti projesini yapılandırma adımları
1. Visual Studio bir bulut hizmeti projesi açın veya oluşturun

1. **Çözüm Gezgini**, projeye sağ tıklayın ve bağlam menüsünden **Özellikler**' i seçin.

1. Projenin Özellikler sayfasında **geliştirme** sekmesini seçin.

    ![Project özellikler menüsü](./media/vs-azure-tools-configuring-an-azure-project/solution-explorer-project-properties-menu.png)

1.  **Mevcut bir dağıtımı doğru bir şekilde silmeden önce sor** ' a ayarlayın. Bu ayar, Azure 'da var olan bir dağıtımı yanlışlıkla silmemenizi sağlamaya yardımcı olur

1. Bulut hizmetinizi yerel olarak çalıştırdığınızda veya hata ayıkladığınızda hangi hizmet yapılandırmasını kullanmak istediğinizi belirtmek için istenen **hizmet yapılandırmasını** seçin. Rol için bir hizmet yapılandırmasını değiştirme hakkında daha fazla bilgi için bkz. [Azure bulut hizmeti rollerini Visual Studio ile yapılandırma](./vs-azure-tools-configure-roles-for-cloud-service.md).

1. bulut hizmetinizi yerel olarak çalıştırdığınızda veya hata ayıkladığınızda, azure Emulator Depolama başlatmak için **azure Depolama Emulator** 'ı **True** olarak ayarlayın.

1. Paket doğrulama hataları varsa **yayımlanmayadığınızdan emin olmak için uyarıları hata olarak değerlendir** ' i **doğru** olarak ayarlayın.

1. Web rolünüzün IIS Express yerel olarak başlatıldığı her seferinde aynı bağlantı noktasını kullandığından emin olmak için **Web projesi bağlantı noktalarını** **doğru** olarak kullan ' a ayarlayın.

1. Visual Studio araç çubuğundan **kaydet**' i seçin.

## <a name="next-steps"></a>Sonraki adımlar
- [Birden çok hizmet yapılandırması kullanarak bir Azure projesi yapılandırma](vs-azure-tools-multiple-services-project-configurations.md)
