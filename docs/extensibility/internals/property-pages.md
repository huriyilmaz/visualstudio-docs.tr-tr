---
title: Özellik Sayfaları | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- configuration options, changing properties
- property pages
- property pages, changing configuration options
ms.assetid: b9b3e6e8-1e30-4c89-9862-330265dcf38c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ac788f51bcdc52cd39469a272909890333c5016b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706053"
---
# <a name="property-pages"></a>Özellik Sayfaları
Kullanıcılar özellik sayfalarını kullanarak proje yapılandırmaya bağlı ve bağımsız özellikleri görüntüleyebilir ve değiştirebilir. **Özellikler** penceresinde veya seçili nesnenin özellik sayfası görünümünü sağlayan nesneler için Çözüm Gezgini araç çubuğunda **Özellik Sayfaları** düğmesi etkinleştirilir. Özellik sayfaları çevre tarafından oluşturulur ve çözümler ve projeler için kullanılabilir. Ancak, yapılandırmaya bağımlı özelliklerden yararlanan proje öğeleri için de kullanılabilir hale getirilebilirler. Bu özellik, proje içindeki dosyaların düzgün oluşturmak için farklı derleyici anahtarı ayarları gerektirdiğinde kullanılabilir.

## <a name="using-property-pages"></a>Özellik Sayfalarını Kullanma
 Bir özellik sayfası zaten görüntüleniyorsa ve seçim değişiyorsa (örneğin, çözümden projeye), sayfalarda görüntülenen bilgiler yeni seçimin özelliklerini görüntülemek için değişir. Nesnede özellik sayfalarını destekleyen özellikler yoksa, özellik sayfası boştur.

 Birden çok nesne seçilirse, özellik sayfası seçili tüm öğelerin özelliklerinin kesişimini görüntüler. Seçili öğe yapılandırmaya bağımlı özellikler içermiyorsa ve Çözüm Gezgini araç çubuğundaki **Özellik Sayfaları** düğmesi tıklanırsa, Özellikler penceresinde değişiklikler eleştirilir. Özellikler penceresi ve seçimiyle ilgili daha fazla bilgi için [bkz.](../../extensibility/internals/extending-properties.md)

 Özellikler birden çok nesne için görüntülenirse ve bir özellik sayfasındaki değeri değiştirirseniz, başlangıçta farklı olsalar bile nesnelerin tüm değerleri yeni değere ayarlanır ve tek bir nesnenin özellikleri görüntülendiğinde sayfa boştur.

 **ProjectProperty Sayfaları** iletişim kutularının [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]iki genel türü vardır. Örneğin, Visual Basic projeleri için ilk olarak, özellik sayfaları aşağıdaki ekran görüntüsünde gösterildiği gibi bir alan biçimi kullanılarak görüntülenir. Bu bölümde daha sonra gösterilen ikinci bölümde, özellik sayfası Özellikler Penceresinde bulunana benzer bir özellik ızgarası barındırabilir.

 ![Visual Basic Özellik Sayfaları](../../extensibility/internals/media/vsvbproppages.gif "vsVBPropPages") Alan biçimi ve ağaç yapısına sahip Project Property Pages iletişim kutusu

 Özellik Sayfaları iletişim kutusundaki ağaç yapısı kullanılarak <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>oluşturulmadı. Ortam, seviye adı ve <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages> <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage> arayüzleri tarafından geçirilen dayalı, oluşturur.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Özellik sayfalarında yalnızca iki üst düzey kategori vardır:

- Seçili nesne veya nesneler için yapılandırmadan bağımsız bilgileri görüntüleyen Ortak Özellikler. Sonuç olarak, Ortak Özellikler alt kategorilerinden biri seçildiğinde, iletişim kutusunun üst kısmındaki Yapılandırma, Platform ve Configuration Manager seçenekleri kullanılamaz.

- Hata Ayıklama, Optimizasyon ve Çözüm veya proje için Yapı parametreleri ile ilgili yapılandırmaya bağımlı bilgiler içeren Yapılandırma Özellikleri.

  Herhangi bir ek üst düzey kategori oluşturamazsınız, ancak uygulamanızda birini veya `IVsPropertyPage`diğerini görüntülememeyi seçebilirsiniz. Örneğin, bir nesne için görüntülenecek yapılandırmadan bağımsız özellikleriniz yoksa, Ortak Özellikler kategorisini görüntülememeyi seçebilirsiniz. Yapılandırma nesnesinde `ISpecifyPropertyPages` (nesne yi `ISpecifyPropertyPages` `IVsCfg` `IVsProjectCfg`uygulayan nesne ve ilgili arabirimler) uyguladığınızda öğenin göz atma nesnesinden ve Yapılandırma özelliklerinden uygulanıyorsa Ortak özellikleri görüntülersiniz.

  Üst düzey bir kategori altında görüntülenen her kategori ayrı bir özellik sayfasını temsil eder. İletişim kutusunda bulunan kategori `ISpecifyPropertyPages` ve alt kategori girişleri, uygulamanıza göre belirlenir ve `IVsPropertyPage`.

  `IDispatch`özellik sayfalarında görüntülenecek özelliklere sahip seçim kapsayıcısındaki öğelerin nesneleri sınıf ii'lerinin listesini listelemek için uygulanır. `ISpecifyPropertyPages` Sınıf işlleri, `ISpecifyPropertyPages` katılım sayfalarına değiştirilen değişken olarak geçirilir ve özellik sayfalarını ani bir şada getirmek için kullanılır. Sınıf işleri listesi de `IVsPropertyPage` iletişim kutusunun solundaki ağak yapısını oluşummak için geçirilir. Özellik sayfaları daha sonra bilgileri, her `IDispatch` `ISpecifyPropertyPages` sayfanın bilgilerini uygulayan ve dolduran nesneye geri aktarır.

  Gözatma nesnesinin özellikleri seçim kapsayıcısındaki her nesne için kullanılarak `IDispatch` alınır.

  VSPackage'ınızda uygulama, `Help::DisplayTopicFromF1Keyword` Yardım düğmesi için işlevsellik sağlar.

  Daha fazla bilgi `IDispatch` `ISpecifyPropertyPages`için, bkz ve MSDN kitaplığında.

  Örneklerde görüntülenen ikinci özellik sayfaları türü, aşağıdaki ekran görüntüsünde gösterildiği gibi özellikler ızgarasının bir biçimini barındırar.

  ![VC Özellik Sayfaları](../../extensibility/internals/media/vsvcproppages.gif "vsVCPropPages") Özellik ızgaralı Özellik Sayfaları iletişim kutusu

  Arabirimler `IVSMDPropertyBrowser` ve `IVSMDPropertyGrid` (vsmanaged.h olarak bildirilen) bir iletişim kutusu veya pencere içinde özellikleri ızgara oluşturmak ve doldurmak için kullanılır.

  Projelerin mimarisi, önceki sürümlerden önemli [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ölçüde değişti. Özellikle, hangi projenin etkin olduğu fikri değişmiştir. Burada [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]etkin bir proje kavramı yoktur. Önceki geliştirme ortamlarında, etkin proje, bağlamne bakılmaksızın komutlar oluşturan ve dağıtacağı projeydi. Şimdi, komutları oluşturan ve dağıtan çözüm denetimleri ve tahkim oranları hangi projelere uygulanır.

  Daha önce etkin bir proje olan proje şimdi üç farklı şekilde yakalanır:

- Başlangıç projesi

   Kullanıcı F5 tuşuna bastığında veya Yapı menüsünden Çalıştır'ı seçtiğinde başlatılacak çözümün özellik sayfasından bir proje veya proje belirtebilirsiniz. Bu, adının Çözüm Gezgini'nde kalın yazı tipiyle görüntülenmesi anlamında eski etkin projeye benzer bir şekilde çalışır.

   Otomasyon modelinde başlangıç projesini özellik olarak alabilirsiniz. `DTE.Solution.SolutionBuild.StartupProjects` VSPackage'da, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> yöntemleri <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> veya yöntemleri çağırırsınız. `IVsSolutionBuildManager``QueryService` SID_SVsSolutionBuildManager'da servis olarak kullanılabilir. Daha fazla bilgi için [Bkz. Proje Yapılandırma Nesnesi](../../extensibility/internals/project-configuration-object.md) ve [Çözüm Yapılandırması.](../../extensibility/internals/solution-configuration.md)

- Etkin çözüm oluşturma yapılandırması

   [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]etkin bir çözüm yapılandırması vardır, uygulayarak `DTE.Solution.SolutionBuild.ActiveConfiguration`otomasyon modelinde kullanılabilir. Çözüm yapılandırması, çözümdeki her proje için bir proje yapılandırması içeren bir koleksiyondur (her projenin birden çok yapılandırması, birden çok platformda farklı adlara sahip olabilir). Çözümün özellik sayfaları yla ilgili daha fazla bilgi için [Bkz. Çözüm Yapılandırması.](../../extensibility/internals/solution-configuration.md)

- Şu anda seçili proje

   Proje <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCurrentSelection%2A> hiyerarşisi ve proje öğesi veya seçili öğeleri almak için yöntemi uygulayın. DTE itibaren, `SelectedItems.SelectedItem.Project` ve `SelectedItems.SelectedItem.ProjectItem` yöntemleri kullanmak istiyorsunuz. Temel [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] belgelerde bu başlıklar altında örnek kod vardır.

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage>
- [Yapılandırma Seçeneklerini Yönetme](../../extensibility/internals/managing-configuration-options.md)
- [Proje Yapılandırması Nesnesi](../../extensibility/internals/project-configuration-object.md)
- [Çözüm Yapılandırması](../../extensibility/internals/solution-configuration.md)
