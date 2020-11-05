---
title: Azure bulut hizmeti yayımlama
description: Visual Studio Azure Uygulama Yayımlama Sihirbazı 'ndaki çeşitli ayarları nasıl yapılandıracağınızı öğrenin
author: ghogen
manager: jillfra
assetId: 7d8f1ac9-e439-47e0-a183-0642c4ea1920
ms.workload: azure-vs
ms.topic: how-to
ms.date: 03/21/2017
ms.author: ghogen
ms.openlocfilehash: 281547356dcb8910af9426a853ceeb7e757b195d
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93399462"
---
# <a name="using-the-visual-studio-publish-azure-application-wizard"></a>Visual Studio Azure Uygulamasını Yayımlama Sihirbazı'nı kullanma

Visual Studio 'da bir Web uygulaması geliştirdikten sonra, **Azure uygulaması yayımlama** Sihirbazı 'nı kullanarak bu uygulamayı bir Azure bulut hizmetinde yayımlayabilirsiniz.

> [!Note]
> Bu makale, Web sitelerine değil, bulut hizmetlerine dağıtım ile ilgilidir. Web sitelerine dağıtma hakkında daha fazla bilgi için bkz. [Azure Web sitesi dağıtma](https://social.msdn.microsoft.com/Search/windowsazure?query=How%20to%20Deploy%20an%20Azure%20Web%20Site&Refinement=138&ac=4#refinementChanges=117&pageNumber=1&showMore=false).

## <a name="accessing-the-publish-azure-application-wizard"></a>Azure uygulama yayımlama sihirbazına erişme

Azure uygulaması Yayımlama Sihirbazı 'na, sahip olduğunuz Visual Studio projesinin türüne bağlı olarak iki şekilde erişebilirsiniz.

**Bir Azure bulut hizmeti projeniz varsa:**

1. Visual Studio 'da bir Azure bulut hizmeti projesi oluşturun veya açın.

1. **Çözüm Gezgini** , projeye sağ tıklayın ve bağlam menüsünden **Yayımla** ' yı seçin.

**Azure için etkinleştirilmemiş bir Web uygulaması projeniz varsa:**

1. Visual Studio 'da bir Azure bulut hizmeti projesi oluşturun veya açın.

1. **Çözüm Gezgini** , projeye sağ tıklayın ve bağlam menüsünde, **Convert**  >  **Dönüştür Azure bulut hizmeti projesine** Dönüştür ' ü seçin.

1. **Çözüm Gezgini** , yeni oluşturulan Azure projesine sağ tıklayın ve bağlam menüsünden **Yayımla** ' yı seçin.

## <a name="sign-in-page"></a>Oturum açma sayfası

![Oturum açma sayfası](./media/vs-azure-tools-publish-azure-application-wizard/sign-in.png)

**Hesap** -hesap açılır listesinden bir hesap seçin veya hesap **Ekle** ' yi seçin.

**Aboneliğinizi seçin** -dağıtımınız için kullanılacak aboneliği seçin.

## <a name="settings-page---common-settings-tab"></a>Ayarlar sayfası-ortak ayarlar sekmesi

![Ortak ayarlar](./media/vs-azure-tools-publish-azure-application-wizard/settings-common-settings.png)

**Bulut hizmeti** -açılan menüyü kullanarak var olan bir bulut hizmetini seçin ya da **&lt; Yeni>oluştur** ' u seçin ve bir bulut hizmeti oluşturun. Veri merkezi her bir bulut hizmeti için parantez içinde görüntülenir. Bulut hizmeti için veri merkezi konumunun, depolama hesabı için veri merkezi konumuyla aynı olması önerilir (Gelişmiş ayarlar).

**Ortam** - **Üretim** veya **hazırlama** seçeneklerinden birini belirleyin. Uygulamanızı bir test ortamında dağıtmak istiyorsanız, hazırlama ortamını seçin.

**Derleme yapılandırması** - **Hata Ayıkla** veya **Yayınla** ' yı seçin.

**Hizmet yapılandırması** - **bulut** ya da **Yerel** ' i seçin.

**Tüm roller Için uzak masaüstünü etkinleştir** -hizmete uzaktan bağlanabiliyor olmanız için bu seçeneği belirleyin. Bu seçenek, birincil olarak sorun giderme için kullanılır. Daha fazla bilgi için bkz. [Visual Studio kullanarak Azure Cloud Services bir rol için Uzak Masaüstü bağlantısı etkinleştirme](/azure/cloud-services/cloud-services-role-enable-remote-desktop-visual-studio).

**Tüm Web rolleri için Web dağıtımı etkinleştir** -hizmetin Web dağıtımını etkinleştirmek için bu seçeneği belirleyin. Bu özelliği kullanmak için, **tüm roller Için uzak masaüstünü etkinleştir** seçeneğini de seçmeniz gerekir. Daha fazla bilgi için bkz. [Visual Studio kullanarak bulut hizmeti yayımlama](vs-azure-tools-publishing-a-cloud-service.md).

## <a name="settings-page---advanced-settings-tab"></a>Ayarlar sayfası-Gelişmiş ayarlar sekmesi

![Gelişmiş ayarlar](./media/vs-azure-tools-publish-azure-application-wizard/settings-advanced-settings.png)

**Dağıtım etiketi** -varsayılan adı kabul edin ya da seçtiğiniz bir adı girin. Dağıtım etiketine tarihi eklemek için onay kutusunu seçili bırakın.

**Depolama hesabı** -bu dağıtım için kullanılacak depolama hesabını seçin, * * &lt; bir depolama hesabı oluşturmak için yeni> oluşturun. Veri merkezi her depolama hesabı için parantez içinde görüntülenir. Depolama hesabı için veri merkezi konumunun, bulut hizmeti için veri merkezi konumuyla aynı olması önerilir (ortak ayarlar).

Azure depolama hesabı, uygulama dağıtımı için paketi depolar. Uygulama dağıtıldıktan sonra, paket depolama hesabından kaldırılır.

**Hatada dağıtımı silme** -yayımlama sırasında herhangi bir hatayla karşılaşıldığında dağıtımın silinmesini sağlamak için bu seçeneği belirleyin. Bulut hizmetiniz için sabit bir sanal IP adresi sürdürmek istiyorsanız bu, işareti kaldırılmış olmalıdır.

**Dağıtım güncelleştirmesi** -yalnızca güncelleştirilmiş bileşenleri dağıtmak istiyorsanız bu seçeneği belirleyin. Bu tür bir dağıtım tam dağıtımdan daha hızlı olabilir. Bulut hizmetiniz için sabit bir sanal IP adresi sürdürmek istiyorsanız bu onay edilmelidir.

**Dağıtım güncelleştirmesi-ayarlar** -bu iletişim kutusu, rollerin nasıl güncelleştirilmesini istediğinizi daha fazla belirtmek için kullanılır. **Artımlı güncelleştirme** ' yi seçerseniz, uygulamanın her bir örneği diğerinden sonra güncelleştirilir, böylece uygulama her zaman kullanılabilir. **Eşzamanlı güncelleştirme** ' yi seçerseniz, uygulamanızın tüm örnekleri aynı anda güncelleştirilir. Eşzamanlı güncelleştirme daha hızlıdır, ancak güncelleştirme işlemi sırasında hizmetiniz kullanılamayabilir.

![Dağıtım ayarları](./media/vs-azure-tools-publish-azure-application-wizard/deployment-settings.png)

**IntelliTrace 'ı etkinleştir** -IntelliTrace 'i etkinleştirmek istiyorsanız belirtin. IntelliTrace ile, Azure 'da çalıştırıldığında bir rol örneği için kapsamlı hata ayıklama bilgilerini günlüğe kaydedebilirsiniz. Bir sorunun nedenini bulmanız gerekiyorsa, Visual Studio 'dan Azure 'da çalışıyor gibi kodunuzda adım adım ilerlemek için IntelliTrace günlüklerini kullanabilirsiniz. IntelliTrace kullanma hakkında daha fazla bilgi için bkz. [Visual Studio ve IntelliTrace ile yayımlanmış bir Azure bulut hizmetinde hata ayıklama](./vs-azure-tools-intellitrace-debug-published-cloud-services.md).

**Profil oluşturmayı etkinleştir** -performans profilini oluşturmayı etkinleştirmek istiyorsanız belirtin. Visual Studio Profiler, bulut hizmetinizin nasıl çalıştığı hakkında ayrıntılı bir analizler almanızı sağlar. Visual Studio Profiler 'ı kullanma hakkında daha fazla bilgi için bkz. [Azure bulut hizmetinin performansını test](./vs-azure-tools-performance-profiling-cloud-services.md)etme.

**Tüm roller Için uzaktan hata ayıklayıcıyı etkinleştir** -uzaktan hata ayıklamayı etkinleştirmek istediğinizi belirtin. Visual Studio kullanarak bulut hizmetlerinde hata ayıklama hakkında daha fazla bilgi için bkz. [Visual Studio 'da bir Azure bulut hizmetinde veya sanal makinede hata ayıklama](./vs-azure-tools-debug-cloud-services-virtual-machines.md).

## <a name="diagnostics-settings-page"></a>Tanılama ayarları sayfası

![Tanılama ayarları](./media/vs-azure-tools-publish-azure-application-wizard/diagnostic-settings.png)

Tanılama, bir Azure bulut hizmetinde (veya Azure sanal makinesinde) sorun gidermenize olanak sağlar. Tanılama hakkında daha fazla bilgi için bkz. [Azure Cloud Services ve sanal makineler Için tanılamayı yapılandırma](./vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md). Application Insights hakkında daha fazla bilgi için bkz. [Application Insights nedir?](/azure/application-insights/app-insights-overview).

## <a name="summary-page"></a>Özet sayfası

![Özet sayfası](./media/vs-azure-tools-publish-azure-application-wizard/summary.png)

**Hedef profil** -seçtiğiniz ayarlardan bir yayımlama profili oluşturmayı tercih edebilirsiniz. Örneğin, bir test ortamı için bir profil ve bir üretim için başka bir profil oluşturabilirsiniz. Bu profili kaydetmek için **Kaydet** simgesini seçin. Sihirbaz profili oluşturur ve Visual Studio projesine kaydeder. Profil adını değiştirmek için, **hedef profil** listesini açın ve ardından **&lt; Yönet... &gt;** öğesini seçin.

   > [!Note]
   > Yayımlama profili, Visual Studio 'da Çözüm Gezgini görüntülenir ve profil ayarları. azurePubxml uzantılı bir dosyaya yazılır. Ayarlar, XML etiketlerinin öznitelikleri olarak kaydedilir.

## <a name="publishing-your-application"></a>Uygulamanızı yayımlama

Projenizin dağıtımı için tüm ayarları yapılandırdıktan sonra, iletişim kutusunun alt kısmında **Yayımla** ' yı seçin. İşlem durumunu Visual Studio 'daki **Çıkış** penceresinde izleyebilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

- [Bir Web uygulamasını Visual Studio 'dan Azure bulut hizmeti 'ne geçirme ve yayımlama](./vs-azure-tools-migrate-publish-web-app-to-cloud-service.md)

- [Azure bulut hizmeti yayımlamak için Visual Studio 'Yu nasıl kullanacağınızı öğrenin](./vs-azure-tools-publishing-a-cloud-service.md)

- [Visual Studio ve IntelliTrace ile yayımlanan bir Azure bulut hizmetinin hatalarını ayıklama](./vs-azure-tools-intellitrace-debug-published-cloud-services.md)

- [Azure bulut hizmetinin performansını test etme](./vs-azure-tools-performance-profiling-cloud-services.md)

- [Azure Cloud Services ve sanal makineler Için tanılamayı yapılandırma](./vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md).

- [Application Insights nedir?](/azure/application-insights/app-insights-overview)