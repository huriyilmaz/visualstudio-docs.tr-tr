---
title: Azure bulut hizmeti yayınlama
description: Visual Studio Publish Azure Uygulama Sihirbazı'ndaki çeşitli ayarları nasıl yapılandırılayacağınızı öğrenin
author: ghogen
manager: jillfra
assetId: 7d8f1ac9-e439-47e0-a183-0642c4ea1920
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/21/2017
ms.author: ghogen
ms.openlocfilehash: bc3c58343c699833a5a12eee6f79c023f57a2e85
ms.sourcegitcommit: 59a8732dc563242590f7c6ccf4ced6c6d195533c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81489655"
---
# <a name="using-the-visual-studio-publish-azure-application-wizard"></a>Visual Studio Azure Uygulamasını Yayımlama Sihirbazı'nı kullanma

Visual Studio'da bir web uygulaması geliştirdikten sonra, **Azure Uygulamasını Yayımla** sihirbazını kullanarak bu uygulamayı bir Azure bulut hizmetinde yayımlayabilirsiniz.

> [!Note]
> Bu makale, web sitelerine değil, bulut hizmetlerine dağıtmakla ilgilidir. Web sitelerine dağıtma hakkında bilgi için [Azure Web Sitesi'ni nasıl dağıtılayabilirsiniz'](https://social.msdn.microsoft.com/Search/windowsazure?query=How%20to%20Deploy%20an%20Azure%20Web%20Site&Refinement=138&ac=4#refinementChanges=117&pageNumber=1&showMore=false)e bakın.

## <a name="accessing-the-publish-azure-application-wizard"></a>Azure Uygulamasını Yayımla sihirbazına erişim

Azure Uygulamasını Yayımla sihirbazına, sahip olduğunuz Visual Studio projesinin türüne bağlı olarak iki şekilde erişebilirsiniz.

**Azure bulut hizmeti projeniz varsa:**

1. Visual Studio'da bir Azure bulut hizmeti projesi oluşturun veya açın.

1. **Çözüm Gezgini'nde**projeyi sağ tıklatın ve bağlam menüsünden **Yayımla'yı**seçin.

**Azure için etkinleştirilen bir web uygulama projeniz varsa:**

1. Visual Studio'da bir Azure bulut hizmeti projesi oluşturun veya açın.

1. **Çözüm Gezgini'nde**projeyi sağ tıklatın ve bağlam menüsünden**Azure Bulut Hizmeti Projesi'ne** **Dönüştür'ü** > seçin.

1. **Çözüm Gezgini'nde,** yeni oluşturulan Azure projesine sağ tıklayın ve bağlam menüsünden **Yayımla'yı**seçin.

## <a name="sign-in-page"></a>Oturum açma sayfası

![Oturum açma sayfası](./media/vs-azure-tools-publish-azure-application-wizard/sign-in.png)

**Hesap** - Bir hesap seçin veya hesap açılır listesinde **hesap ekle'yi** seçin.

**Aboneliğinizi seçin** - Dağıtımınız için kullanılacak aboneliği seçin.

## <a name="settings-page---common-settings-tab"></a>Ayarlar sayfası - Ortak Ayarlar sekmesi

![Ortak Ayarlar](./media/vs-azure-tools-publish-azure-application-wizard/settings-common-settings.png)

**Bulut hizmeti** - Açılır açılır hizmeti kullanarak, varolan bir bulut hizmetini seçin veya ** &lt;Yeni>Oluştur'u **seçin ve bir bulut hizmeti oluşturun. Veri merkezi, her bulut hizmeti için parantez içinde görüntülenir. Bulut hizmetinin veri merkezi konumunun depolama hesabının (Gelişmiş Ayarlar) veri merkezi konumuyla aynı olması önerilir.

**Çevre** - **Üretim** veya **Evreleme'yi**seçin. Uygulamanızı bir test ortamında dağıtmak istiyorsanız hazırlama ortamını seçin.

**Yapılandırma oluştur** - **Hata Ayıklama** veya **Sürüm'u**seçin.

**Hizmet yapılandırması** - **Bulut** veya **Yerel'i**seçin.

**Tüm roller için Uzak Masaüstü'nü etkinleştirin** - Hizmete uzaktan bağlanabilmek istiyorsanız bu seçeneği belirleyin. Bu seçenek öncelikle sorun giderme için kullanılır. Daha fazla bilgi için Visual [Studio'u kullanarak Azure Bulut Hizmetlerinde Rol Için Uzak Masaüstü Bağlantısını Etkinleştir'e](/azure/cloud-services/cloud-services-role-enable-remote-desktop-visual-studio)bakın.

**Tüm web rolleri için Web Dağıtımı'nı etkinleştirin** - Hizmet için web dağıtımını etkinleştirmek için bu seçeneği seçin. Bu özelliği kullanmak **için tüm roller için Uzak Masaüstü etkinleştir** seçeneğini de seçmeniz gerekir. Daha fazla bilgi için Visual [Studio'u kullanarak bulut hizmeti yayımlama'ya](vs-azure-tools-publishing-a-cloud-service.md)bakın.

## <a name="settings-page---advanced-settings-tab"></a>Ayarlar sayfası - Gelişmiş Ayarlar sekmesi

![Gelişmiş ayarlar](./media/vs-azure-tools-publish-azure-application-wizard/settings-advanced-settings.png)

**Dağıtım etiketi** - Varsayılan adı kabul edin veya seçtiğiniz bir ad girin. Tarihi dağıtım etiketine eklemek için onay kutusunu seçili bırakın.

**Depolama hesabı** - Bu dağıtım için kullanılacak&lt;depolama hesabını seçin, ** Depolama hesabı oluşturmak için Yeni> oluşturun. Veri merkezi, her depolama hesabı için parantez içinde görüntülenir. Depolama hesabının veri merkezi konumunun bulut hizmetinin veri merkezi konumuyla aynı olması önerilir (Ortak Ayarlar).

Azure depolama hesabı, uygulama dağıtımı için paketi depolar. Uygulama dağıtıldıktan sonra paket depolama hesabından kaldırılır.

**Hata üzerine dağıtımı silme** - Yayımlama sırasında herhangi bir hatayla karşılaşılırsa dağıtımın silinmesi için bu seçeneği belirleyin. Bulut hizmetiniz için sabit bir sanal IP adresi tutmak istiyorsanız, bu işaretlenmemelidir.

**Dağıtım güncelleştirmesi** - Yalnızca güncelleştirilmiş bileşenleri dağıtmak istiyorsanız bu seçeneği belirleyin. Bu tür bir dağıtım tam dağıtımdan daha hızlı olabilir. Bulut hizmetiniz için sabit bir sanal IP adresi tutmak istiyorsanız, bu durum kontrol edilmelidir.

**Dağıtım güncelleştirmesi - ayarlar** - Bu iletişim kutusu, rollerin nasıl güncelleştirilmesini istediğinizi daha fazla belirtmek için kullanılır. **Artımlı güncelleştirmeyi**seçerseniz, uygulamanızın her örneği birbiri ardına güncelleştirilir, böylece uygulama her zaman kullanılabilir olur. **Eşzamanlı güncelleştirmeyi**seçerseniz, uygulamanızın tüm örnekleri aynı anda güncelleştirilir. Aynı anda güncelleştirme daha hızlıdır, ancak güncelleştirme işlemi sırasında hizmetiniz kullanılamayabilir.

![Dağıtım ayarları](./media/vs-azure-tools-publish-azure-application-wizard/deployment-settings.png)

**IntelliTrace'i etkinleştir** - IntelliTrace'i etkinleştirmek isteyip istemediğinizi belirtin. IntelliTrace ile, Azure'da çalıştığında bir rol örneği için kapsamlı hata ayıklama bilgilerini günlüğe kaydedebilirsiniz. Bir sorunun nedenini bulmanız gerekiyorsa, Visual Studio'dan kodunuzu Azure'da çalışıyormuş gibi geçmek için IntelliTrace günlüklerini kullanabilirsiniz. IntelliTrace'i kullanma hakkında daha fazla bilgi için Visual [Studio ve IntelliTrace ile yayınlanan bir Azure bulut hizmetini hata ayıklama](./vs-azure-tools-intellitrace-debug-published-cloud-services.md)bölümüne bakın.

**Profil oluşturmayı etkinleştir** - Performans profil oluşturmayı etkinleştirmek isteyip istemediğinibelirtin. Visual Studio profilleyicisi, bulut hizmetinizin nasıl çalıştığına ait hesaplama yönlerini derinlemesine analiz etmenizi sağlar. Visual Studio profil oluşturucusunu kullanma hakkında daha fazla bilgi [için](./vs-azure-tools-performance-profiling-cloud-services.md)bkz.

**Tüm roller için Uzaktan Hata Ayıklama'yı etkinleştirin** - Uzaktan hata ayıklamayı etkinleştirmek isteyip istemediğinizi belirtin. Visual Studio'u kullanarak bulut hizmetlerinin hata ayıklama hakkında daha fazla bilgi için [Visual Studio'da bir Azure bulut hizmetini veya sanal makineyi hata ayıklama](./vs-azure-tools-debug-cloud-services-virtual-machines.md)bölümüne bakın.

## <a name="diagnostics-settings-page"></a>Tanılama Ayarları sayfası

![Tanılama ayarları](./media/vs-azure-tools-publish-azure-application-wizard/diagnostic-settings.png)

Tanılama, bir Azure bulut hizmetini (veya Azure sanal makinesini) sorun gidermenizi sağlar. Tanılama hakkında bilgi için azure [bulut hizmetleri ve Sanal Makineler için Tanılama](./vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md)Yapılandırma'ya bakın. Uygulama Öngörüleri hakkında bilgi için Bkz. [Uygulama Öngörüleri nedir?](/azure/application-insights/app-insights-overview)

## <a name="summary-page"></a>Özet sayfası

![Özet](./media/vs-azure-tools-publish-azure-application-wizard/summary.png)

**Hedef profil** - Seçtiğiniz ayarlardan bir yayımlama profili oluşturmayı seçebilirsiniz. Örneğin, bir test ortamı için bir profil ve üretim için başka bir profil oluşturabilirsiniz. Bu profili kaydetmek için **Kaydet** simgesini seçin. Sihirbaz profili oluşturur ve Visual Studio projesinde kaydeder. Profil adını değiştirmek için **Hedef profil** listesini açın ve ardından ** &lt;Yönet'i seçin... &gt;**.

   > [!Note]
   > Yayımlama profili Visual Studio'da Solution Explorer'da görünür ve profil ayarları .azurePubxml uzantılı bir dosyaya yazılır. Ayarlar XML etiketleri öznitelikleri olarak kaydedilir.

## <a name="publishing-your-application"></a>Uygulamanızı yayımlama

Projenizin dağıtımı için tüm ayarları yapılandırdıktan sonra iletişim kutusunun altındaki **Yayımla'yı** seçin. Visual Studio'daki **Çıkış** penceresinde işlem durumunu izleyebilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

- [Visual Studio'dan bir Web Uygulamasını Azure bulut hizmetine geçirin ve yayımlayın](./vs-azure-tools-migrate-publish-web-app-to-cloud-service.md)

- [Azure bulut hizmeti yayınlamak için Visual Studio'yı nasıl kullanacağınızı öğrenin](./vs-azure-tools-publishing-a-cloud-service.md)

- [Visual Studio ve IntelliTrace ile yayımlanan bir Azure bulut hizmetinin hatalarını ayıklama](./vs-azure-tools-intellitrace-debug-published-cloud-services.md)

- [Azure bulut hizmetinin performansını test edin](./vs-azure-tools-performance-profiling-cloud-services.md)

- [Azure Bulut Hizmetleri ve Sanal Makineler için Tanılama](./vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md)yapılandırma.

- [Application Insights nedir?](/azure/application-insights/app-insights-overview)