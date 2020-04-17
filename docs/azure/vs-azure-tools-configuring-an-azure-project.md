---
title: Azure bulut hizmeti projesi yapılandırma
description: Bu proje için gereksinimlerinize bağlı olarak Visual Studio'da bir Azure bulut hizmeti projesini nasıl yapılandıracaklarınızı öğrenin.
author: ghogen
manager: jillfra
assetId: 609d6965-05cc-47b1-82dc-c76a92d4f295
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/06/2017
ms.author: ghogen
ms.openlocfilehash: 609830b5182ef726a6d1933acecb1ddcbf4e25ef
ms.sourcegitcommit: 59a8732dc563242590f7c6ccf4ced6c6d195533c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81489707"
---
# <a name="configure-an-azure-cloud-service-project-with-visual-studio"></a>Visual Studio ile Azure bulut hizmeti projesini yapılandırma
Bir Azure bulut hizmeti projesini, bu proje için gereksinimlerinize bağlı olarak yapılandırabilirsiniz. Proje özelliklerini aşağıdaki kategoriler için ayarlayabilirsiniz:

- **Azure'da bir bulut hizmeti yayımlama** - Azure'da dağıtılan varolan bir bulut hizmetinin yanlışlıkla silinmediğinden emin olmak için bir özellik ayarlayabilirsiniz.
- **Yerel bilgisayarda bir bulut hizmeti çalıştırın veya hata ayıklama** - Kullanmak üzere bir hizmet yapılandırması seçebilir ve Azure depolama emülatörü başlatmak isteyip istemediğinizbelirtebilirsiniz.
- **Bulut hizmet paketini oluşturulduğunda doğrulayın** - Bulut hizmeti paketinin herhangi bir sorun olmadan dağıldığından emin olmak için herhangi bir uyarıyı hata olarak ele almaya karar verebilirsiniz.

## <a name="steps-to-configure-an-azure-cloud-service-project"></a>Azure bulut hizmeti projesini yapılandırma adımları
1. Visual Studio'da bir bulut hizmeti projesi açma veya oluşturma

1. **Çözüm Gezgini'nde**projeyi sağ tıklatın ve bağlam menüsünden **Özellikler'i**seçin.

1. Projenin özellikleri sayfasında **Geliştirme** sekmesini seçin.

    ![Proje özellikleri menüsü](./media/vs-azure-tools-configuring-an-azure-project/solution-explorer-project-properties-menu.png)

1. Varolan bir dağıtımı **True'ya** **silmeden önce İstem'i** ayarlayın. Bu ayar, Azure'da varolan bir dağıtımı yanlışlıkla silmemenize yardımcı olur

1. Bulut hizmetinizi yerel olarak çalıştırDığınızda veya hata ayıklarken hangi hizmet yapılandırmasını kullanmak istediğinizi belirtmek için istenen **Hizmet yapılandırmasını** seçin. Bir rol için hizmet yapılandırmasını nasıl değiştirebilirsiniz hakkında daha fazla bilgi için Visual [Studio ile bir Azure bulut hizmetinin rollerini nasıl yapılandırılabilirsiniz.](./vs-azure-tools-configure-roles-for-cloud-service.md)

1. Bulut hizmetinizi yerel olarak çalıştırdığınızda veya hata ayıklama yaptığınızda Azure depolama emülatörüne başlamak için **Azure depolama emülatörüne Başlat'ı** **True** olarak ayarlayın.

1. Paket doğrulama hataları varsa yayımlayamayacağınıza emin olmak için Uyarıları **True'ya** **hata olarak** ayarlayın.

1. Web rolünün IIS Express'te yerel olarak her başlatışında aynı bağlantı noktasını kullandığından emin olmak için **web proje bağlantı noktalarını** **True** olarak kullanın.

1. Visual Studio araç çubuğundan **Kaydet'i**seçin.

## <a name="next-steps"></a>Sonraki adımlar
- [Birden çok hizmet yapılandırması kullanarak bir Azure projesini yapılandırma](vs-azure-tools-multiple-services-project-configurations.md)
