---
title: Azure bulut hizmeti yayımlama
description: Azure Uygulaması Yayımlama Sihirbazı'nda Visual Studio yapılandırmayı öğrenin
author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.workload: azure-vs
ms.topic: how-to
ms.date: 03/21/2017
ms.author: ghogen
ms.openlocfilehash: 8e1dcaf760eada7d67eaab445361d6aa8c0219de
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633078"
---
# <a name="using-the-visual-studio-publish-azure-application-wizard"></a>Visual Studio Azure Uygulamasını Yayımlama Sihirbazı'nı kullanma

Visual Studio'de bir web uygulaması Visual Studio, Azure Uygulamasını Yayımla sihirbazını kullanarak bu uygulamayı bir **Azure bulut hizmetine yayımlayın.**

> [!Note]
> Bu makale, web sitelerine değil bulut hizmetine dağıtımla ilgilidir. Web sitelerine dağıtma hakkında bilgi için [bkz. Azure Web Sitesi Dağıtma.](https://social.msdn.microsoft.com/Search/windowsazure?query=How%20to%20Deploy%20an%20Azure%20Web%20Site&Refinement=138&ac=4#refinementChanges=117&pageNumber=1&showMore=false)

## <a name="accessing-the-publish-azure-application-wizard"></a>Azure Uygulamasını Yayımla sihirbazına erişme

Azure Uygulamasını Yayımla sihirbazına sahip olduğunuz proje türüne bağlı olarak Visual Studio şekilde erişebilirsiniz.

**Azure bulut hizmeti projeniz varsa:**

1. Azure bulut hizmeti projesi oluşturma veya açma Visual Studio.

1. Bu **Çözüm Gezgini** projesine sağ tıklayın ve bağlam menüsünde Yayımla'yı **seçin.**

**Azure için etkinleştirilmemiş bir web uygulaması projeniz varsa:**

1. Azure bulut hizmeti projesi oluşturma veya açma Visual Studio.

1. Bu **Çözüm Gezgini,** projeye sağ tıklayın ve bağlam menüsünden Dönüştür'den Azure Bulut Hizmetine   >  **Dönüştür'Project.**

1. Bu **Çözüm Gezgini** yeni oluşturulan Azure projesine sağ tıklayın ve bağlam menüsünde Yayımla'yı **seçin.**

## <a name="sign-in-page"></a>Oturum açma sayfası

![Oturum açma sayfası](./media/vs-azure-tools-publish-azure-application-wizard/sign-in.png)

**Hesap** - Hesap seçin veya **hesap açılan listesinde** Hesap ekle'yi seçin.

**Aboneliğinizi seçin** - Dağıtımınız için kullanmak istediğiniz aboneliği seçin.

## <a name="settings-page---common-settings-tab"></a>Ayarlar sayfası - Ortak Ayarlar sekmesi

![Ortak Ayarlar](./media/vs-azure-tools-publish-azure-application-wizard/settings-common-settings.png)

**Bulut hizmeti** - Açılan listeden var olan bir bulut hizmetini seçin veya Yeni Hizmet Oluştur'>ve bir bulut hizmeti oluşturun. **&lt;** Veri merkezi, her bulut hizmeti için parantez içinde görüntülenir. Bulut hizmeti için veri merkezi konumunun depolama hesabı için veri merkezi konumuyla aynı olması önerilir (Gelişmiş Ayarlar).

**Ortam** - **Üretim'i veya** **Hazırlama'yi seçin.** Uygulamanızı bir test ortamında dağıtmak için hazırlama ortamını seçin.

**Derleme yapılandırması** - Hata Ayıkla **veya Yayın'ı** **seçin.**

**Hizmet yapılandırması** - Bulut veya **Yerel'i** **seçin.**

**Tüm roller için Uzak Masaüstü'nü** etkinleştir - Hizmete uzaktan bağlanabiliyorsanız bu seçeneği belirleyin. Bu seçenek öncelikli olarak sorun giderme için kullanılır. Daha fazla bilgi için [bkz. Uzak Masaüstü Bağlantısı kullanarak Azure Cloud Services rolü Visual Studio.](/azure/cloud-services/cloud-services-role-enable-remote-desktop-visual-studio)

**Tüm Web Dağıtımı rollerini etkinleştirme** - Hizmet için web dağıtımını etkinleştirmek için bu seçeneği belirleyin. Bu özelliği kullanmak için **Tüm roller için Uzak Masaüstünü Etkinleştir** seçeneğini de seçmeniz gerekir. Daha fazla bilgi için [bkz. Visual Studio kullanarak bulut hizmeti yayımlama.](vs-azure-tools-publishing-a-cloud-service.md)

## <a name="settings-page---advanced-settings-tab"></a>Ayarlar sayfası - Gelişmiş Ayarlar sekmesi

![Gelişmiş ayarlar](./media/vs-azure-tools-publish-azure-application-wizard/settings-advanced-settings.png)

**Dağıtım etiketi** - Varsayılan adı kabul et veya seçtiğiniz bir ad girin. Tarihi dağıtım etiketine eklemek için onay kutusunu seçili bırakın.

**Depolama -** Bu dağıtım için kullanmak üzere depolama hesabını seçin, ** Yeni &lt;> oluştur'a bir depolama hesabı oluşturun. Veri merkezi, her depolama hesabı için parantez içinde görüntülenir. Depolama hesabının veri merkezi konumunun, bulut hizmeti için veri merkezi konumuyla aynı olması önerilir (Common Ayarlar).

Azure depolama hesabı, uygulama dağıtımı için paketi depolar. Uygulama dağıtıldıktan sonra paket depolama hesabından kaldırılır.

**Hata durumunda dağıtımı sil** - Yayımlama sırasında herhangi bir hatayla karşılaşırsanız dağıtımın silinmesi için bu seçeneği belirleyin. Bulut hizmetiniz için sabit bir sanal IP adresi korumak için bu seçeneğin işaretlenmemiş olması gerekir.

**Dağıtım güncelleştirmesi** - Yalnızca güncelleştirilmiş bileşenleri dağıtmak için bu seçeneği belirleyin. Bu dağıtım türü, tam dağıtımdan daha hızlı olabilir. Bulut hizmetiniz için sabit bir sanal IP adresi korumak istiyorsanız bu denetlenir.

**Dağıtım güncelleştirmesi -** ayarlar - Bu iletişim kutusu rollerin nasıl güncelleştirileceklerini daha fazla belirtmek için kullanılır. Artımlı **güncelleştirme'yi** seçerseniz, uygulamanın her zaman kullanılabilir durumda olacak şekilde, her örneği birbirinin ardından güncelleştirilir. Eşzamanlı **güncelleştirme'yi** seçerseniz, uygulamanın tüm örnekleri aynı anda güncelleştirilir. Eşzamanlı güncelleştirme daha hızlıdır, ancak hizmetiniz güncelleştirme işlemi sırasında kullanılamıyor olabilir.

![Dağıtım ayarları](./media/vs-azure-tools-publish-azure-application-wizard/deployment-settings.png)

**IntelliTrace'i** etkinleştir - IntelliTrace'i etkinleştirmek mi istediğiniz belirtin. IntelliTrace ile, Azure'da çalışan bir rol örneği için kapsamlı hata ayıklama bilgilerini günlüğe görüntüebilirsiniz. Bir sorunun nedenini bulmanız gerekirse IntelliTrace günlüklerini kullanarak azure'da çalışıyor gibi Visual Studio kod adımlarını atabilirsiniz. IntelliTrace kullanma hakkında daha fazla bilgi için bkz. Visual Studio ve [IntelliTrace](./vs-azure-tools-intellitrace-debug-published-cloud-services.md)ile yayımlanmış bir Azure bulut hizmetinde hata ayıklama.

**Profil oluşturmayı etkinleştir** - Performans profili oluşturmayı etkinleştirmek mi istediğinizi belirtin. Visual Studio profili oluşturma, bulut hizmetinizin nasıl çalıştırıcı olduğuyla ilgili hesaplama yönleriyle ilgili ayrıntılı bir analiz elde etmek için size olanak sağlar. Visual Studio profil Visual Studio daha fazla bilgi için bkz. [Azure bulut hizmetinin performansını test edin.](./vs-azure-tools-performance-profiling-cloud-services.md)

**Tüm roller için Uzaktan Hata Ayıklayıcı'ya** etkinleştir - Uzaktan hata ayıklamayı etkinleştirmek mi istediğiniz belirtin. Visual Studio kullanarak bulut hizmetlerde hata ayıklama hakkında daha fazla bilgi için bkz. Azure bulut hizmetinde veya sanal makinede [hata Visual Studio.](./vs-azure-tools-debug-cloud-services-virtual-machines.md)

## <a name="diagnostics-settings-page"></a>Tanılama Ayarlar sayfası

![Tanılama ayarları](./media/vs-azure-tools-publish-azure-application-wizard/diagnostic-settings.png)

Tanılama, bir Azure bulut hizmeti (veya Azure sanal makinesi) ile ilgili sorunları gidermenize olanak sağlar. Tanılama hakkında bilgi için, [bkz. Configuring Diagnostics for Azure Cloud Services and Virtual Machines](./vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md). Application Analizler için [bkz. Application Analizler?](/azure/application-insights/app-insights-overview).

## <a name="summary-page"></a>Özet sayfası

![Özet sayfası](./media/vs-azure-tools-publish-azure-application-wizard/summary.png)

**Hedef profil** - Seçtiğiniz ayarlardan bir yayımlama profili oluşturabilirsiniz. Örneğin, bir test ortamı için bir profil ve üretim için başka bir profil oluşturabilirsiniz. Bu profili kaydetmek için Kaydet **simgesini** seçin. Sihirbaz, profili oluşturur ve Visual Studio kaydeder. Profil adını değiştirmek için Hedef profil **listesini açın ve** **&lt; Yönet... 'i seçin. &gt;**

   > [!Note]
   > Yayımlama profili, Çözüm Gezgini içinde Visual Studio ve profil ayarları .azurePubxml uzantısına sahip bir dosyaya yazılır. Ayarlar XML etiketlerinin öznitelikleri olarak kaydedilir.

## <a name="publishing-your-application"></a>Uygulamanızı yayımlama

Projenizin dağıtımı için tüm ayarları yapılandırdıktan sonra iletişim kutusunun **alt kısmında** Yayımla'yı seçin. İşlem durumunu, aşağıdaki çıkış **penceresindeki** Çıkış penceresinde Visual Studio.

## <a name="next-steps"></a>Sonraki adımlar

- [Web Uygulamasını azure'dan Azure bulut hizmetine geçirme ve yayımlama Visual Studio](./vs-azure-tools-migrate-publish-web-app-to-cloud-service.md)

- [Azure bulut hizmetini Visual Studio için Visual Studio kullanmayı öğrenin](./vs-azure-tools-publishing-a-cloud-service.md)

- [Visual Studio ve IntelliTrace ile yayımlanan bir Azure bulut hizmetinin hatalarını ayıklama](./vs-azure-tools-intellitrace-debug-published-cloud-services.md)

- [Azure bulut hizmetinin performansını test edin](./vs-azure-tools-performance-profiling-cloud-services.md)

- Azure Cloud Services ve [Sanal Makineler için Tanılamayı Yapılandırma.](./vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md)

- [Application Insights nedir?](/azure/application-insights/app-insights-overview)