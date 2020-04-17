---
title: Azure bulut hizmeti projesi oluşturma
description: Visual Studio ile bir Azure bulut hizmeti projesi oluşturmayı hemen öğrenin
author: ghogen
manager: jillfra
assetId: ec580df7-3dcc-45a9-a1d9-8c110678dfb5
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/19/2019
ms.author: ghogen
ms.openlocfilehash: 23e2db0b42fb12872feb5942d9f4eeaab96d3c2d
ms.sourcegitcommit: 59a8732dc563242590f7c6ccf4ced6c6d195533c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81489759"
---
# <a name="create-an-azure-cloud-service-project-with-visual-studio"></a>Visual Studio ile Azure bulut hizmeti projesi oluşturması

Visual Studio, basit bir genel amaçlı Azure hizmeti olan bir [Azure bulut hizmeti](/azure/cloud-services/cloud-services-choose-me)oluşturmanıza olanak tanıyan bir proje şablonu sağlar. Proje oluşturulduktan sonra Visual Studio bulut hizmetini Yapılandırmanızı, hata ayıklamanızı ve Azure'a dağıtmanızı sağlar.

## <a name="steps-to-create-an-azure-cloud-service-project-in-visual-studio"></a>Visual Studio'da bir Azure bulut hizmeti projesi oluşturma adımları
Bu bölüm, Visual Studio'da bir veya daha fazla web rolüiçeren bir Azure bulut hizmeti projesi oluşturmanızda size yol sunar.

::: moniker range="vs-2017"
1. Yönetici olarak Visual Studio'u açın.

1. Ana menüde **Yeni** > **Dosya** > **Projesi'ni**seçin.

1. Visual C# veya Visual Basic proje şablon düğümlerinden **Bulut'u** seçin ve şablonlar listesinden **Azure Bulut Hizmeti'ni** seçin.

    ![Yeni Azure bulut hizmeti](./media/vs-azure-tools-azure-project-create/new-project-wizard-for-cloud-service.png)

1. Projenizi geliştirmek için .NET Framework'ün hangi sürümünü kullanmak istediğinizi belirtin.

1. Projeniz için bir ad ve konum ve çözüm için bir ad girin.

1. **Tamam'ı**seçin.
::: moniker-end
::: moniker range=">=vs-2019"
1. Başlangıç penceresinden **yeni bir proje oluştur'u**seçin.

1. Arama kutusuna *Bulut'u*yazın ve ardından **Azure Bulut Hizmeti'ni**seçin.

   ![Yeni Azure bulut hizmeti](./media/vs-azure-tools-azure-project-create/vs-2019/new-project-cloud-service.png)

1. Projeye bir ad verin ve **Oluştur'u**seçin.

   ![Projeye bir ad verin](./media/vs-azure-tools-azure-project-create/vs-2019/new-project-cloud-service-2.png)
::: moniker-end

1. Yeni **Microsoft Azure Bulut Hizmeti** iletişim kutusunda, eklemek istediğiniz rolleri seçin ve çözümünüze eklemek için doğru ok düğmesini seçin.

    ![Yeni Azure bulut hizmeti rolleri seçin](./media/vs-azure-tools-azure-project-create/new-cloud-service.png)

1. Eklediğiniz bir rolü yeniden adlandırmak için, **Yeni Microsoft Azure Bulut Hizmeti** iletişim kutusundaki role odaklanın ve bağlam menüsünden Yeniden **Adlandır'ı**seçin. Ayrıca, eklendikten sonra çözümünüzdeki rolü **(Çözüm Gezgini'nde)** yeniden adlandırabilirsiniz.

    ![Azure bulut hizmeti rolünü yeniden adlandırın](./media/vs-azure-tools-azure-project-create/new-cloud-service-rename.png)

Visual Studio Azure projesi, çözümdeki rol projelerine çağrışımlara sahiptir. Proje ayrıca *hizmet tanımı dosyave* *hizmet yapılandırma dosyası*içerir:

- **Hizmet tanımı dosyası** - Hangi rollerin gerekli olduğu, uç noktaları ve sanal makine boyutu dahil olmak üzere uygulamanızın çalışma zamanı ayarlarını tanımlar.
- **Hizmet yapılandırma dosyası** - Bir rolün kaç örneğinin çalıştırıldığını ve bir rol için tanımlanan ayarların değerlerini yapılandırır.

Bu dosyalar hakkında daha fazla bilgi için Visual [Studio ile Azure bulut hizmetinin Rollerini Yapılandır'a](vs-azure-tools-configure-roles-for-cloud-service.md)bakın.

## <a name="next-steps"></a>Sonraki adımlar
- [Visual Studio ile Azure bulut hizmeti projelerinde rolleri yönetme](./vs-azure-tools-cloud-service-project-managing-roles.md)
