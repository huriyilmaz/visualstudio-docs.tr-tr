---
title: Azure bulut hizmeti projesi oluşturma
description: Visual Studio ile bir Azure bulut hizmeti projesi oluşturmayı öğrenin
author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.workload: azure-vs
ms.topic: how-to
ms.date: 03/19/2019
ms.author: ghogen
ms.openlocfilehash: b5893787a1a5a7569c072d49fddd6902118f6aed
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122082419"
---
# <a name="create-an-azure-cloud-service-project-with-visual-studio"></a>Visual Studio ile Azure bulut hizmeti projesi oluşturması

Visual Studio, basit bir genel amaçlı azure hizmeti olan [azure bulut hizmeti](/azure/cloud-services/cloud-services-choose-me)oluşturmanıza olanak sağlayan bir proje şablonu sağlar. proje oluşturulduktan sonra, Visual Studio bulut hizmetini yapılandırmanıza, hata ayıklamanıza ve Azure 'da dağıtmanıza olanak sağlar.

## <a name="steps-to-create-an-azure-cloud-service-project-in-visual-studio"></a>Visual Studio 'de Azure bulut hizmeti projesi oluşturma adımları
bu bölümde, bir veya daha fazla web rolü ile Visual Studio bir Azure bulut hizmeti projesi oluşturma işlemi adım adım açıklanmaktadır.

::: moniker range="vs-2017"
1. Visual Studio yönetici olarak açın.

1. ana menüde **dosya** > **yeni** > **Project**' yi seçin.

1. Visual C# veya Visual Basic proje şablonu düğümlerinde **bulut** ' u seçin ve şablonlar listesinden **Azure Cloud Service** ' i seçin.

    ![Yeni Azure bulut hizmeti](./media/vs-azure-tools-azure-project-create/new-project-wizard-for-cloud-service.png)

1. projenizi geliştirmek için kullanmak istediğiniz .NET Framework sürümünü belirtin.

1. Projeniz için bir ad ve konum ve çözüm için bir ad girin.

1. **Tamam**’ı seçin.
::: moniker-end
::: moniker range=">=vs-2019"
1. Başlangıç penceresinden **Yeni proje oluştur**' u seçin.

1. Arama kutusuna *Cloud* yazın ve ardından **Azure bulut hizmeti**' ni seçin.

   ![Yeni Azure bulut hizmeti](./media/vs-azure-tools-azure-project-create/vs-2019/new-project-cloud-service.png)

1. Projeye bir ad verin ve **Oluştur**' a tıklayın.

   ![Projeye bir ad verin](./media/vs-azure-tools-azure-project-create/vs-2019/new-project-cloud-service-2.png)
::: moniker-end

1. **yeni Microsoft Azure bulut hizmeti** iletişim kutusunda eklemek istediğiniz rolleri seçin ve sağ ok düğmesini seçerek bunları çözümünüze ekleyin.

    ![Yeni Azure bulut hizmeti rolleri seçin](./media/vs-azure-tools-azure-project-create/new-cloud-service.png)

1. eklediğiniz bir rolü yeniden adlandırmak için, **yeni Microsoft Azure bulut hizmeti** iletişim kutusundaki rol üzerine gelin ve bağlam menüsünden **yeniden adlandır**' ı seçin. Ayrıca, çözümünüzde bir rolü ( **Çözüm Gezgini**) eklendikten sonra yeniden adlandırabilirsiniz.

    ![Azure bulut hizmeti rolünü yeniden adlandır](./media/vs-azure-tools-azure-project-create/new-cloud-service-rename.png)

Visual Studio Azure projesinde, çözümdeki rol projeleriyle ilişkiler vardır. Proje ayrıca *hizmet tanım dosyasını* ve *hizmet yapılandırma dosyasını* da içerir:

- **Hizmet tanımı dosyası** -uygulamanız için gerekli olan, uç noktaların ve sanal makine boyutu dahil olmak üzere çalışma zamanı ayarlarını tanımlar.
- **Hizmet yapılandırma dosyası** -bir rolün kaç örneğinin çalıştırılacağını ve bir rol için tanımlanan ayarların değerlerini yapılandırır.

Bu dosyalar hakkında daha fazla bilgi için bkz. [Visual Studio bir Azure bulut hizmeti Için rolleri yapılandırma](vs-azure-tools-configure-roles-for-cloud-service.md).

## <a name="next-steps"></a>Sonraki adımlar
- [Visual Studio ile Azure bulut hizmeti projelerinde rolleri yönetme](./vs-azure-tools-cloud-service-project-managing-roles.md)
