---
title: Visual Studio SDK'sı | Microsoft Docs
description: Visual Studio SDK'sı'Visual Studio bileşenleri, hizmetleri, şemaları ve yardımcı programları içeren uzantılar hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- roadmap, Visual Studio integration SDK
- Visual Studio integration SDK roadmap
- integration roadmap, Visual Studio SDK
ms.assetid: 9118eaa4-0453-4dc5-9e16-c7062d254869
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: fc4f300e6da070a150903281c6ff3a623576cf836b5fdd05ecb8c2b366a6ff35
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121376006"
---
# <a name="inside-the-visual-studio-sdk"></a>Visual Studio SDK’nın İçinde

Bu bölümde, Visual Studio mimarisi, bileşenleri, hizmetleri, şemaları, yardımcı programları ve benzerleri dahil olmak üzere Visual Studio uzantıları hakkında ayrıntılı bilgiler sağlar.

## <a name="extensibility-architecture"></a>Genişletilebilirlik Mimarisi
 Aşağıdaki çizimde, Visual Studio mimarisi gösterilmiştir. VSPackage'lar, IDE genelinde hizmet olarak paylaşılan uygulama işlevselliği sağlar. Standart IDE, IDE pencere işlevselliğine erişim sağlayan gibi çok <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> çeşitli hizmetler de sunar.

 ![Ortam Mimarisi grafiği](../../extensibility/internals/media/environment.gif "ortam") Visual Studio mimarisinin genelleştirilmiş görünümü

## <a name="vspackages"></a>VSPackage’lar
 VSPackage'lar kullanıcı arabirimi öğeleri, Visual Studio, projeler, düzenleyiciler ve tasarımcılarla birlikte bu öğeleri toplanmış ve genişleten yazılım modülleridir. VSPackage'lar, mimarinin merkezi Visual Studio. Daha fazla bilgi için bkz. [VSPackages](../../extensibility/internals/vspackages.md).

## <a name="visual-studio-shell"></a>Visual Studio Kabuğu
 Visual Studio kabuğu, temel işlevler sağlar ve bileşeni VSPackage'ları ile MEF uzantıları arasında çapraz iletişimi destekler. Daha fazla bilgi için [bkz. Visual Studio Kabuğu.](../../extensibility/internals/visual-studio-shell.md)

## <a name="user-experience-guidelines"></a>Kullanıcı Deneyimi Yönergeleri
 Visual Studio için yeni özellikler tasarlamayı planlıyorsanız, tasarım ve kullanılabilirlik ipuçları için şu yönergelere göz atabilirsiniz: [Visual Studio Deneyimi Yönergeleri.](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)

## <a name="commands"></a>Komutlar
 Komutlar, bir belge yazdırma, görünümü yenileme veya yeni dosya oluşturma gibi görevleri gerçekleştiren işlevlerdir.

 Uygulamanın Visual Studio, komutları oluşturabilir ve Visual Studio kabuğuna Visual Studio. Bu komutların IDE'de(örneğin, bir menü veya araç çubuğunda) nasıl görüneceklerini belirtebilirsiniz. Genellikle Araçlar menüsünde özel bir **komut** görüntülenir ve görünüm penceresini görüntüleme  komutu Görünüm menüsünün Diğer Windows menüsünde **görünür.**

 Bir komut oluşturdukta bunun için bir olay işleyicisi de oluşturmanız gerekir. Olay işleyicisi komutun ne zaman görünür veya etkin olduğunu belirler, metnini değiştirmenize olanak sağlar ve etkinleştirildiğinde komutun uygun şekilde yanıt vermesini garantiler. Çoğu örnekte IDE, komutları arabirimini kullanarak <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> işlemeye devam ediyor. Komut Visual Studio, yerel seçime bağlı olarak en içteki komut bağlamıyla başlayarak ve genel seçime göre en dıştaki bağlama doğru ilerler. Ana menüye eklenen komutlar betikler için hemen kullanılabilir.

 Daha fazla bilgi için [bkz. Komutlar, Menüler ve Araç Çubukları.](../../extensibility/internals/commands-menus-and-toolbars.md)

## <a name="menus-and-toolbars"></a>Menüler ve Araç Çubukları
 Menüler ve araç çubukları, kullanıcıların komutlarını çağırmalarını sağlar. Menüler, genellikle bir araç penceresinin üst kısmında tek tek metin öğeleri olarak görüntülenen satırlar veya komut sütunlarıdır. Alt menüler, kullanıcı küçük bir ok içeren komutlara tıkladığında görünen ikincil menülerdir. Kullanıcı belirli kullanıcı arabirimi öğelerine sağ tıkladığında bağlam menüleri görüntülenir. Bazı yaygın menü adları **Dosya,** **Düzenle,** **Görüntüle ve** **Pencere'dir.** Daha fazla bilgi için [bkz. Menüleri ve Komutları Genişletme.](../../extensibility/extending-menus-and-commands.md)

 Araç çubukları; düğme satırları veya sütunları ile birleşik giriş kutuları, liste kutuları ve metin kutuları gibi diğer denetimlerdir. Araç çubuğu düğmeleri genellikle Dosya Aç komutu için klasör simgesi veya Yazdır komutu **için** yazıcı gibi simge **görüntüleri** içerir. Tüm araç çubuğu öğeleri komutlarla ilişkilendirildi. Bir araç çubuğu düğmesine tıklarsanız, ilişkili komutu çalışır. Açılan denetim durumunda, açılan listede yer alan her öğe farklı bir komutla ilişkilendirilr. Bölen denetimi gibi bazı araç çubuğu denetimleri karmadır. Denetimin bir tarafı bir araç çubuğu düğmesi, diğeri ise tıkıldığında birkaç komutu görüntüleyen aşağı ok işaretidir.

## <a name="tool-windows"></a>Araç Pencereleri
 Araç pencereleri, bilgileri görüntülemek için IDE'de kullanılır. **Araç kutusu,** **Çözüm Gezgini,** **Özellikler** penceresi ve **Web Tarayıcısı araç** pencerelerinin örnekleridir.

 Araç pencereleri genellikle kullanıcının etkileşimde buluna çeşitli denetimler sağlar. Örneğin, Özellikler **penceresi** kullanıcının belirli bir amaca hizmet eden nesnelerin özelliklerini ayarlamaya olanak sağlar. Özellikler  penceresi bu anlamda özeldir, ancak birçok farklı durumda kullanılaa da geneldir. Benzer şekilde, **Çıkış** penceresi metin tabanlı çıkış sağladığı için özeldir, ancak Visual Studio'daki birçok alt sistem, kullanıcıya çıkış sağlamak için Visual Studio kullanabilir.

 Çeşitli araç pencereleri içeren Visual Studio aşağıdaki resmi düşünün:

 ![Ekran görüntü](../../extensibility/internals/media/t1gui.png "T1gui")

 Araç pencerelerinin bazıları, araç penceresini görüntüleyen ve diğer araç pencerelerini gizle Çözüm Gezgini sekmelere tıklayarak bunları kullanılabilir yapan tek bir bölmede bir araya bulunur. Resimde, tek bir bölmede bir araya **alınan Hata** Listesi **ve Çıkış** penceresi gibi iki araç penceresi daha gösterilir.

 Ayrıca, çeşitli düzenleyici pencerelerini gösteren ana belge bölmesi de gösterilir. Araç pencerelerinin genellikle yalnızca bir örneği olsa da (örneğin, yalnızca bir **Çözüm Gezgini** açabilirsiniz), düzenleyici pencerelerinin her biri ayrı bir belgeyi düzenlemek için kullanılan ancak hepsi aynı bölmeye yerleştirilen birden çok örnek olabilir. Resimde, bir form tasarımcısı penceresi olmak için iki düzenleyici penceresi olan bir belge bölmesi gösterilir. Belge bölmesindeki tüm pencereler sekmelere tıklayarak kullanılabilir, ancak EditorPane.cs dosyasını içeren düzenleyici penceresi görünür ve etkindir.

 Uzantıyı genişlet Visual Studio kullanıcıların uzantınız ile etkileşim kurmasına izin Visual Studio araç pencereleri oluşturabilirsiniz. Ayrıca, kullanıcıların belgeleri düzenlemesine izin Visual Studio kendi düzenleyicilerinizi oluşturabilirsiniz. Araç pencerelerinizi ve düzenleyicilerinizi tümleştirin Visual Studio, bunları yerleştirecek veya bir sekmede doğru şekilde görünecek şekilde programlayamanıza gerek yok. Visual Studio'a doğru şekilde Visual Studio, otomatik olarak araç pencerelerinin ve belge pencerelerinin tipik özelliklerine Visual Studio. Daha fazla bilgi için [bkz. Genişletme ve Özelleştirme Aracı Windows.](../../extensibility/extending-and-customizing-tool-windows.md)

## <a name="document-windows"></a>Belge Pencereleri
 Belge penceresi, çok belgeli arabirim (MDI) penceresinin çerçeveli alt penceresidir. Belge pencereleri genellikle metin düzenleyicilerini, form düzenleyicilerini (tasarımcılar olarak da bilinir) veya düzenleme denetimlerini barındırmak için kullanılır, ancak diğer işlev türlerini de barındırabilirsiniz. Yeni **Dosya iletişim** kutusu, dosyanın sağladığı belge pencerelerinin Visual Studio içerir.

 Çoğu düzenleyici bir programlama diline veya HTML sayfaları, çerçeve kümeleri, C++ dosyaları veya üst bilgi dosyaları gibi bir dosya türüne özgüdür. Kullanıcı, Yeni Dosya **iletişim kutusunda bir** şablon seçerek, şablonla ilişkili dosya türü için düzenleyici için dinamik olarak bir belge penceresi oluşturur. Kullanıcı mevcut bir dosyayı açtığında da bir belge penceresi oluşturulur.

 Belge pencereleri MDI istemci alanıyla sınırlıdır. Her belge penceresinin üst kısmında bir sekme vardır ve sekme sırası MDI alanında açık olan diğer pencerelere bağlıdır. Belge penceresinin sekmesine sağ tıklarken, MDI alanı birden çok yatay veya dikey sekme gruplarına bölme seçeneklerini içeren bir kısayol menüsü görüntülenir. MDI alanı bölmek, birden çok dosyanın aynı anda görüntülemeye olanak sağlar. Daha fazla bilgi için [bkz. Belge Windows.](../../extensibility/internals/document-windows.md)

## <a name="editors"></a>Düzenleyiciler
 Visual Studio düzenleyicisi, bu düzenleyiciyi özelleştirmenize ve kendi içerik türünüz için kullanmanıza olanak Managed Extensibility Framework sağlar. Çoğu durumda düzenleyiciyi genişletmek için VSPackage oluşturmanız gerekmese de, kabuktan özellikler eklemek (örneğin, bir menü komutu veya kısayol tuşu) eklemek için BIR MEF uzantısını VSPackage ile birleştirebilirsiniz.

 Ayrıca, örneğin bir veritabanını okumak ve yazmak veya tasarımcı kullanmak isterseniz özel bir düzenleyici de oluşturabilirsiniz. Not Defteri veya Microsoft WordPad gibi bir dış düzenleyici de kullanabilirsiniz. Daha fazla bilgi için [bkz. Düzenleyici ve Dil Hizmeti Uzantıları.](../../extensibility/editor-and-language-service-extensions.md)

## <a name="language-services"></a>Dil Hizmetleri
 Düzenleyicinin yeni Visual Studio anahtar sözcükleri veya hatta yeni bir programlama dilini desteklemesi için bir dil hizmeti oluşturmanız gerekir. Her dil hizmeti belirli düzenleyici özelliklerini tamamen, kısmen veya hiç uygulamaz. Dil hizmeti, nasıl yapılandırıldıklerine bağlı olarak söz dizimi vurgulama, küme ayracı eşleştirme, IntelliSense desteği ve düzenleyicide diğer özellikler sağlar.

 Dil hizmetinin merkezinde ayrıştırıcı ve tarayıcı yer almaktadır. Tarayıcı (veya sözcük sözcük) bir kaynak dosyayı belirteç olarak bilinen öğelere böler ve ayrıştırıcı bu belirteçler arasındaki ilişkileri kurulur. Dil hizmeti oluşturma sırasında, dil belirteçlerini ve dil bilgisini Visual Studio için ayrıştırıcıyı ve tarayıcıyı uygulamalısınız. Yönetilen veya yönetilemeyen dil hizmetleri oluşturabilirsiniz. Daha fazla bilgi için [bkz. Eski Dil Hizmeti Genişletilebilirliği.](../../extensibility/internals/legacy-language-service-extensibility.md)

## <a name="projects"></a>Projeler

Bu Visual Studio, geliştiricilerin kaynak kodunu ve diğer kaynakları düzenlemek ve derlemek için kullanabileceği kapsayıcılardır. Projeler kaynak kodunu düzenlemenize, derlemenize, hata ayıklamanızı ve dağıtmanızı, Web hizmetleri ve veritabanlarına yönelik başvuruları ve diğer kaynakları dağıtmanızı sağlar. VSPackage'lar proje Visual Studio, proje alt türleri ve özel araçlar sağlayarak proje sistemini genişletebilirsiniz.

Projeler ayrıca bir çözümde bir araya *toplanmış olabilir.* Bu, bir uygulama oluşturmak için birlikte çalışan bir veya daha fazla projeden gruplamadır. Project ilgili durum bilgileri ve durum bilgileri, metin tabanlı çözüm [(.sln)](solution-dot-sln-file.md) dosyası ve ikili çözüm kullanıcı seçeneği [(.suo)](solution-user-options-dot-suo-file.md)dosyası olmak için iki çözüm dosyasında depolanır. Bu dosyalar, Visual Basic'nin önceki sürümlerinde kullanılan grup (.vbg) dosyalarına ve C++ önceki sürümlerinde kullanılan çalışma alanı (.dsw) ve kullanıcı seçenekleri (.opt) dosyalarına benzer.

Daha fazla bilgi için bkz. [Projeler](../../extensibility/internals/projects.md) ve [Çözümler.](../../extensibility/internals/solutions-overview.md)

## <a name="project-and-item-templates"></a>Proje ve Öğe Şablonları
 Visual Studio önceden tanımlanmış proje şablonları ve proje öğesi şablonları içerir. Ayrıca kendi şablonlarınızı oluşturabilir veya topluluktan şablonlar edinebilirsiniz ve ardından bunları kendi şablonlarınız ile Visual Studio. [MSDN Kod Galerisi,](https://code.msdn.microsoft.com/site/search?query=visual%20studio) şablonlar ve uzantılar için uygun yerdir.

 Şablonlar, belirli bir uygulama, denetim, kitaplık veya sınıf oluşturmak için gereken proje yapısını ve temel dosyaları içerir. Şablonlardan biri gibi bir yazılım geliştirmek istediğinizde, şablonu temel alan bir proje oluşturun ve ardından bu projede dosyaları değiştirebilirsiniz.

> [!NOTE]
> Bu şablon mimarisi projeler için [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] desteklenmiyor.

 Daha fazla bilgi için [bkz. Project ve Project Şablonları Ekleme.](../../extensibility/internals/adding-project-and-project-item-templates.md)

## <a name="properties-and-options"></a>Özellikler ve Seçenekler
 Özellikler **penceresi,** seçilen tek veya birden çok öğenin özelliklerini [görüntüler:](../../extensibility/internals/extending-properties.md) Özellikler Seçenekleri sayfalarını genişletme, programlama dili veya VSPackage gibi belirli bir bileşenle ilgili seçenek kümeleri içerir: Seçenekler ve [Seçenekler Sayfaları.](../../extensibility/internals/options-and-options-pages.md) Ayarlar genel olarak kullanıcı arabirimiyle ilgili, içe ve dışarı aktarılmış özelliklerdir: [Kullanıcı Arabirimi Ayarlar.](../../extensibility/internals/support-for-user-settings.md)

## <a name="visual-studio-services"></a>Visual Studio Hizmetleri
 Hizmet, bileşenlerin tüketmesi için belirli bir arabirim kümesi sağlar. Visual Studio, uzantılar da dahil olmak üzere tüm bileşenler tarafından kullanılmaktadır. Örneğin, Visual Studio pencerelerini dinamik olarak gösterme veya gizli olarak etkinleştirme, Yardım, durum çubuğu veya KULLANıCı arabirimi olaylarına erişimi etkinleştirme. Bu Visual Studio düzenleyici, düzenleyici uzantıları tarafından içe aktarılmış hizmetler de sağlar. Daha fazla bilgi için [bkz. Using and Providing Services](../../extensibility/using-and-providing-services.md).

## <a name="debugger"></a>Hata Ayıklayıcısı
 Hata ayıklayıcı, dile özgü hata ayıklama bileşenleri için kullanıcı arabirimidir. Yeni bir dil hizmeti oluşturduysanız hata ayıklayıcıya bağlanacak belirli bir hata ayıklama altyapısı oluşturmanız gerekir. Daha fazla bilgi için [bkz. Visual Studio Hata Ayıklayıcısı Genişletilebilirliği.](../../extensibility/debugger/visual-studio-debugger-extensibility.md)

## <a name="source-control"></a>Kaynak Denetimi
 Kaynak denetimi eklentisi veya VSPackage uygulama hakkında bilgi için bkz. [Kaynak Denetimi.](../../extensibility/internals/source-control.md)

## <a name="wizards"></a>Sihirbazlar
 Sihirbazı yeni proje türüyle birlikte oluşturabilirsiniz; böylece sihirbaz, kullanıcılarınızı bu türde yeni bir proje oluşturduklarında doğru kararları almalarına yardımcı olabilir. Daha fazla bilgi için [bkz. Sihirbazlar.](../../extensibility/internals/wizards.md)

## <a name="custom-tools"></a>Özel Araçlar
 Özel araçlar, bir aracı proje içinde bir öğeyle ilişkilendirmenizi ve dosya her kaydedilebilirken bu aracı çalıştırmanızı sağlar. Daha fazla bilgi için bkz. [Özel Araçlar](../../extensibility/internals/custom-tools.md).

## <a name="vssdk-utilities"></a>VSSDK Yardımcı Programları
 VSSDK, VSPackage'ların farklı yönleriyle çalışmak için ihtiyacınız olan bir dizi yardımcı program içerir. Daha fazla bilgi için bkz. [VSSDK Yardımcı Programları.](../../extensibility/internals/vssdk-utilities.md)

## <a name="using-windows-installer"></a>Windows Yükleyiciyi Kullanma
 Bazı durumlarda VSIX yükleyicisi yerine Windows Yükleyicisi'ni kullanabilirsiniz. Örneğin, kayıt defterine yazmanız gerekir. Windows Installer'ı uzantılarınız ile kullanma hakkında bilgi için [bkz. VSPackage'ları Windows Yükleme.](../../extensibility/internals/installing-vspackages-with-windows-installer.md)

## <a name="help-viewer"></a>Yardım Görüntüleyicisi
 Kendi yardım ve F1 sayfalarınızı Yardım Görüntüleyicisi ile tümleştirebilirsiniz. Daha fazla bilgi için [bkz. Microsoft Yardım Görüntüleyicisi SDK.](../../extensibility/internals/microsoft-help-viewer-sdk.md)
