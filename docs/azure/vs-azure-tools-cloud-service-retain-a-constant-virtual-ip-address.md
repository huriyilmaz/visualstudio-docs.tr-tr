---
title: Azure bulut hizmeti için sabit sanal IP'yi koruma
description: Azure bulut hizmetinizin sanal IP adresinin (VIP) değişmey olduğundan emin olun.
ms.custom: SEO-VS-2020
author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.workload: azure-vs
ms.topic: how-to
ms.date: 03/21/2017
ms.author: ghogen
ms.openlocfilehash: b29f7b4380233a510fb34c3e72cf2aac9b948ba1
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633214"
---
# <a name="retain-a-constant-virtual-ip-address-for-an-azure-cloud-service"></a>Azure bulut hizmeti için sabit bir sanal IP adresi tutma
Azure'da barındırılan bir bulut hizmetini güncelleştirin, hizmetin sanal IP adresinin (VIP) değişmey olduğundan emin olun. Birçok etki alanı yönetim hizmeti, etki alanı adlarını kaydetmek için Etki Alanı Adı Sistemi'ni (DNS) kullanır. DNS yalnızca VIP aynı kalırsa çalışır. Bulut hizmetinizin **VIP'sini** güncelleştirinca değişmey olduğundan emin olmak için Azure Araçları'nda Yayımlama Sihirbazı'nı kullanabilirsiniz. Bulut hizmetleri için DNS etki alanı yönetimini kullanma hakkında daha fazla bilgi için bkz. Azure bulut hizmeti [için özel etki alanı adı yapılandırma.](/azure/cloud-services/cloud-services-custom-domain-name-portal)

## <a name="publish-a-cloud-service-without-changing-its-vip"></a>VIP'sini değiştirmeden bulut hizmeti yayımlama
Bir bulut hizmetinin VIP'sini, azure'a üretim ortamı gibi belirli bir ortamda ilk dağıtarak ayrılır. VIP yalnızca dağıtımı açıkça siler veya dağıtım güncelleştirme işlemi tarafından örtülü olarak silinirse değişir. VIP'i korumak için dağıtımınızı silmeniz ve Visual Studio otomatik olarak silmeyebilirsiniz.

Çeşitli dağıtım seçeneklerini destekleyen Yayımlama **Sihirbazı'nda** dağıtım ayarlarını belirtebilirsiniz. Artımlı veya eşzamanlı olarak yeni bir dağıtım veya güncelleştirme dağıtımı belirtebilirsiniz. Her iki güncelleştirme dağıtımı türü de VIP'i korur. Bu farklı dağıtım türlerinin tanımları için bkz. [Azure Uygulama Yayımlama Sihirbazı.](vs-azure-tools-publish-azure-application-wizard.md) Ayrıca, bir hata oluşursa bulut hizmetinin önceki dağıtımının silinip silinip siline olmadığını da kontrol edin. Bu seçeneği doğru ayarlayamasanız VIP beklenmedik şekilde değişebilir.

## <a name="update-a-cloud-service-without-changing-its-vip"></a>VIP'sini değiştirmeden bulut hizmetini güncelleştirme
1. Azure bulut hizmeti projesi oluşturma veya açma Visual Studio.

2. Bu **Çözüm Gezgini** projeye sağ tıklayın. Kısayol menüsünde Yayımla'yı **seçin.**

    ![Yayımlama menüsü](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/solution-explorer-publish-menu.png)

3. Azure **Uygulamasını Yayımla** iletişim kutusunda, dağıtmak istediğiniz Azure aboneliğini seçin. Gerekirse oturum açma ve Sonraki'yi **seçin.**

    ![Azure Uygulama Oturum Açma sayfasını yayımlama](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/azure-publish-signin.png)

4. Common **Ayarlar** sekmesinde, dağıtmakta olduğunu bulut hizmetinin adının, **Ortamın,** Derleme yapılandırmasının ve Hizmet yapılandırmasının **doğru** olduğunu doğrulayın.

    ![Azure Application Common Ayarlar yayımlama sekmesi](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/azure-publish-common-settings.png)

5. Gelişmiş **Ayarlar** sekmesinde Dağıtım **etiketinin ve** Depolama doğru **olduğunu** doğrulayın. Hata durumunda **dağıtımı sil onay kutusunun** temiz olduğunu doğrulayın ve Dağıtım güncelleştirmesi onay **kutusunun** seçili olduğunu doğrulayın. Hata durumunda dağıtımı **sil onay kutusunu** temizleerek, dağıtım sırasında bir hata oluşursa VIP'nizin kaybedilmaması gerekir. Dağıtım güncelleştirmesi **onay kutusunu** seçerek, dağıtımınızı silmeyi ve uygulamayı yeniden yayımlaya kadar VIP'nizin silinmemiş olduğundan emin olun.

    ![Azure Uygulaması Gelişmiş Ayarlar yayımlama sekmesi](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/azure-publish-advanced-settings.png)

6. Rollerin nasıl güncelleştirileceklerini daha fazla belirtmek için Dağıtım **güncelleştirmesi'nin Ayarlar'yi** **seçin.** Artımlı **güncelleştirme veya Eşzamanlı** **güncelleştirme'yi seçin** ve Tamam'ı **seçin.** Uygulamanın **her** zaman kullanılabilir durumda olacak şekilde, uygulamanın her örneğini birbirinin ardından güncelleştirmek için Artımlı güncelleştirme'yi seçin. Aynı **anda tüm** uygulama örneklerini güncelleştirmek için Eşzamanlı güncelleştirme'yi seçin. Eşzamanlı güncelleştirme daha hızlıdır, ancak hizmetiniz güncelleştirme işlemi sırasında kullanılamıyor olabilir. Bitirdikten sonra, Sonraki'yi **seçin.**

    ![Azure Uygulama Dağıtımı Ayarlar yayımlama](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/azure-publish-deployment-update-settings.png)

7. Azure Uygulamasını **Yayımla iletişim** kutusunda Özet sayfası **görüntülenene** kadar **Sonraki'yi** seçin. Ayarlarınızı doğrulayın ve yayımla'yı **seçin.**

    ![Azure Uygulama Özeti sayfasını yayımlama](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/azure-publish-summary.png)

## <a name="next-steps"></a>Sonraki adımlar
- [Visual Studio Azure Uygulamasını Yayımlama Sihirbazı'nı kullanma](vs-azure-tools-publish-azure-application-wizard.md)
