---
title: Azure bulut hizmeti için sabit sanal IP 'yi koruma
description: Azure bulut hizmetinizin sanal IP adresinin (VIP) değişmemesini nasıl sağlayacağınızı öğrenin.
ms.custom: SEO-VS-2020
author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.workload: azure-vs
ms.topic: how-to
ms.date: 03/21/2017
ms.author: ghogen
ms.openlocfilehash: b29f7b4380233a510fb34c3e72cf2aac9b948ba1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122091766"
---
# <a name="retain-a-constant-virtual-ip-address-for-an-azure-cloud-service"></a>Azure bulut hizmeti için sabit bir sanal IP adresi tutma
Azure 'da barındırılan bir bulut hizmetini güncelleştirdiğinizde hizmetin sanal IP adresinin (VIP) değişmediğinden emin olmanız gerekebilir. Birçok etki alanı yönetim hizmeti, etki alanı adlarını kaydetmek için etki alanı adı sistemi 'ni (DNS) kullanır. DNS yalnızca VIP aynı kalırsa kullanılabilir. Azure Araçları 'nda **Yayımla sihirbazını** kullanarak, bulut hizmetinizin VIP 'sini güncelleştirdiğinizde değişiklik yapmaz. Bulut hizmetleri için DNS etki alanı yönetimini kullanma hakkında daha fazla bilgi için bkz. [Azure bulut hizmeti için özel etki alanı adı yapılandırma](/azure/cloud-services/cloud-services-custom-domain-name-portal).

## <a name="publish-a-cloud-service-without-changing-its-vip"></a>VIP 'yi değiştirmeden bir bulut hizmeti yayımlama
Bulut hizmetinin VIP 'si, üretim ortamı gibi belirli bir ortamda Azure 'a ilk kez dağıttığınızda ayrılır. VIP yalnızca dağıtımı açıkça sildiğinizde veya dağıtım, dağıtım güncelleştirme işlemi tarafından örtük olarak silinirse değişir. vıp 'yi sürdürmek için dağıtımınızı silmemeniz ve Visual Studio dağıtımınızı otomatik olarak silmediğinden emin olmanız gerekir.

Dağıtım ayarlarını, çeşitli dağıtım seçeneklerini destekleyen **Yayımla sihirbazında** belirtebilirsiniz. Artımlı veya eşzamanlı olabilen yeni bir dağıtım veya bir güncelleştirme dağıtımı belirtebilirsiniz. Her iki tür güncelleştirme dağıtımı VIP 'yi korurlar. Bu farklı dağıtım türlerinin tanımları için bkz. [Azure Uygulama Yayımlama Sihirbazı](vs-azure-tools-publish-azure-application-wizard.md). Ayrıca bir hata oluşursa, bir bulut hizmetinin önceki dağıtımının silinip silinmediğini kontrol edebilirsiniz. Bu seçeneği doğru ayarlamazsanız, VIP beklenmedik şekilde değişebilir.

## <a name="update-a-cloud-service-without-changing-its-vip"></a>VIP 'yi değiştirmeden bir bulut hizmetini güncelleştirme
1. Visual Studio bir Azure bulut hizmeti projesi oluşturun veya açın.

2. **Çözüm Gezgini**, projeye sağ tıklayın. Kısayol menüsünde **Yayımla**' yı seçin.

    ![Yayımlama menüsü](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/solution-explorer-publish-menu.png)

3. **Azure uygulaması Yayımla** iletişim kutusunda, dağıtmak istediğiniz Azure aboneliğini seçin. Gerekirse oturum açın ve **İleri**' yi seçin.

    ![Azure uygulama oturum açma sayfasını yayımlama](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/azure-publish-signin.png)

4. **ortak Ayarlar** sekmesinde, dağıttığınız bulut hizmeti adının, **ortam**, **derleme yapılandırması** ve **hizmet yapılandırmasının** tümünün doğru olduğundan emin olun.

    ![Azure uygulaması ortak Ayarlar sekmesini yayımlama](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/azure-publish-common-settings.png)

5. **gelişmiş Ayarlar** sekmesinde **dağıtım etiketinin** ve **Depolama hesabının** doğru olduğundan emin olun. **Hata durumunda dağıtımı Sil** onay kutusunun işaretli olduğunu doğrulayın ve **dağıtım güncelleştirmesi** onay kutusunun seçili olduğunu doğrulayın. **Hata durumunda dağıtımı Sil** onay kutusunun işaretini kaldırarak, dağıtım sırasında bir hata oluşursa VIP 'nizin kaybolmamasını sağlayabilirsiniz. **Dağıtım güncelleştirmesi** onay kutusunu seçerek dağıtımınızın silinmediğini ve uygulamanızı YENIDEN yayımladığınızda VIP 'nizin kaybolmamasını sağlayabilirsiniz.

    ![Azure uygulaması gelişmiş Ayarlar sekmesini yayımlama](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/azure-publish-advanced-settings.png)

6. rollerin nasıl güncelleştirilmesini istediğinizi daha fazla belirtmek için, **dağıtım güncelleştirmesi**' nin yanındaki **Ayarlar** ' yi seçin. **Artımlı güncelleştirme** veya **eşzamanlı güncelleştirme** seçeneklerinden birini belirleyin ve **Tamam**' ı seçin. Uygulamanızın her zaman kullanılabilir olması için her bir örneğini bir diğeri sonra güncelleştirmek üzere **artımlı güncelleştirme** ' yi seçin. Aynı anda uygulamanızın tüm örneklerini güncelleştirmek için **eşzamanlı güncelleştirme** ' yi seçin. Eşzamanlı güncelleştirme daha hızlıdır, ancak güncelleştirme işlemi sırasında hizmetiniz kullanılamayabilir. İşiniz bittiğinde **İleri**' yi seçin.

    ![Azure uygulama dağıtımını yayımlama Ayarlar sayfası](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/azure-publish-deployment-update-settings.png)

7. **Azure uygulaması Yayımla** Iletişim kutusunda **Özet** sayfası görüntülenene kadar **İleri** ' yi seçin. Ayarlarınızı doğrulayın ve ardından **Yayımla**' yı seçin.

    ![Azure Uygulama Özeti sayfasını Yayımla](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/azure-publish-summary.png)

## <a name="next-steps"></a>Sonraki adımlar
- [Visual Studio Azure Uygulamasını Yayımlama Sihirbazı'nı kullanma](vs-azure-tools-publish-azure-application-wizard.md)
