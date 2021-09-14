---
title: Hizmet yapılandırmalarını ve profillerini | Microsoft Docs
description: Hizmet yapılandırmaları ve profil yapılandırma dosyalarıyla çalışma hakkında bilgi | dağıtım ortamlarının ayarlarını depolar ve bulut hizmetleri için yayımlama ayarları.
author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 8/11/2017
ms.author: ghogen
ms.openlocfilehash: d57272582a75ddc183250f0f6978e529263e901c
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633049"
---
# <a name="how-to-manage-service-configurations-and-profiles"></a>Hizmet yapılandırmalarını ve profillerini yönetme
## <a name="overview"></a>Genel Bakış
Bir bulut hizmetini yayımlarken, Visual Studio bilgilerini iki tür yapılandırma dosyası içinde depolar: hizmet yapılandırmaları ve profiller. Hizmet yapılandırmaları (.cscfg dosyaları), Azure bulut hizmeti için dağıtım ortamlarının ayarlarını depolar. Azure, bulut hizmetlerinizi yönetirken bu yapılandırma dosyalarını kullanır. Öte yandan, profiller (.azurePubxml dosyaları) bulut hizmetleri için yayımlama ayarlarını depolar. Bu ayarlar, yayımlama sihirbazını kullanırken seçtiğiniz ayarların bir kaydıdır ve yayımlama sihirbazı tarafından yerel Visual Studio. Bu konu başlığında, her iki yapılandırma dosyası türüyle nasıl çalışabilirsiniz?

## <a name="service-configurations"></a>Hizmet Yapılandırmaları
Dağıtım ortamlarınızı her biri için kullanmak üzere birden çok hizmet yapılandırması oluşturabilirsiniz. Örneğin, bir Azure uygulamasını çalıştırmak ve test etmek için yerel ortam için bir hizmet yapılandırması ve üretim ortamınız için başka bir hizmet yapılandırması oluşturabilirsiniz.

Gereksinimlerinize göre bu hizmet yapılandırmalarını ekleyebilir, silebilir, yeniden adlandırabilirsiniz ve değiştirebilirsiniz. Bu hizmet yapılandırmalarını aşağıdaki çizimde Visual Studio hizmet yapılandırmalarından yönetebilirsiniz.

![Hizmet Yapılandırmalarını Yönetme](./media/vs-azure-tools-service-configurations-and-profiles-how-to-manage/manage-service-config.png)

Rolün özellik **sayfalarından Yapılandırmaları** Yönet iletişim kutusunu da açabilirsiniz. Azure projenize bir rolün özelliklerini açmak için bu rolün kısayol menüsünü açın ve Özellikler'i **seçin.** Yapılandırmalar **Ayarlar,** Hizmet Yapılandırması **listesini genişletin** ve ardından Yönet'i seçerek **Yapılandırmaları Yönet iletişim** kutusunu açın. 

### <a name="to-add-a-service-configuration"></a>Hizmet yapılandırması eklemek için
1. Bu Çözüm Gezgini Azure projesinin kısayol menüsünü açın ve Yapılandırmaları **Yönet'i seçin.**

    Hizmet **Yapılandırmalarını Yönet** iletişim kutusu görüntülenir.
2. Hizmet yapılandırması eklemek için mevcut yapılandırmanın bir kopyasını oluşturmanız gerekir. Bunu yapmak için Ad listesinden kopyalamak istediğiniz yapılandırmayı seçin ve ardından Kopyala **oluştur'a tıklayın.**
3. (İsteğe bağlı) Hizmet yapılandırmasına farklı bir ad vermek için Ad listesinden yeni hizmet yapılandırmasını seçin ve ardından Yeniden Adlandır'ı **seçin.** Ad **metin** kutusuna bu hizmet yapılandırması için kullanmak istediğiniz adı yazın ve tamam'ı **seçin.**

    ServiceConfiguration adlı yeni bir hizmet yapılandırma dosyası. [Yeni Ad].cscfg, Azure projesine Çözüm Gezgini.

### <a name="to-delete-a-service-configuration"></a>Hizmet yapılandırmasını silmek için
1. Bu Çözüm Gezgini Azure projesinin kısayol menüsünü açın ve Yapılandırmaları **Yönet'i seçin.**

    Hizmet **Yapılandırmalarını Yönet** iletişim kutusu görüntülenir.
2. Bir hizmet yapılandırmasını silmek için Ad listesinden silmek istediğiniz **yapılandırmayı** seçin ve ardından Kaldır'ı **seçin.** Bu yapılandırmayı silmek istediğinizden emin olmak için bir iletişim kutusu görüntülenir.
3. **Sil**’i seçin.

     Hizmet yapılandırma dosyası, azure projesinde Çözüm Gezgini.

### <a name="to-rename-a-service-configuration"></a>Hizmet yapılandırmasını yeniden adlandırmak için
1. Bu Çözüm Gezgini Azure projesinin kısayol menüsünü açın ve Yapılandırmaları **Yönet'i seçin.**

    Hizmet **Yapılandırmalarını Yönet** iletişim kutusu görüntülenir.
2. Bir hizmet yapılandırmasını yeniden adlandırmak için Ad listesinden yeni hizmet **yapılandırmasını seçin** ve ardından Yeniden Adlandır'ı **seçin.** Ad **metin** kutusuna bu hizmet yapılandırması için kullanmak istediğiniz adı yazın ve tamam'ı **seçin.**

    Hizmet yapılandırma dosyasının adı, azure projesinde Çözüm Gezgini.

### <a name="to-change-a-service-configuration"></a>Hizmet yapılandırmasını değiştirmek için
* Hizmet yapılandırmasını değiştirmek için Azure projesinde değiştirmek istediğiniz rolün kısayol menüsünü açın ve Özellikler'i **seçin.** Daha [fazla bilgi için bkz. Azure Bulut](vs-azure-tools-configure-roles-for-cloud-service.md) Hizmeti rollerini Visual Studio yapılandırma.

## <a name="make-different-setting-combinations-by-using-profiles"></a>Profilleri kullanarak farklı ayar bileşimleri oluşturma
Bir profil kullanarak, Yayımlama Sihirbazı'nı farklı amaçlarla **farklı** ayar birleşimleriyle otomatik olarak doldurabilirsiniz. Örneğin, hata ayıklama için bir profiliniz ve yayın derlemeleri için başka bir profiliniz olabilir. Bu durumda, **Hata Ayıklama** **profilinizde IntelliTrace**  etkin ve Hata ayıklama  yapılandırması seçili olur ve Yayın **profilinizde IntelliTrace** devre dışı bırakılır ve **Sürüm** yapılandırması seçili olur. Bir hizmeti farklı bir depolama hesabı kullanarak dağıtmak için farklı profiller de kullanabilirsiniz.

Sihirbazı ilk kez çalıştıracak olurken varsayılan bir profil oluşturulur. Visual Studio, Profiller klasörünün altında Azure projenize eklenen .azurePubXml uzantısına sahip bir **dosyada depolar.** Sihirbazı daha sonra çalıştıracaksanız, el ile farklı seçenekler belirtirsiniz, dosya otomatik olarak ler. Aşağıdaki yordamı çalıştırmadan önce bulut hizmetinizi en az bir kez yayımlamış olması gerekir.

### <a name="to-add-a-profile"></a>Profil eklemek için
1. Azure projenizin kısayol menüsünü açın ve Yayımla'yı **seçin.**
2. Hedef profil **listesinin** yanında, aşağıdaki **çizimde gösterildiği** gibi Profili Kaydet düğmesini seçin. Bu işlem sizin için bir profil oluşturur.

    ![Yeni profil oluşturma](./media/vs-azure-tools-service-configurations-and-profiles-how-to-manage/create-new-profile.png)
3. Profil oluşturulduktan sonra Hedef profil **<Yönet...>'yi**  seçin.

    Aşağıdaki **çizimde** gösterildiği gibi Profilleri Yönet iletişim kutusu görüntülenir.

    ![Profilleri Yönet İletişim Kutusu](./media/vs-azure-tools-service-configurations-and-profiles-how-to-manage/manage-profiles.png)
4. Ad **listesinde bir** profil seçin ve ardından Kopyala Oluştur'a **tıklayın.**
5. Kapat **düğmesini** seçin.

    Yeni profil Hedef profil listesinde görünür.
6. Hedef **profil listesinde,** yeni oluşturduğunuz profili seçin. Yayımlama Sihirbazı ayarları, seçtiğiniz profilden gelen seçeneklerle doldurulur.
7. Yayımlama **Sihirbazı'nın** **her** sayfasını görüntülemek için Önceki ve Sonraki düğmelerini seçin ve ardından bu profilin ayarlarını özelleştirin. Bilgi [için bkz. Azure Uygulama Yayımlama](vs-azure-tools-publish-azure-application-wizard.md) Sihirbazı.
8. Ayarları özelleştirmeyi bitirdikten sonra, **Ayarlar** sayfasına geri dönmek için Ayarlar seçin. Profil, hizmeti yayımlarken bu ayarlar kullanılarak kaydedilir veya profil **listesinin** yanındaki Kaydet'i seçmeniz gerekir.

### <a name="to-rename-or-delete-a-profile"></a>Bir profili yeniden adlandırmak veya silmek için
1. Azure projenizin kısayol menüsünü açın ve Yayımla'yı **seçin.**
2. Hedef profil **listesinde Yönet'i** **seçin.**
3. Profilleri **Yönet iletişim kutusunda,** silmek istediğiniz profili seçin ve ardından Kaldır'ı **seçin.**
4. Görüntülenen onay iletişim kutusunda Tamam'ı **seçin.**
5. **Kapat**’ı seçin.

### <a name="to-change-a-profile"></a>Bir profili değiştirmek için
1. Azure projenizin kısayol menüsünü açın ve Yayımla'yı **seçin.**
2. Hedef **profil listesinde,** değiştirmek istediğiniz profili seçin.
3. Yayımlama **Sihirbazı'nın** **her** sayfasını görüntülemek için Önceki ve Sonraki düğmelerini seçin ve ardından istediğiniz ayarları değiştirin. Bilgi [için bkz. Azure Uygulama Yayımlama](vs-azure-tools-publish-azure-application-wizard.md) Sihirbazı.
4. Ayarları değiştirmeyi bitirdikten sonra, yeni **sayfaya** geri dönmek için **Ayarlar** seçin.
5. (İsteğe bağlı) **Yeni ayarları** kullanarak bulut hizmetini yayımlamak için Yayımla'yı seçin. Şu anda bulut hizmetinizi yayımlamak istemiyorsanız ve Yayımlama Sihirbazı'nı kapatırsanız, Visual Studio profilde kaydetmek istediğiniz değişiklikleri sorar.

## <a name="next-steps"></a>Sonraki adımlar
Azure projenizin diğer bölümlerini yapılandırma hakkında daha fazla bilgi edinmek Visual Studio bkz. [Azure Project.](vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address.md)
