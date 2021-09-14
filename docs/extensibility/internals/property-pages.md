---
title: Özellik Sayfaları | Microsoft Docs
description: Kullanıcıların proje özelliklerini görüntülemesine ve değiştirmesine olanak sağlayan Visual Studio SDK'sı ile yeni proje türünüz için Özellikler Sayfaları ile çalışma hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- configuration options, changing properties
- property pages
- property pages, changing configuration options
ms.assetid: b9b3e6e8-1e30-4c89-9862-330265dcf38c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 63660d52f6b5707d4e667da07e5d4ccfa38dae7d
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126636089"
---
# <a name="property-pages"></a>Özellik Sayfaları
Kullanıcılar özellik sayfalarını kullanarak proje yapılandırmasına bağımlı ve bağımsız özellikleri görüntüp değiştirebilir. Özellikler **penceresinde veya** seçili  nesnenin özellik sayfası görünümünü Çözüm Gezgini nesneler için bir özellik sayfaları düğmesi etkinleştirilir. Özellik sayfaları ortam tarafından oluşturulur ve çözümler ve projeler için kullanılabilir. Ancak, yapılandırmaya bağımlı özellikleri kullanan proje öğeleri için de kullanılabilir hale gelirler. Bu özellik, bir proje içindeki dosyaların düzgün bir şekilde derlenmiş olması için farklı derleyici anahtarı ayarları gerektirmesi için kullanılabilir.

## <a name="using-property-pages"></a>Özellik Sayfalarını Kullanma
 Bir özellik sayfası zaten görüntüleniyorsa ve seçim değişirse (örneğin, bir çözümden projeye), sayfalarda görüntülenen bilgiler yeni seçimin özelliklerini görüntülemek için değişir. Nesnede özellik sayfalarını destekleyen bir özellik yoksa özellik sayfası boştur.

 Birden çok nesne seçilirse, özellik sayfasında tüm seçili öğelerin özelliklerinin kesişimi görüntülenir. Seçilen öğe yapılandırmaya bağımlı özelliklere sahip  değilse ve Çözüm Gezgini araç çubuğundaki Özellik Sayfaları düğmesine tıklarsanız odak, Özellikler penceresi. Özellikler ve seçimle ilgili daha Özellikler penceresi için bkz. [Özellikleri Genişletme.](../../extensibility/internals/extending-properties.md)

 Özellikler birden çok nesne için görüntülenirse ve bir özellik sayfasındaki bir değeri değiştirirsanız, nesnelerin tüm değerleri başlangıçta farklı olsalar ve tek bir nesnenin özellikleri görüntülendiğinde sayfa boş olsa bile yeni değere ayarlanır.

 içinde iki genel **tür ProjectProperty Pages** iletişim kutusu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] vardır. İlk olarak, Visual Basic için, örneğin, özellik sayfaları aşağıdaki ekran görüntüsünde gösterildiği gibi bir alan biçimi kullanılarak görüntülenir. Bu bölümün ilerleyen kısımlarında gösterilen ikinci bölümde, özellik sayfası Özellikler Penceresinde bulunana benzer bir özellik kılavuzu barındırmaktadır.

 ![Visual Basic Biçimi ve](../../extensibility/internals/media/vsvbproppages.gif "vsVBPropPages") ağaç Project Özellik Sayfaları iletişim kutusunda Özellik Sayfaları

 Özellik Sayfaları iletişim kutusundaki ağaç yapısı kullanılarak yerleşik <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> değildir. ortam, ve arabirimleri tarafından geçirilen düzey adına <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages> <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage> bağlı olarak onu derlemeye devam eder.

 Özellik sayfalarında yalnızca iki üst düzey kategori [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] vardır:

- Seçilen nesne veya nesneler için yapılandırmadan bağımsız bilgileri görüntüleyen Ortak Özellikler. Sonuç olarak, Ortak Özellikler alt kategorilerinden biri seçildiğinde, iletişim kutusunun üst kısmında Yapılandırma, Platform ve Yapılandırma Yöneticisi seçenekleri kullanılamaz.

- Çözüm veya proje için Hata Ayıklama, İyileştirme ve Derleme parametreleriyle ilgili yapılandırmaya bağımlı bilgileri içeren Yapılandırma Özellikleri.

  Herhangi bir ek üst düzey kategori oluşturamaz, ancak uygulamanıza birini veya diğerini görüntülemeyi `IVsPropertyPage` seçebilirsiniz. Örneğin, bir nesne için görüntülemek istediğiniz yapılandırmadan bağımsız bir özelliği yoksa, Ortak Özellikler kategorisini görüntülemeyebilirsiniz. Öğenin gözatma nesnesinden uygulanırsa Ortak özellikler'i ve yapılandırma nesnesine (, ve ilgili arabirimleri uygulayan nesne) uygulayan Yapılandırma `ISpecifyPropertyPages` `ISpecifyPropertyPages` `IVsCfg` özellikleri'ne `IVsProjectCfg` sahipse görüntülersiniz.

  Üst düzey kategori altında görüntülenen her kategori ayrı bir özellik sayfasını temsil eder. İletişim kutusunda kullanılabilen kategori ve alt kategori girdileri, ve uygulamanıza göre `ISpecifyPropertyPages` `IVsPropertyPage` belirlenir.

  `IDispatch` özellik sayfalarında görüntülenecek özelliklere sahip seçim kapsayıcısı öğelerinin nesneleri, sınıf kimliklerinin `ISpecifyPropertyPages` listesini numaralara eklemeye uygulanır. Sınıf kimlikleri değişkenleri olarak `ISpecifyPropertyPages` geçirildi ve özellik sayfalarının örneğini oluşturma için kullanılır. İletişim kutusunun sol tarafından ağaç yapısını `IVsPropertyPage` oluşturmak için sınıf kimlikleri listesi de geçirildi. Özellik sayfaları daha sonra bilgileri uygulayan ve her sayfanın `IDispatch` `ISpecifyPropertyPages` bilgilerini dolduran nesnesine geri iletir.

  Göz atma nesnesinin özellikleri, seçim `IDispatch` kapsayıcısı içinde her nesne için kullanılarak alınır.

  `Help::DisplayTopicFromF1Keyword`VSPackage uygulama, Yardım düğmesinin işlevselliğini sağlar.

  Daha fazla bilgi için MSDN `IDispatch` `ISpecifyPropertyPages` kitaplığında ve konusuna bakın.

  Örneklerde görüntülenen ikinci özellik sayfası türü, aşağıdaki ekran görüntüsünde gösterildiği gibi özellikler kılavuzu formunu barındırmaktadır.

  ![VC Özellik Sayfaları](../../extensibility/internals/media/vsvcproppages.gif "vsVCPropPages") Özellikler kılavuzu ile Özellik Sayfaları iletişim kutusu

  Ve `IVSMDPropertyBrowser` arabirimleri (vsmanaged.h içinde bildirilen) bir iletişim kutusu veya pencere içinde özellikler kılavuzu oluşturmak `IVSMDPropertyGrid` ve doldurmak için kullanılır.

  Projelerin mimarisi, geçmiş sürümlerinden önemli ölçüde [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] değişmiştir. Özellikle, hangi projenin etkin olduğuyla ilgili bir değişiklik oldu. içinde [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] etkin proje kavramı yoktur. Önceki geliştirme ortamlarında etkin proje, bağlama bakılmaksızın komutlar derleme ve dağıtma projesiydi. Artık çözüm, derleme ve dağıtma komutlarının hangi projeler için geçerli olduğunu kontrol eder ve dağıtır.

  Daha önce etkin olan bir proje şimdi üç farklı şekilde yakalanır:

- Başlangıç projesi

   Kullanıcı F5 tuşuna basıyor veya Derleme menüsünden Çalıştır'ı seçerek çözümün özellik sayfasından başlatacak bir proje veya proje belirtebilirsiniz. Bu, eski etkin projeye benzer şekilde çalışır ve adının kalın yazı tipiyle Çözüm Gezgini şekilde görüntülenir.

   çağrısını kullanarak başlangıç projesini otomasyon modelinde bir özellik olarak `DTE.Solution.SolutionBuild.StartupProjects` edinabilirsiniz. VsPackage'da veya <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> yöntemlerini <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> çağırırsiniz. `IVsSolutionBuildManager` tarafından hizmet olarak kullanılabilir `QueryService` SID_SVsSolutionBuildManager. Daha fazla bilgi için [bkz. Project Nesnesi ve](../../extensibility/internals/project-configuration-object.md) Çözüm [Yapılandırması.](../../extensibility/internals/solution-configuration.md)

- Etkin çözüm derleme yapılandırması

   [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , uygulanarak otomasyon modelinde kullanılabilen etkin bir çözüm yapılandırmasına `DTE.Solution.SolutionBuild.ActiveConfiguration` sahip. Çözüm yapılandırması, çözümde her proje için bir proje yapılandırması içeren bir koleksiyondur (her projenin birden çok platformda, farklı adlarla birden çok yapılandırmaya sahip olabilir). Çözümün özellik sayfalarıyla ilgili daha fazla bilgi için bkz. [Çözüm Yapılandırması.](../../extensibility/internals/solution-configuration.md)

- Project seçili

   Proje <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCurrentSelection%2A> hiyerarşisini ve seçilen proje öğesini veya öğeleri almak için yöntemini uygulama. DTE'den ve yöntemlerini `SelectedItems.SelectedItem.Project` `SelectedItems.SelectedItem.ProjectItem` kullanabilirsiniz. Temel belgelerde bu başlıkların altında örnek kod [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] vardır.

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage>
- [Yapılandırma Seçeneklerini Yönetme](../../extensibility/internals/managing-configuration-options.md)
- [Proje Yapılandırması Nesnesi](../../extensibility/internals/project-configuration-object.md)
- [Çözüm Yapılandırması](../../extensibility/internals/solution-configuration.md)
