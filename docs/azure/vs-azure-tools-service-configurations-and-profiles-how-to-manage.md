---
title: Hizmet yapılandırma ve profillerini yönetme | Microsoft Docs
description: Hizmet yapılandırmaları ve profilleri yapılandırma dosyalarıyla çalışmayı öğrenin | Dağıtım ortamları ve bulut hizmetleri için yayımlama ayarları için hangi ayarları depolar.
author: ghogen
manager: jillfra
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 8/11/2017
ms.author: ghogen
ms.openlocfilehash: 751214a99c7724c83f01226164202f90425ebf65
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94902089"
---
# <a name="how-to-manage-service-configurations-and-profiles"></a>Hizmet yapılandırmalarını ve profillerini yönetme
## <a name="overview"></a>Genel Bakış
Bir bulut hizmeti yayımladığınızda, Visual Studio yapılandırma bilgilerini iki tür yapılandırma dosyasında depolar: hizmet yapılandırmaları ve profiller. Hizmet yapılandırma (. cscfg dosyaları) bir Azure bulut hizmeti için dağıtım ortamları için depolama ayarları. Azure, bulut hizmetlerinizi yönetirken bu yapılandırma dosyalarını kullanır. Diğer yandan, profiller (. azurePubxml dosyaları), bulut hizmetleri için yayımlama ayarlarını depolar. Bu ayarlar, Yayımlama Sihirbazı 'nı kullanırken seçtiğiniz ayarların bir kaydıdır ve Visual Studio tarafından yerel olarak kullanılır. Bu konu, her iki yapılandırma dosyası türüyle nasıl çalışılacağını açıklamaktadır.

## <a name="service-configurations"></a>Hizmet yapılandırması
Dağıtım ortamlarınızın her biri için kullanmak üzere birden çok hizmet yapılandırması oluşturabilirsiniz. Örneğin, bir Azure uygulamasını ve üretim ortamınız için başka bir hizmet yapılandırmasını çalıştırmak ve test etmek üzere kullandığınız yerel ortam için bir hizmet yapılandırması oluşturabilirsiniz.

Gereksinimlerinize göre bu hizmet yapılandırmasını ekleyebilir, silebilir, yeniden adlandırabilir ve değiştirebilirsiniz. Aşağıdaki çizimde gösterildiği gibi, bu hizmet yapılandırmalarının Visual Studio 'dan yönetebilirsiniz.

![Hizmet yapılandırmasını yönetme](./media/vs-azure-tools-service-configurations-and-profiles-how-to-manage/manage-service-config.png)

Ayrıca rolün özellik sayfalarındaki **konfigürasyonları Yönet** iletişim kutusunu da açabilirsiniz. Azure projenizde bir rolün özelliklerini açmak için, bu rolün kısayol menüsünü açın ve **Özellikler**' i seçin. **Ayarlar** sekmesinde, **hizmet yapılandırması** listesini genişletin ve ardından **Yönet** ' i seçerek **yapılandırmaları Yönet** iletişim kutusunu açın.

### <a name="to-add-a-service-configuration"></a>Hizmet yapılandırması eklemek için
1. Çözüm Gezgini ' de, Azure projesi için kısayol menüsünü açın ve ardından **konfigürasyonları Yönet**' i seçin.

    **Hizmet yapılandırmasını Yönet** iletişim kutusu görüntülenir.
2. Bir hizmet yapılandırması eklemek için, var olan yapılandırmanın bir kopyasını oluşturmanız gerekir. Bunu yapmak için, ad listesinden kopyalamak istediğiniz yapılandırmayı seçin ve ardından **kopya oluştur**' u seçin.
3. Seçim Hizmet yapılandırmasına farklı bir ad vermek için, ad listesinden yeni hizmet yapılandırması ' nı seçin ve ardından **Yeniden Adlandır**' ı seçin. **Ad** metin kutusuna, bu hizmet yapılandırması için kullanmak istediğiniz adı yazın ve ardından **Tamam**' ı seçin.

    ServiceConfiguration adlı yeni bir hizmet yapılandırma dosyası. [New Name]. cscfg Çözüm Gezgini Azure projesine eklenir.

### <a name="to-delete-a-service-configuration"></a>Bir hizmet yapılandırmasını silmek için
1. Çözüm Gezgini ' de, Azure projesi için kısayol menüsünü açın ve ardından **konfigürasyonları Yönet**' i seçin.

    **Hizmet yapılandırmasını Yönet** iletişim kutusu görüntülenir.
2. Bir hizmet yapılandırmasını silmek için, **ad** listesinden silmek istediğiniz yapılandırmayı seçin ve ardından **Kaldır**' ı seçin. Bu yapılandırmayı silmek istediğinizi doğrulayan bir iletişim kutusu görünür.
3. **Sil**’i seçin.

     Hizmet yapılandırma dosyası Çözüm Gezgini Azure projesinden kaldırılır.

### <a name="to-rename-a-service-configuration"></a>Bir hizmet yapılandırmasını yeniden adlandırmak için
1. Çözüm Gezgini ' de Azure projesi için kısayol menüsünü açın ve ardından **konfigürasyonları Yönet**' i seçin.

    **Hizmet yapılandırmasını Yönet** iletişim kutusu görüntülenir.
2. Bir hizmet yapılandırmasını yeniden adlandırmak için, **ad** listesinden yeni hizmet yapılandırması ' nı seçin ve ardından **Yeniden Adlandır**' ı seçin. **Ad** metin kutusuna, bu hizmet yapılandırması için kullanmak istediğiniz adı yazın ve ardından **Tamam**' ı seçin.

    Hizmet yapılandırma dosyasının adı, Azure projesinde Çözüm Gezgini değiştirilir.

### <a name="to-change-a-service-configuration"></a>Bir hizmet yapılandırmasını değiştirmek için
* Bir hizmet yapılandırmasını değiştirmek isterseniz, Azure projesinde değiştirmek istediğiniz belirli rolün kısayol menüsünü açın ve ardından **Özellikler**' i seçin. Daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio Ile Azure bulut hizmeti Için rolleri yapılandırma](vs-azure-tools-configure-roles-for-cloud-service.md) .

## <a name="make-different-setting-combinations-by-using-profiles"></a>Profilleri kullanarak farklı ayar birleşimleri yapın
Bir profil kullanarak, farklı amaçlar için farklı ayarlar birleşimleriyle **Yayımla Sihirbazı** ' nı otomatik olarak doldurabilirsiniz. Örneğin, hata ayıklama için bir profiliniz ve yayın yapıları için bir profil oluşturabilirsiniz. Bu durumda, **hata ayıklama** profilinizde **IntelliTrace** etkin ve **hata ayıklama** yapılandırması seçili olur ve **yayın** profilinizde **IntelliTrace** devre dışı bırakılır ve **Sürüm** yapılandırması seçilidir. Farklı bir depolama hesabı kullanarak bir hizmeti dağıtmak için farklı profiller de kullanabilirsiniz.

Sihirbazı ilk kez çalıştırdığınızda varsayılan bir profil oluşturulur. Visual Studio **profili, profil klasörü altında** Azure projenize eklenen. azurePubXml uzantısına sahip bir dosyada depolar. Sihirbazı daha sonra çalıştırdığınızda farklı seçimleri el ile belirtirseniz dosya otomatik olarak güncelleştirilir. Aşağıdaki yordamı çalıştırmadan önce, zaten bulut hizmetinizi en az bir kez yayımladınız.

### <a name="to-add-a-profile"></a>Bir profil eklemek için
1. Azure projeniz için kısayol menüsünü açın ve ardından **Yayımla**' yı seçin.
2. Aşağıdaki çizimde gösterildiği gibi, **hedef profil** listesinin yanındaki **profili kaydet** düğmesini seçin. Bu, sizin için bir profil oluşturur.

    ![Yeni bir profil oluşturun](./media/vs-azure-tools-service-configurations-and-profiles-how-to-manage/create-new-profile.png)
3. Profil oluşturulduktan sonra **hedef profil** listesinde **<Yönet... >** öğesini seçin.

    Aşağıdaki çizimde gösterildiği gibi **profilleri Yönet** iletişim kutusu görünür.

    ![Profilleri Yönet Iletişim kutusu](./media/vs-azure-tools-service-configurations-and-profiles-how-to-manage/manage-profiles.png)
4. **Ad** listesinde bir profil seçin ve ardından **kopya oluştur**' u seçin.
5. **Kapat** düğmesini seçin.

    Yeni profil, hedef profil listesinde görünür.
6. **Hedef profil** listesinde, az önce oluşturduğunuz profili seçin. Yayımla Sihirbazı ayarları, seçtiğiniz profildeki seçimlerle doldurulur.
7. Yayımla sihirbazının her bir sayfasını göstermek için **önceki** ve **sonraki** düğmeleri seçin ve ardından bu profilin ayarlarını özelleştirin. Bilgi için bkz. [Azure Uygulama Yayımlama Sihirbazı](vs-azure-tools-publish-azure-application-wizard.md) .
8. Ayarları özelleştirmeyi tamamladıktan sonra, ayarlar sayfasına geri dönmek için **İleri** ' yi seçin. Bu ayarları kullanarak hizmeti yayımladığınızda veya profil listesinin yanındaki **Kaydet** ' i seçtiğinizde profil kaydedilir.

### <a name="to-rename-or-delete-a-profile"></a>Bir profili yeniden adlandırmak veya silmek için
1. Azure projeniz için kısayol menüsünü açın ve ardından **Yayımla**' yı seçin.
2. **Hedef profil** listesinde **Yönet**' i seçin.
3. **Profilleri Yönet** iletişim kutusunda, silmek istediğiniz profili seçin ve ardından **Kaldır**' ı seçin.
4. Görüntülenen onay iletişim kutusunda **Tamam**' ı seçin.
5. **Kapat**’ı seçin.

### <a name="to-change-a-profile"></a>Bir profili değiştirmek için
1. Azure projeniz için kısayol menüsünü açın ve ardından **Yayımla**' yı seçin.
2. **Hedef profil** listesinde, değiştirmek istediğiniz profili seçin.
3. Yayımla sihirbazının her bir sayfasını göstermek için **önceki** ve **sonraki** düğmeleri seçin ve ardından istediğiniz ayarları değiştirin. Bilgi için bkz. [Azure Uygulama Yayımlama Sihirbazı](vs-azure-tools-publish-azure-application-wizard.md) .
4. Ayarları değiştirmeyi tamamladıktan sonra **Ayarlar** sayfasına geri dönmek için **İleri** ' yi seçin.
5. (İsteğe bağlı) yeni ayarları kullanarak bulut hizmetini yayımlamak için **Yayımla** ' yı seçin. Bulut hizmetinizi Şu anda yayımlamak istemiyorsanız ve Yayımlama Sihirbazı 'nı kapatırsanız, değişiklikleri profile kaydetmek isteyip istemediğinizi sorar.

## <a name="next-steps"></a>Sonraki adımlar
Visual Studio 'da Azure projenizin diğer bölümlerini yapılandırma hakkında bilgi edinmek için bkz. [Azure projesi yapılandırma](vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address.md).
