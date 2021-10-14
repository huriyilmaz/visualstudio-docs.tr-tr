---
title: Azure bulut hizmeti yayımlama
description: Visual Studio Azure uygulaması yayımlama sihirbazı 'nda çeşitli ayarları nasıl yapılandıracağınızı öğrenin
author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.workload: azure-vs
ms.topic: how-to
ms.date: 03/21/2017
ms.author: ghogen
ms.openlocfilehash: 0d58f664117f28439ea6a3d98d77fd5da0ab27ea
ms.sourcegitcommit: 8fae163333e22a673fd119e1d2da8a1ebfe0e51a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "129969105"
---
# <a name="using-the-visual-studio-publish-azure-application-wizard"></a>Visual Studio Azure Uygulamasını Yayımlama Sihirbazı'nı kullanma

Visual Studio ' de bir web uygulaması geliştirdikten sonra, **azure uygulaması yayımlama** sihirbazı 'nı kullanarak bu uygulamayı bir azure bulut hizmetinde yayımlayabilirsiniz.

## <a name="accessing-the-publish-azure-application-wizard"></a>Azure uygulama yayımlama sihirbazına erişme

Azure uygulaması yayımla sihirbazına, sahip olduğunuz Visual Studio projenin türüne bağlı olarak iki şekilde erişebilirsiniz.

**Bir Azure bulut hizmeti projeniz varsa:**

1. Visual Studio bir Azure bulut hizmeti projesi oluşturun veya açın.

1. **Çözüm Gezgini**, projeye sağ tıklayın ve bağlam menüsünden **Yayımla**' yı seçin.

**Azure için etkinleştirilmemiş bir Web uygulaması projeniz varsa:**

1. Visual Studio bir Azure bulut hizmeti projesi oluşturun veya açın.

1. **Çözüm Gezgini**, projeye sağ tıklayın ve bağlam menüsünde, dönüştür ' ü   >  **Azure bulut hizmeti 'ne dönüştür Project**' i seçin.

1. **Çözüm Gezgini**, yeni oluşturulan Azure projesine sağ tıklayın ve bağlam menüsünden **Yayımla**' yı seçin.

## <a name="sign-in-page"></a>Oturum açma sayfası

![Oturum açma sayfası](./media/vs-azure-tools-publish-azure-application-wizard/sign-in.png)

**Hesap** -hesap açılır listesinden bir hesap seçin veya hesap **Ekle** ' yi seçin.

**Aboneliğinizi seçin** -dağıtımınız için kullanılacak aboneliği seçin.

## <a name="settings-page---common-settings-tab"></a>Ayarlar sayfası-ortak Ayarlar sekmesi

![ortak Ayarlar](./media/vs-azure-tools-publish-azure-application-wizard/settings-common-settings.png)

**Bulut hizmeti** -açılan menüyü kullanarak var olan bir bulut hizmetini seçin ya da **&lt; Yeni>oluştur**' u seçin ve bir bulut hizmeti oluşturun. Veri merkezi her bir bulut hizmeti için parantez içinde görüntülenir. bulut hizmeti için veri merkezi konumunun, depolama hesabı için veri merkezi konumuyla aynı olması önerilir (gelişmiş Ayarlar).

**Ortam** - **Üretim** veya **hazırlama** seçeneklerinden birini belirleyin. Uygulamanızı bir test ortamında dağıtmak istiyorsanız, hazırlama ortamını seçin.

**Derleme yapılandırması** - **Hata Ayıkla** veya **Yayınla**' yı seçin.

**Hizmet yapılandırması** - **bulut** ya da **Yerel**' i seçin.

**Tüm roller Için uzak masaüstünü etkinleştir** -hizmete uzaktan bağlanabiliyor olmanız için bu seçeneği belirleyin. Bu seçenek, birincil olarak sorun giderme için kullanılır. Daha fazla bilgi için bkz. [Visual Studio kullanarak Azure Cloud Services bir rol için Uzak Masaüstü bağlantısı etkinleştirme](/azure/cloud-services/cloud-services-role-enable-remote-desktop-visual-studio).

**Tüm Web rolleri için Web dağıtımı etkinleştir** -hizmetin Web dağıtımını etkinleştirmek için bu seçeneği belirleyin. Bu özelliği kullanmak için, **tüm roller Için uzak masaüstünü etkinleştir** seçeneğini de seçmeniz gerekir. Daha fazla bilgi için bkz. [Visual Studio kullanarak bulut hizmeti yayımlama](vs-azure-tools-publishing-a-cloud-service.md).

## <a name="settings-page---advanced-settings-tab"></a>Ayarlar sayfası-gelişmiş Ayarlar sekmesi

![Gelişmiş ayarlar](./media/vs-azure-tools-publish-azure-application-wizard/settings-advanced-settings.png)

**Dağıtım etiketi** -varsayılan adı kabul edin ya da seçtiğiniz bir adı girin. Dağıtım etiketine tarihi eklemek için onay kutusunu seçili bırakın.

**Depolama hesabı** -bu dağıtım için kullanılacak depolama hesabını seçin, * * &lt; bir depolama hesabı oluşturmak için yeni> oluşturun. Veri merkezi her depolama hesabı için parantez içinde görüntülenir. depolama hesabı için veri merkezi konumunun, bulut hizmeti için veri merkezi konumuyla aynı olması önerilir (ortak Ayarlar).

Azure depolama hesabı, uygulama dağıtımı için paketi depolar. Uygulama dağıtıldıktan sonra, paket depolama hesabından kaldırılır.

**Hatada dağıtımı silme** -yayımlama sırasında herhangi bir hatayla karşılaşıldığında dağıtımın silinmesini sağlamak için bu seçeneği belirleyin. Bulut hizmetiniz için sabit bir sanal IP adresi sürdürmek istiyorsanız bu, işareti kaldırılmış olmalıdır.

**Dağıtım güncelleştirmesi** -yalnızca güncelleştirilmiş bileşenleri dağıtmak istiyorsanız bu seçeneği belirleyin. Bu tür bir dağıtım tam dağıtımdan daha hızlı olabilir. Bulut hizmetiniz için sabit bir sanal IP adresi sürdürmek istiyorsanız bu onay edilmelidir.

**Dağıtım güncelleştirmesi-ayarlar** -bu iletişim kutusu, rollerin nasıl güncelleştirilmesini istediğinizi daha fazla belirtmek için kullanılır. **Artımlı güncelleştirme**' yi seçerseniz, uygulamanın her bir örneği diğerinden sonra güncelleştirilir, böylece uygulama her zaman kullanılabilir. **Eşzamanlı güncelleştirme**' yi seçerseniz, uygulamanızın tüm örnekleri aynı anda güncelleştirilir. Eşzamanlı güncelleştirme daha hızlıdır, ancak güncelleştirme işlemi sırasında hizmetiniz kullanılamayabilir.

![Dağıtım ayarları](./media/vs-azure-tools-publish-azure-application-wizard/deployment-settings.png)

**IntelliTrace 'ı etkinleştir** -IntelliTrace 'i etkinleştirmek istiyorsanız belirtin. IntelliTrace ile, Azure 'da çalıştırıldığında bir rol örneği için kapsamlı hata ayıklama bilgilerini günlüğe kaydedebilirsiniz. bir sorunun nedenini bulmanız gerekiyorsa, Azure 'da çalışıyor gibi Visual Studio kodunuzda adım adım ilerlemek için ıntellitrace günlüklerini kullanabilirsiniz. ıntellitrace kullanma hakkında daha fazla bilgi için bkz. [Visual Studio ve ıntellitrace ile yayımlanmış bir Azure bulut hizmetinde hata ayıklama](./vs-azure-tools-intellitrace-debug-published-cloud-services.md).

**Profil oluşturmayı etkinleştir** -performans profilini oluşturmayı etkinleştirmek istiyorsanız belirtin. Visual Studio profiler, bulut hizmetinizin nasıl çalıştığı hakkında ayrıntılı bir analizler almanızı sağlar. Visual Studio profil oluşturucuyu kullanma hakkında daha fazla bilgi için bkz. [Azure bulut hizmetinin performansını Test](./vs-azure-tools-performance-profiling-cloud-services.md)etme.

**Tüm roller Için uzaktan hata ayıklayıcıyı etkinleştir** -uzaktan hata ayıklamayı etkinleştirmek istediğinizi belirtin. Visual Studio kullanarak bulut hizmetlerinde hata ayıklama hakkında daha fazla bilgi için, bkz. [Visual Studio 'de Azure bulut hizmetinde veya sanal makinede hata ayıklama](./vs-azure-tools-debug-cloud-services-virtual-machines.md).

## <a name="diagnostics-settings-page"></a>tanılama Ayarlar sayfası

![Tanılama ayarları](./media/vs-azure-tools-publish-azure-application-wizard/diagnostic-settings.png)

Tanılama, bir Azure bulut hizmetinde (veya Azure sanal makinesinde) sorun gidermenize olanak sağlar. Tanılama hakkında daha fazla bilgi için bkz. [Azure Cloud Services ve sanal makineler Için tanılamayı yapılandırma](./vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md). Application Insights hakkında daha fazla bilgi için bkz. [Application Insights nedir?](/azure/application-insights/app-insights-overview).

## <a name="summary-page"></a>Özet sayfası

![Özet sayfası](./media/vs-azure-tools-publish-azure-application-wizard/summary.png)

**Hedef profil** -seçtiğiniz ayarlardan bir yayımlama profili oluşturmayı tercih edebilirsiniz. Örneğin, bir test ortamı için bir profil ve bir üretim için başka bir profil oluşturabilirsiniz. Bu profili kaydetmek için **Kaydet** simgesini seçin. sihirbaz profili oluşturur ve Visual Studio projesine kaydeder. Profil adını değiştirmek için, **hedef profil** listesini açın ve ardından **&lt; Yönet... &gt;** öğesini seçin.

   > [!Note]
   > yayımlama profili Visual Studio Çözüm Gezgini görüntülenir ve profil ayarları. azurePubxml uzantılı bir dosyaya yazılır. Ayarlar, XML etiketlerinin öznitelikleri olarak kaydedilir.

## <a name="publishing-your-application"></a>Uygulamanızı yayımlama

Projenizin dağıtımı için tüm ayarları yapılandırdıktan sonra, iletişim kutusunun alt kısmında **Yayımla** ' yı seçin. İşlem durumunu, Visual Studio **Çıkış** penceresinde izleyebilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

- [Visual Studio 'ten bir Web uygulamasını bir Azure bulut hizmetine geçirme ve yayımlama](./vs-azure-tools-migrate-publish-web-app-to-cloud-service.md)

- [Azure bulut hizmeti yayımlamak için Visual Studio kullanmayı öğrenin](./vs-azure-tools-publishing-a-cloud-service.md)

- [Visual Studio ve IntelliTrace ile yayımlanan bir Azure bulut hizmetinin hatalarını ayıklama](./vs-azure-tools-intellitrace-debug-published-cloud-services.md)

- [Azure bulut hizmetinin performansını test etme](./vs-azure-tools-performance-profiling-cloud-services.md)

- [Azure Cloud Services ve sanal makineler Için tanılamayı yapılandırma](./vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md).

- [Application Insights nedir?](/azure/application-insights/app-insights-overview)
