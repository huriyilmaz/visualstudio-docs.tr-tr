---
title: Azure bulut hizmeti projesi oluşturma
description: Visual Studio ile bir Azure bulut hizmeti projesi oluşturmak için şimdi öğrenin
author: ghogen
manager: jillfra
assetId: ec580df7-3dcc-45a9-a1d9-8c110678dfb5
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/21/2017
ms.author: ghogen
ms.openlocfilehash: c4daf3d92aa08e6dbbb81eac79112772900d08d8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62964059"
---
# <a name="creating-an-azure-cloud-service-project-with-visual-studio"></a>Visual Studio ile Azure bulut hizmeti projesi oluşturma
Visual Studio için Azure Araçları, basit bir genel amaçlı Azure hizmeti olan [Azure bulut hizmeti](/azure/cloud-services/cloud-services-choose-me)oluşturmanıza olanak sağlayan bir proje şablonu sağlar. Proje oluşturulduktan sonra, Visual Studio bulut hizmetini yapılandırmanıza, hata ayıklamanıza ve Azure 'da dağıtmanıza olanak sağlar.

## <a name="steps-to-create-an-azure-cloud-service-project-in-visual-studio"></a>Visual Studio 'da Azure bulut hizmeti projesi oluşturma adımları
Bu bölümde, bir veya daha fazla web rolü ile Visual Studio 'da bir Azure bulut hizmeti projesi oluşturma işlemi adım adım açıklanmaktadır.

1. Visual Studio'yu yönetici olarak başlatın.

1. Ana menüde **Dosya**  >  **Yeni**  >  **Proje**' yi seçin.

1. Visual C# veya Visual Basic proje şablonu düğümlerinde **bulut** ' u seçin ve şablonlar listesinden **Azure Cloud Service** ' i seçin.

    ![Yeni Azure bulut hizmeti](./media/vs-azure-tools-azure-project-create/new-project-wizard-for-cloud-service.png)

1. Projenizi geliştirmek için kullanmak istediğiniz .NET Framework sürümünü belirtin.

1. Projeniz için bir ad ve konum ve çözüm için bir ad girin.

1. **Tamam**’ı seçin.

1. **Yeni Microsoft Azure bulut hizmeti** iletişim kutusunda eklemek istediğiniz rolleri seçin ve sağ ok düğmesini seçerek bunları çözümünüze ekleyin.

    ![Yeni Azure bulut hizmeti rolleri seçin](./media/vs-azure-tools-azure-project-create/new-cloud-service.png)

1. Eklediğiniz bir rolü yeniden adlandırmak için, **yeni Microsoft Azure bulut hizmeti** iletişim kutusundaki rol üzerine gelin ve bağlam menüsünden **Yeniden Adlandır**' ı seçin. Ayrıca, çözümünüzde bir rolü ( **Çözüm Gezgini**) eklendikten sonra yeniden adlandırabilirsiniz.

    ![Azure bulut hizmeti rolünü yeniden adlandır](./media/vs-azure-tools-azure-project-create/new-cloud-service-rename.png)

Visual Studio Azure projesinde, çözümdeki rol projeleriyle ilişkiler vardır. Proje ayrıca *hizmet tanım dosyasını* ve *hizmet yapılandırma dosyasını*da içerir:

- **Hizmet tanımı dosyası** -uygulamanız için gereken rollerin, uç noktaların ve sanal makine boyutunun dahil olduğu çalışma zamanı ayarlarını tanımlar.
- **Hizmet yapılandırma dosyası** -bir rolün kaç örneğinin çalıştırılacağını ve bir rol için tanımlanan ayarların değerlerini yapılandırır.

Bu dosyalar hakkında daha fazla bilgi için bkz. [Visual Studio Ile Azure bulut hizmeti Için rolleri yapılandırma](vs-azure-tools-configure-roles-for-cloud-service.md).

## <a name="next-steps"></a>Sonraki adımlar
- [Visual Studio ile Azure bulut hizmeti projelerinde rolleri yönetme](./vs-azure-tools-cloud-service-project-managing-roles.md)
