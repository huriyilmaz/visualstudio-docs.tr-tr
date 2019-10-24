---
title: Özellik sayfaları | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- configuration options, changing properties
- property pages
- property pages, changing configuration options
ms.assetid: b9b3e6e8-1e30-4c89-9862-330265dcf38c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 51487b35686da9676f201a157ddb8e47afb75ce8
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72725054"
---
# <a name="property-pages"></a>Özellik Sayfaları
Kullanıcılar, özellik sayfalarını kullanarak proje yapılandırmasına bağımlı ve bağımsız özellikleri görüntüleyebilir ve değiştirebilir. **Özellikler** penceresinde veya seçili nesnenin özellik sayfası görünümünü sağlayan nesneler için Çözüm Gezgini araç çubuğunda **Özellik sayfaları** düğmesi etkinleştirilir. Özellik sayfaları, ortam tarafından oluşturulur ve çözümler ve projeler için kullanılabilir. Bununla birlikte, yapılandırma bağımlı özelliklerden oluşan proje öğeleri için de kullanılabilir hale getirilebilir. Bu özellik bir proje içindeki dosyalar doğru bir şekilde derlemek için farklı derleyici anahtarı ayarları gerektirdiğinde kullanılabilir.

## <a name="using-property-pages"></a>Özellik sayfalarını kullanma
 Bir özellik sayfası zaten görüntüleniyorsa ve seçim değişirse (örneğin, bir çözümden bir projeden), sayfalarda görüntülenen bilgiler yeni seçimin özelliklerini görüntüleyecek şekilde değişir. Nesne üzerinde özellik sayfalarını destekleyen bir özellik yoksa, özellik sayfası boştur.

 Birden çok nesne seçilirse, özellik sayfası seçili tüm öğelerin özelliklerinin kesişimini görüntüler. Seçilen öğe yapılandırmaya bağımlı özellikler içermiyorsa ve Çözüm Gezgini araç çubuğunda **Özellik sayfaları** düğmesine tıklandıysanız, odak, Özellikler penceresi değişir. Özellikler penceresi ve seçimle ilgili daha fazla bilgi için bkz. [özellikleri genişletme](../../extensibility/internals/extending-properties.md).

 Özellikler birden çok nesne için görüntüleniyorsa ve bir özellik sayfasında bir değeri değiştirirseniz, nesneler için tüm değerler, başlangıçta farklı olsalar ve tek bir nesnenin özellikleri görüntülenirken sayfanın boş olması durumunda bile yeni değere ayarlanır.

 @No__t_1 ' de kullanılabilen iki genel tür **ProjectProperty sayfası** iletişim kutusu vardır. İlk olarak, Visual Basic projeleri için, örneğin, aşağıdaki ekran görüntüsünde gösterildiği gibi, özellik sayfaları bir alan biçimi kullanılarak görüntülenir. İkincisi, bu bölümün ilerleyen kısımlarında gösterilen özellik sayfası, Özellikler penceresinde bulunan şuna benzer bir Özellikler Kılavuzu barındırır.

 ![Visual Basic Özellik sayfaları](../../extensibility/internals/media/vsvbproppages.gif "vsVBPropPages") Alan biçimi ve ağaç yapısıyla proje özellik sayfaları iletişim kutusu

 Özellik sayfaları iletişim kutusundaki ağaç yapısı, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> kullanılarak oluşturulmamış. Ortam, <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages> ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage> arabirimleri tarafından kendisine geçirilen düzey adına göre oluşturulur.

 @No__t_0 özellik sayfalarında kullanılabilen yalnızca iki üst düzey kategori vardır:

- Seçili nesne veya nesneler için yapılandırma bağımsız bilgilerini görüntüleyen ortak özellikler. Sonuç olarak, ortak özellikler alt kategorilerinden biri seçildiğinde, iletişim kutusunun üst kısmında yapılandırma, platform ve Configuration Manager seçenekleri kullanılamaz.

- Çözüm veya proje için hata ayıklama, Iyileştirme ve derleme parametreleriyle ilgili yapılandırma bağımlı bilgileri içeren yapılandırma özellikleri.

  Herhangi bir ek üst düzey kategori oluşturamazsınız, ancak `IVsPropertyPage` uygulamanızda bir veya diğerini görüntülememe seçeneğini belirleyebilirsiniz. Örneğin, bir nesne için görüntülenecek yapılandırmadan bağımsız bir özellik yoksa, ortak özellikler kategorisini görüntülememe seçeneğini belirleyebilirsiniz. Yapılandırma nesnesinde `ISpecifyPropertyPages` uyguladığınızda (`IVsCfg`, `IVsProjectCfg` ve ilgili arabirimleri uygulayan nesne) öğenin nesne ve yapılandırma özelliklerinden `ISpecifyPropertyPages` uygulanmışsa ortak özellikleri görüntüleyebilirsiniz.

  Üst düzey kategori altında görünen her kategori ayrı bir özellik sayfasını temsil eder. İletişim kutusunda bulunan kategori ve alt kategori girdileri, `ISpecifyPropertyPages` ve `IVsPropertyPage` uygulamanız tarafından belirlenir.

  seçim kapsayıcısında, özellik sayfalarında görüntülenecek özellikleri olan öğelerin `IDispatch` nesneleri, sınıf kimliklerinin bir listesini numaralandırmak için `ISpecifyPropertyPages` uygular. Sınıf kimlikleri, `ISpecifyPropertyPages` değişken olarak geçirilir ve özellik sayfalarını oluşturmak için kullanılır. Ayrıca, iletişim kutusunun solunda ağaç yapısını oluşturmak için `IVsPropertyPage` sınıf kimliklerinin listesi de geçirilir. Özellik sayfaları daha sonra bilgileri `ISpecifyPropertyPages` uygulayan `IDispatch` nesnesine geri iletir ve her sayfanın bilgisini doldurur.

  Tarama nesnesinin özellikleri, seçim kapsayıcısındaki her bir nesne için `IDispatch` kullanılarak alınır.

  VSPackage içinde `Help::DisplayTopicFromF1Keyword` uygulamak, Yardım düğmesi için işlevsellik sağlar.

  Daha fazla bilgi için bkz. MSDN Kitaplığı `IDispatch` ve `ISpecifyPropertyPages`in.

  Örneklerde gösterilen özellik sayfalarının ikinci türü, aşağıdaki ekran görüntüsünde gösterildiği gibi bir özellikler kılavuzunun bir biçimini barındırır.

  ![VC Özellik sayfaları](../../extensibility/internals/media/vsvcproppages.gif "vsVCPropPages") Özellikler kılavuzundan Özellik sayfaları iletişim kutusu

  @No__t_0 ve `IVSMDPropertyGrid` arabirimleri (vsmanaged. h içinde belirtilen), bir iletişim kutusu veya pencere içinde Özellikler kılavuzunu oluşturmak ve doldurmak için kullanılır.

  Projelerin mimarisi, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] geçmiş sürümlerinden önemli ölçüde değiştirilmiştir. Özellikle, hangi projenin etkin olduğu kavramı değişmiştir. @No__t_0, etkin bir proje kavramı yoktur. Önceki geliştirme ortamlarında etkin proje, oluşturma ve dağıtma komutlarının, bağlamdan bağımsız olarak varsayılan olarak olduğu projgelidir. Artık çözüm, hangi projeler için hangi derleme ve dağıtım komutlarının uygulanacağını denetler ve dağıtır.

  Daha önce etkin bir proje üç farklı yönden birinde yakalanır:

- Başlangıç projesi

   Kullanıcı F5 tuşuna bastığında veya Build menüsünden Çalıştır ' a tıkladığında başlatılacak çözüm özellik sayfasından bir proje veya proje belirtebilirsiniz. Bu, adının kalın yazı tipiyle Çözüm Gezgini gösterildiği gibi, eski etkin projeye benzer şekilde çalışıyor.

   @No__t_0 çağırarak, başlangıç projesini otomasyon modelinde bir özellik olarak alabilirsiniz. VSPackage içinde <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> veya <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> yöntemlerini çağırabilirsiniz. `IVsSolutionBuildManager`, SID_SVsSolutionBuildManager üzerinde `QueryService` tarafından bir hizmet olarak kullanılabilir. Daha fazla bilgi için bkz. [Proje yapılandırma nesnesi](../../extensibility/internals/project-configuration-object.md) ve [çözüm yapılandırması](../../extensibility/internals/solution-configuration.md).

- Etkin çözüm derleme yapılandırması

   [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], `DTE.Solution.SolutionBuild.ActiveConfiguration` uygulayarak otomasyon modelinde kullanılabilen etkin bir çözüm yapılandırmasına sahiptir. Çözüm yapılandırması, çözümdeki her proje için bir proje yapılandırması içeren bir koleksiyondur (her proje birden çok platformda, farklı adlara sahip birden fazla yapılandırmaya sahip olabilir). Çözümün özellik sayfalarıyla ilgili daha fazla bilgi için bkz. [çözüm yapılandırması](../../extensibility/internals/solution-configuration.md).

- Proje şu anda seçili

   Proje hiyerarşisini ve seçili proje öğesi ya da öğeleri almak için <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCurrentSelection%2A> yöntemini uygulayın. DTE 'den `SelectedItems.SelectedItem.Project` ve `SelectedItems.SelectedItem.ProjectItem` yöntemlerini kullanırsınız. Temel [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] belgelerindeki Bu başlıklar altında örnek kod vardır.

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage>
- [Yapılandırma Seçeneklerini Yönetme](../../extensibility/internals/managing-configuration-options.md)
- [Proje Yapılandırması Nesnesi](../../extensibility/internals/project-configuration-object.md)
- [Çözüm Yapılandırması](../../extensibility/internals/solution-configuration.md)