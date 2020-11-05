---
title: Azure bulut hizmeti için sabit sanal IP 'yi koruma
description: Azure bulut hizmetinizin sanal IP adresinin (VIP) değişmemesini nasıl sağlayacağınızı öğrenin.
ms.custom: SEO-VS-2020
author: ghogen
manager: jillfra
assetId: 4a58e2c6-7a79-4051-8a2c-99182ff8b881
ms.workload: azure-vs
ms.topic: how-to
ms.date: 03/21/2017
ms.author: ghogen
ms.openlocfilehash: 95d6a695c31dc62bbe12c2e7aec217aeac8403d8
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93399845"
---
# <a name="retain-a-constant-virtual-ip-address-for-an-azure-cloud-service"></a>Azure bulut hizmeti için sabit bir sanal IP adresi tutma
Azure 'da barındırılan bir bulut hizmetini güncelleştirdiğinizde hizmetin sanal IP adresinin (VIP) değişmediğinden emin olmanız gerekebilir. Birçok etki alanı yönetim hizmeti, etki alanı adlarını kaydetmek için etki alanı adı sistemi 'ni (DNS) kullanır. DNS yalnızca VIP aynı kalırsa kullanılabilir. Azure Araçları 'nda **Yayımla sihirbazını** kullanarak, bulut hizmetinizin VIP 'sini güncelleştirdiğinizde değişiklik yapmaz. Bulut hizmetleri için DNS etki alanı yönetimini kullanma hakkında daha fazla bilgi için bkz. [Azure bulut hizmeti için özel etki alanı adı yapılandırma](/azure/cloud-services/cloud-services-custom-domain-name-portal).

## <a name="publish-a-cloud-service-without-changing-its-vip"></a>VIP 'yi değiştirmeden bir bulut hizmeti yayımlama
Bulut hizmetinin VIP 'si, üretim ortamı gibi belirli bir ortamda Azure 'a ilk kez dağıttığınızda ayrılır. VIP yalnızca dağıtımı açıkça sildiğinizde veya dağıtım, dağıtım güncelleştirme işlemi tarafından örtük olarak silinirse değişir. VIP 'yi sürdürmek için dağıtımınızı silmeniz ve Visual Studio 'Nun dağıtımınızı otomatik olarak silmediğinden emin olmanız gerekir.

Dağıtım ayarlarını, çeşitli dağıtım seçeneklerini destekleyen **Yayımla sihirbazında** belirtebilirsiniz. Artımlı veya eşzamanlı olabilen yeni bir dağıtım veya bir güncelleştirme dağıtımı belirtebilirsiniz. Her iki tür güncelleştirme dağıtımı VIP 'yi korurlar. Bu farklı dağıtım türlerinin tanımları için bkz. [Azure Uygulama Yayımlama Sihirbazı](vs-azure-tools-publish-azure-application-wizard.md). Ayrıca bir hata oluşursa, bir bulut hizmetinin önceki dağıtımının silinip silinmediğini kontrol edebilirsiniz. Bu seçeneği doğru ayarlamazsanız, VIP beklenmedik şekilde değişebilir.

## <a name="update-a-cloud-service-without-changing-its-vip"></a>VIP 'yi değiştirmeden bir bulut hizmetini güncelleştirme
1. Visual Studio 'da bir Azure bulut hizmeti projesi oluşturun veya açın.

2. **Çözüm Gezgini** , projeye sağ tıklayın. Kısayol menüsünde **Yayımla** ' yı seçin.

    ![Yayımlama menüsü](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/solution-explorer-publish-menu.png)

3. **Azure uygulaması Yayımla** iletişim kutusunda, dağıtmak istediğiniz Azure aboneliğini seçin. Gerekirse oturum açın ve **İleri** ' yi seçin.

    ![Azure uygulama oturum açma sayfasını yayımlama](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/azure-publish-signin.png)

4. **Ortak ayarlar** sekmesinde, dağıttığınız bulut hizmeti adının, **ortam** , **Derleme yapılandırması** ve **hizmet yapılandırmasının** tümünün doğru olduğundan emin olun.

    ![Azure uygulaması ortak ayarlarını yayımlama sekmesi](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/azure-publish-common-settings.png)

5. **Gelişmiş ayarlar** sekmesinde, **dağıtım etiketinin** ve **depolama hesabının** doğru olduğundan emin olun. **Hata durumunda dağıtımı Sil** onay kutusunun işaretli olduğunu doğrulayın ve **dağıtım güncelleştirmesi** onay kutusunun seçili olduğunu doğrulayın. **Hata durumunda dağıtımı Sil** onay kutusunun işaretini kaldırarak, dağıtım sırasında bir hata oluşursa VIP 'nizin kaybolmamasını sağlayabilirsiniz. **Dağıtım güncelleştirmesi** onay kutusunu seçerek dağıtımınızın silinmediğini ve uygulamanızı YENIDEN yayımladığınızda VIP 'nizin kaybolmamasını sağlayabilirsiniz.

    ![Azure uygulama gelişmiş ayarları sekmesini yayımlama](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/azure-publish-advanced-settings.png)

6. Rollerin nasıl güncelleştirilmesini istediğinizi daha fazla belirtmek için, **dağıtım güncelleştirmesi** ' nin yanındaki **Ayarlar** ' ı seçin. **Artımlı güncelleştirme** veya **eşzamanlı güncelleştirme** seçeneklerinden birini belirleyin ve **Tamam** ' ı seçin. Uygulamanızın her zaman kullanılabilir olması için her bir örneğini bir diğeri sonra güncelleştirmek üzere **artımlı güncelleştirme** ' yi seçin. Aynı anda uygulamanızın tüm örneklerini güncelleştirmek için **eşzamanlı güncelleştirme** ' yi seçin. Eşzamanlı güncelleştirme daha hızlıdır, ancak güncelleştirme işlemi sırasında hizmetiniz kullanılamayabilir. İşiniz bittiğinde **İleri** ' yi seçin.

    ![Azure uygulama dağıtım ayarlarını yayımlama sayfası](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/azure-publish-deployment-update-settings.png)

7. **Azure uygulaması Yayımla** Iletişim kutusunda **Özet** sayfası görüntülenene kadar **İleri** ' yi seçin. Ayarlarınızı doğrulayın ve ardından **Yayımla** ' yı seçin.

    ![Azure Uygulama Özeti sayfasını Yayımla](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/azure-publish-summary.png)

## <a name="next-steps"></a>Sonraki adımlar
- [Visual Studio Azure Uygulamasını Yayımlama Sihirbazı'nı kullanma](vs-azure-tools-publish-azure-application-wizard.md)
