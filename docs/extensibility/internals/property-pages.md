---
title: Özellik sayfaları | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80706053"
---
# <a name="property-pages"></a>Özellik Sayfaları
Kullanıcılar, özellik sayfalarını kullanarak proje yapılandırmasına bağımlı ve bağımsız özellikleri görüntüleyebilir ve değiştirebilir. **Özellikler** penceresinde veya seçili nesnenin özellik sayfası görünümünü sağlayan nesneler için Çözüm Gezgini araç çubuğunda **Özellik sayfaları** düğmesi etkinleştirilir. Özellik sayfaları, ortam tarafından oluşturulur ve çözümler ve projeler için kullanılabilir. Bununla birlikte, yapılandırma bağımlı özelliklerden oluşan proje öğeleri için de kullanılabilir hale getirilebilir. Bu özellik bir proje içindeki dosyalar doğru bir şekilde derlemek için farklı derleyici anahtarı ayarları gerektirdiğinde kullanılabilir.

## <a name="using-property-pages"></a>Özellik sayfalarını kullanma
 Bir özellik sayfası zaten görüntüleniyorsa ve seçim değişirse (örneğin, bir çözümden bir projeden), sayfalarda görüntülenen bilgiler yeni seçimin özelliklerini görüntüleyecek şekilde değişir. Nesne üzerinde özellik sayfalarını destekleyen bir özellik yoksa, özellik sayfası boştur.

 Birden çok nesne seçilirse, özellik sayfası seçili tüm öğelerin özelliklerinin kesişimini görüntüler. Seçilen öğe yapılandırmaya bağımlı özellikler içermiyorsa ve Çözüm Gezgini araç çubuğunda **Özellik sayfaları** düğmesine tıklandıysanız, odak, Özellikler penceresi değişir. Özellikler penceresi ve seçimle ilgili daha fazla bilgi için bkz. [özellikleri genişletme](../../extensibility/internals/extending-properties.md).

 Özellikler birden çok nesne için görüntüleniyorsa ve bir özellik sayfasında bir değeri değiştirirseniz, nesneler için tüm değerler, başlangıçta farklı olsalar ve tek bir nesnenin özellikleri görüntülenirken sayfanın boş olması durumunda bile yeni değere ayarlanır.

 ' De kullanılabilen iki genel tür **ProjectProperty sayfası** iletişim kutusu vardır [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . İlk olarak, Visual Basic projeleri için, örneğin, aşağıdaki ekran görüntüsünde gösterildiği gibi, özellik sayfaları bir alan biçimi kullanılarak görüntülenir. İkincisi, bu bölümün ilerleyen kısımlarında gösterilen özellik sayfası, Özellikler penceresinde bulunan şuna benzer bir Özellikler Kılavuzu barındırır.

 ![Visual Basic Özellik sayfaları](../../extensibility/internals/media/vsvbproppages.gif "vsVBPropPages") Alan biçimi ve ağaç yapısıyla proje özellik sayfaları iletişim kutusu

 Özellik sayfaları iletişim kutusundaki ağaç yapısı kullanılarak oluşturulmamış <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> . Ortam, ve arabirimleri tarafından kendisine geçirilen düzey adına göre <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages> <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage> oluşturulur.

 Özellik sayfalarında kullanılabilen yalnızca iki üst düzey kategori vardır [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] :

- Seçili nesne veya nesneler için yapılandırma bağımsız bilgilerini görüntüleyen ortak özellikler. Sonuç olarak, ortak özellikler alt kategorilerinden biri seçildiğinde, iletişim kutusunun üst kısmında yapılandırma, platform ve Configuration Manager seçenekleri kullanılamaz.

- Çözüm veya proje için hata ayıklama, Iyileştirme ve derleme parametreleriyle ilgili yapılandırma bağımlı bilgileri içeren yapılandırma özellikleri.

  Herhangi bir ek üst düzey kategori oluşturamazsınız, ancak uygulamanızda bir veya diğerini görüntülememe seçeneğini belirleyebilirsiniz `IVsPropertyPage` . Örneğin, bir nesne için görüntülenecek yapılandırmadan bağımsız bir özellik yoksa, ortak özellikler kategorisini görüntülememe seçeneğini belirleyebilirsiniz. `ISpecifyPropertyPages` `ISpecifyPropertyPages` Yapılandırma nesnesinde (uygulama, `IVsCfg` `IVsProjectCfg` ve ilgili arabirimler) uyguladığınızda öğenin nesne ve yapılandırma özelliklerinden uygulanmışsa ortak özellikleri görüntüleyebilirsiniz.

  Üst düzey kategori altında görünen her kategori ayrı bir özellik sayfasını temsil eder. İletişim kutusunda bulunan kategori ve alt kategori girdileri, ve uygulamanız tarafından belirlenir `ISpecifyPropertyPages` `IVsPropertyPage` .

  `IDispatch` özellik sayfalarında görüntülenecek özellikleri olan seçim kapsayıcısındaki öğelerin nesneleri `ISpecifyPropertyPages` , sınıf kimliklerinin bir listesini listelemek için uygular. Sınıf kimlikleri öğesine değişkenler olarak geçirilir `ISpecifyPropertyPages` ve özellik sayfalarını oluşturmak için kullanılır. Ayrıca, `IVsPropertyPage` iletişim kutusunun sol tarafında ağaç yapısını oluşturmak için sınıf kimliklerinin listesi ' ne geçirilir. Özellik sayfaları daha sonra bilgileri öğesini `IDispatch` uygulayan nesneye geri iletir `ISpecifyPropertyPages` ve her sayfanın bilgilerini doldurur.

  Gezinme nesnesinin özellikleri, `IDispatch` seçim kapsayıcısındaki her bir nesne için kullanılarak alınır.

  `Help::DisplayTopicFromF1Keyword`VSPackage uygulamanızda uygulama, Yardım düğmesi için işlevsellik sağlar.

  Daha fazla bilgi için `IDispatch` `ISpecifyPropertyPages` MSDN Kitaplığı 'nda ve bölümüne bakın.

  Örneklerde gösterilen özellik sayfalarının ikinci türü, aşağıdaki ekran görüntüsünde gösterildiği gibi bir özellikler kılavuzunun bir biçimini barındırır.

  ![VC Özellik sayfaları](../../extensibility/internals/media/vsvcproppages.gif "vsVCPropPages") Özellikler kılavuzundan Özellik sayfaları iletişim kutusu

  Arabirimler `IVSMDPropertyBrowser` ve `IVSMDPropertyGrid` (vsmanaged. h içinde belirtilen), Özellikler kılavuzunu bir iletişim kutusu veya pencere içinde oluşturmak ve doldurmak için kullanılır.

  Projelerin mimarisi, eski sürümlerinden önemli ölçüde değiştirilmiştir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Özellikle, hangi projenin etkin olduğu kavramı değişmiştir. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]' De, etkin bir proje kavramı yoktur. Önceki geliştirme ortamlarında etkin proje, oluşturma ve dağıtma komutlarının, bağlamdan bağımsız olarak varsayılan olarak olduğu projgelidir. Artık çözüm, hangi projeler için hangi derleme ve dağıtım komutlarının uygulanacağını denetler ve dağıtır.

  Daha önce etkin bir proje üç farklı yönden birinde yakalanır:

- Başlangıç projesi

   Kullanıcı F5 tuşuna bastığında veya Build menüsünden Çalıştır ' a tıkladığında başlatılacak çözüm özellik sayfasından bir proje veya proje belirtebilirsiniz. Bu, adının kalın yazı tipiyle Çözüm Gezgini gösterildiği gibi, eski etkin projeye benzer şekilde çalışıyor.

   ' İ çağırarak, başlangıç projesini otomasyon modelinde bir özellik olarak elde edebilirsiniz `DTE.Solution.SolutionBuild.StartupProjects` . Bir VSPackage içinde, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> veya <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> yöntemlerini çağırabilirsiniz. `IVsSolutionBuildManager` SID_SVsSolutionBuildManager tarafından bir hizmet olarak kullanılabilir `QueryService` . Daha fazla bilgi için bkz. [Proje yapılandırma nesnesi](../../extensibility/internals/project-configuration-object.md) ve [çözüm yapılandırması](../../extensibility/internals/solution-configuration.md).

- Etkin çözüm derleme yapılandırması

   [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , uygulayarak otomasyon modelinde kullanılabilen etkin bir çözüm yapılandırmasına sahiptir `DTE.Solution.SolutionBuild.ActiveConfiguration` . Çözüm yapılandırması, çözümdeki her proje için bir proje yapılandırması içeren bir koleksiyondur (her proje birden çok platformda, farklı adlara sahip birden fazla yapılandırmaya sahip olabilir). Çözümün özellik sayfalarıyla ilgili daha fazla bilgi için bkz. [çözüm yapılandırması](../../extensibility/internals/solution-configuration.md).

- Proje şu anda seçili

   <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCurrentSelection%2A>Proje hiyerarşisini ve Proje öğesini veya seçili öğeleri almak için yöntemini uygulayın. DTE 'den `SelectedItems.SelectedItem.Project` ve `SelectedItems.SelectedItem.ProjectItem` yöntemlerini kullanabilirsiniz. Temel belgelerde Bu başlıklar altında örnek kod vardır [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage>
- [Yapılandırma Seçeneklerini Yönetme](../../extensibility/internals/managing-configuration-options.md)
- [Proje Yapılandırması Nesnesi](../../extensibility/internals/project-configuration-object.md)
- [Çözüm Yapılandırması](../../extensibility/internals/solution-configuration.md)
