---
title: İçi Görsel Stüdyo SDK | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- roadmap, Visual Studio integration SDK
- Visual Studio integration SDK roadmap
- integration roadmap, Visual Studio SDK
ms.assetid: 9118eaa4-0453-4dc5-9e16-c7062d254869
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0e72020795bc3181e11f0f90eff580a2365d4000
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707584"
---
# <a name="inside-the-visual-studio-sdk"></a>Visual Studio SDK’nın İçinde

Bu bölümde Visual Studio mimarisi, bileşenleri, hizmetleri, şemalar, yardımcı programlar ve benzeri dahil olmak üzere Visual Studio uzantıları hakkında ayrıntılı bilgi sağlar.

## <a name="extensibility-architecture"></a>Genişletilebilirlik Mimarisi
 Aşağıdaki resimde Visual Studio genişletilebilirlik mimarisi gösterilmektedir. VSPackages, IDE genelinde hizmet olarak paylaşılan uygulama işlevselliği sağlar. Standart IDE, IDE pencereleme işlevine <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>erişim sağlayan geniş bir hizmet yelpazesi de sunar.

 ![Çevre Mimarisi grafiği](../../extensibility/internals/media/environment.gif "environment") Visual Studio mimarisinin genelleştirilmiş görünümü

## <a name="vspackages"></a>VSPackage’lar
 VSPackages, UI öğeleri, hizmetler, projeler, editörler ve tasarımcılarla Visual Studio'u oluşturan ve genişleten yazılım modülleridir. VSPackages Visual Studio merkezi mimari birimidir. Daha fazla bilgi için [VSPackages'e](../../extensibility/internals/vspackages.md)bakın.

## <a name="visual-studio-shell"></a>Visual Studio Kabuğu
 Visual Studio kabuğu, bileşeni VSPackages ve MEF uzantıları arasında temel işlevsellik ve destek çapraz iletişim sağlar. Daha fazla bilgi için [Visual Studio Shell'e](../../extensibility/internals/visual-studio-shell.md)bakın.

## <a name="user-experience-guidelines"></a>Kullanıcı Deneyimi Yönergeleri
 Visual Studio için yeni özellikler tasarlamayı planlıyorsanız, tasarım ve kullanılabilirlik ipuçları için bu yönergelere bir göz atmalısınız: [Visual Studio Kullanıcı Deneyimi Yönergeleri.](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)

## <a name="commands"></a>Komutlar
 Komutlar, belge yazdırma, görünümü yenileme veya yeni bir dosya oluşturma gibi görevleri gerçekleştiren işlevlerdir.

 Visual Studio'yu genişletdiğinizde, komutlar oluşturabilir ve Bunları Visual Studio kabuğuna kaydedebilirsiniz. Bu komutların IDE'de örneğin bir menüde veya araç çubuğunda nasıl görüneceğini belirtebilirsiniz. Genellikle **Araçlar** menüsünde özel bir komut görüntülenir ve bir araç penceresi görüntülemek için bir komut **Görünüm** menüsünün **Diğer Windows** alt menüsünde görünür.

 Bir komut oluşturduğunuzda, bunun için bir olay işleyicisi de oluşturmanız gerekir. Olay işleyicisi komutun ne zaman görünür veya etkin olacağını belirler, metnini değiştirmenize izin verir ve etkinleştirildiğinde komutun uygun şekilde yanıt verdiğini garanti eder. Çoğu durumda, IDE <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> arabirimi kullanarak komutları işler. Visual Studio'daki komutlar, yerel seçilim temel alınarak en içteki komut bağlamından başlayarak ve genel seçime dayalı olarak en dıştaki içeriğe doğru ilerler. Ana menüye eklenen komutlar komut dosyası için hemen kullanılabilir.

 Daha fazla bilgi için [Komutlar, Menüler ve Araç Çubukları'na](../../extensibility/internals/commands-menus-and-toolbars.md)bakın.

## <a name="menus-and-toolbars"></a>Menüler ve Araç Çubukları
 Menüler ve araç çubukları, kullanıcıların komutları çağırması için bir yol sağlar. Menüler, genellikle bir araç penceresinin üst kısmında tek tek metin öğeleri olarak görüntülenen komut satırları veya sütunlarıdır. Alt menüler, kullanıcı küçük bir ok içeren komutları tıklattığında görünen ikincil menülerdir. Bir kullanıcı belirli Kullanıcı Arası Öğeleri'ni sağ tıklattığında bağlam menüleri görüntülenir. Bazı yaygın menü adları **Dosya,** **Edit,** **Görünüm**ve **Pencere'dir.** Daha fazla bilgi için, [Menüleri ve Komutları Genişletme'ye](../../extensibility/extending-menus-and-commands.md)bakın.

 Araç çubukları, açılan kutular, liste kutuları ve metin kutuları gibi düğme ve diğer denetimlerin satırları veya sütunlarıdır. Araç çubuğu düğmelerinde genellikle **Açık Dosya** komutu için klasör simgesi veya **Yazdır** komutu için yazıcı gibi simge resimleri bulunur. Tüm araç çubuğu öğeleri komutlarla ilişkilidir. Bir araç çubuğu düğmesini tıklattığınızda, ilişkili komutu çalışır. Açılan denetim söz konusu olduğunda, açılır listedeki her öğe farklı bir komutla ilişkilidir. Bölücü denetimi gibi bazı araç çubuğu denetimleri melezdir. Denetimin bir tarafı araç çubuğu düğmesi, diğer tarafı ise tıklatıldığında birkaç komut görüntüleyen bir aşağı oktur.

## <a name="tool-windows"></a>Araç Pencereleri
 Araç pencereleri Bilgileri görüntülemek için IDE'de kullanılır. **Araç kutusu**, **Çözüm Gezgini**, **Özellikler** penceresi ve **Web Tarayıcısı** araç pencerelerinin örnekleridir.

 Araç pencereleri genellikle kullanıcının etkileşim kurabileceği çeşitli denetimler sunar. Örneğin, **Özellikler** penceresi, kullanıcının belirli bir amaca hizmet eden nesnelerin özelliklerini ayarlamasına olanak tanır. **Özellikler** penceresi bu anlamda uzmanlaşmıştır, ancak birçok farklı durumda kullanılabildiği için geneldir. Benzer şekilde, Metin tabanlı çıktı sağladığı için **Çıktı** penceresi özelleştirilmiştir, ancak Visual Studio'daki birçok alt sistem Visual Studio kullanıcısına çıktı sağlamak için kullanabileceğinden genel olarak kullanılır.

 Birkaç araç penceresi içeren Visual Studio'nun aşağıdaki resmini düşünün:

 ![Ekran görüntüsü](../../extensibility/internals/media/t1gui.png "T1gui")

 Bazı araç pencereleri, Çözüm Gezgini araç penceresini görüntüleyen ve diğer araç pencerelerini gizleyen ancak sekmeleri tıklatarak kullanılabilir hale getiren tek bir bölmeye sabitlenir. Resim, tek bir bölmede birbirine kenetlenmiş diğer iki araç penceresi olan **Hata Listesi** ve **Çıktı** penceresini gösterir.

 Ayrıca gösterilen birkaç düzenleyici pencere gösterir ana belge bölmesi vardır. Araç pencerelerinde genellikle yalnızca bir örnek olsa da (örneğin, yalnızca bir **Çözüm Gezgini**açabilirsiniz), düzenleyici pencerelerde her biri ayrı bir belgeyi düzenlemek için kullanılan ancak tümü aynı bölmeye sabitlenmiş olan birden çok örnek olabilir. Resimde iki düzenleyici penceresi, bir form tasarımcısı penceresi olan bir belge bölmesi gösterilmektedir. Belge bölmesindeki tüm pencereler sekmeleri tıklatarak kullanılabilir, ancak EditorPane.cs dosya içeren düzenleyici penceresi görünür ve etkindir.

 Visual Studio'yı genişletdiğinizde, Visual Studio kullanıcılarının uzantınızınizle etkileşimkurmasına izin veren araç pencereleri oluşturabilirsiniz. Visual Studio kullanıcılarının belgeleri düzenlenmesine izin veren kendi editörlerinizi de oluşturabilirsiniz. Araç pencereleriniz ve editörleriniz Visual Studio'ya entegre edilince, bunları bir sekmede doğru şekilde yerleştirmeleri veya görünmesi için programlamanız gerekmez. Visual Studio'ya doğru bir şekilde kaydedildiklerinde, Visual Studio'daki araç pencerelerinin ve belge pencerelerinin tipik özelliklerine otomatik olarak sahip olurlar. Daha fazla bilgi için Bkz. [Genişletme ve Özelleştirme Aracı Windows.](../../extensibility/extending-and-customizing-tool-windows.md)

## <a name="document-windows"></a>Belge Pencereleri
 Belge penceresi, birden çok belge arabirimi (MDI) penceresinin çerçeveli alt penceresidir. Belge pencereleri genellikle metin editörlerini, form düzenleyicilerini (tasarımcı olarak da bilinir) veya denetimleri düzenlemek için kullanılır, ancak diğer işlevsel türleri de barındırabilirler. **Yeni Dosya** iletişim kutusu, Visual Studio'nun sağladığı belge pencerelerinden örnekler içerir.

 Çoğu düzenleyici, bir programlama diline veya HTML sayfaları, çerçeve kümeleri, C++ dosyaları veya üstbilgi dosyaları gibi bir dosya türüne özgüdür. **Yeni Dosya** iletişim kutusunda bir şablon seçerek, kullanıcı şablonla ilişkili dosya türü için düzenleyici için bir belge penceresi oluşturur. Bir kullanıcı varolan bir dosyayı açtığında da belge penceresi oluşturulur.

 Belge pencereleri MDI istemci alanıyla sınırlıdır. Her belge penceresinin üst kısmında bir sekme vardır ve sekme sırası MDI alanında açık olabilecek diğer pencerelere bağlıdır. Belge penceresinin sekmesini sağ tıklattığınızda, MDI alanını birden çok yatay veya dikey sekme grubuna bölme seçenekleri içeren bir kısayol menüsü görüntülenir. MDI alanının bölünmesi, birden çok dosyanın aynı anda görüntülenmesini sağlar. Daha fazla bilgi için [Bkz. Windows Belgesi.](../../extensibility/internals/document-windows.md)

## <a name="editors"></a>Düzenleyiciler
 Visual Studio editörü, Yönetilen Genişletilebilirlik Çerçevesi (MEF) ile özelleştirip kendi içerik türünüz için kullanmanıza olanak tanır. Çoğu durumda, düzenleyiciyi genişletmek için bir VSPackage oluşturmanız gerekmez, ancak kabuktan özellikler eklemek isterseniz (örneğin, bir menü komutu veya kısayol tuşu), bir MEF uzantısını VSPackage ile birleştirebilirsiniz.

 Ayrıca, örneğin bir veritabanını okuyup yazmak istiyorsanız veya bir tasarımcı kullanmak istiyorsanız özel bir düzenleyici de oluşturabilirsiniz. Not Defteri veya Microsoft WordPad gibi harici bir düzenleyici de kullanabilirsiniz. Daha fazla bilgi için [Editör ve Dil Hizmeti Uzantıları'na](../../extensibility/editor-and-language-service-extensions.md)bakın.

## <a name="language-services"></a>Dil Hizmetleri
 Visual Studio düzenleyicisinin yeni programlama anahtar kelimelerini ve hatta yeni bir programlama dilini desteklemesini istiyorsanız, bir dil hizmeti oluşturursunuz. Her dil hizmeti belirli düzenleyici özelliklerini tam olarak, kısmen veya hiç uygulayabilir. Nasıl yapılandırıldığına bağlı olarak, dil hizmeti sözdizimi vurgulama, ayraç eşleştirme, IntelliSense desteği ve düzenleyicideki diğer özellikleri sağlayabilir.

 Bir dil servisinin kalbinde bir ayrıştırıcı ve tarayıcı vardır. Tarayıcı (veya lexer), kaynak dosyayı belirteçolarak bilinen öğelere böler ve bir parser bu belirteçler arasındaki ilişkileri kurar. Bir dil hizmeti oluşturduğunuzda, Visual Studio'nun dilin belirteçlerini ve dilbilgisini anlayabilmeleri için ayrıştırıcıyı ve tarayıcıyı uygulamanız gerekir. Yönetilen veya yönetilmeyen dil hizmetleri oluşturabilirsiniz. Daha fazla bilgi için [Bkz. Eski Dil Hizmeti Genişletilebilirliği.](../../extensibility/internals/legacy-language-service-extensibility.md)

## <a name="projects"></a>Projeler

Visual Studio'da projeler, geliştiricilerin kaynak kodunu ve diğer kaynakları düzenlemek ve oluşturmak için kullandıkları kapsayıcılardır. Projeler, kaynak kodu, Web hizmetleri ve veritabanlarına yapılan başvuruları ve diğer kaynakları düzenlemenize, oluşturmanıza, hata ayıklamanıza ve dağıtmanıza izin verir. VSPackages proje türleri, proje alt türleri ve özel araçlar sağlayarak Visual Studio proje sistemini genişletebilir.

Projeler, bir uygulama oluşturmak için birlikte çalışan bir veya daha fazla projenin gruplandırması olan bir *çözümde*de bir araya getirilebilir. Çözümle ilgili proje ve durum bilgileri iki çözüm dosyasında, metin tabanlı [çözüm (.sln) dosyasında](solution-dot-sln-file.md) ve ikili [çözüm kullanıcı seçeneğinde (.suo)](solution-user-options-dot-suo-file.md)saklanır. Bu dosyalar Visual Basic'in önceki sürümlerinde kullanılan grup (.vbg) dosyalarına ve C++'ın önceki sürümlerinde kullanılan çalışma alanı (.dsw) ve kullanıcı seçeneklerine (.opt) benzer.

Daha fazla bilgi için [Projeler](../../extensibility/internals/projects.md) ve [Çözümler'e](../../extensibility/internals/solutions-overview.md)bakın.

## <a name="project-and-item-templates"></a>Proje ve Öğe Şablonları
 Visual Studio önceden tanımlanmış proje şablonları ve proje öğesi şablonları içerir. Ayrıca kendi şablonlarınızı yapabilir veya topluluktan şablonlar edinebilir ve bunları Visual Studio'ya entegre edebilirsiniz. [MSDN Kod Galerisi](https://code.msdn.microsoft.com/site/search?query=visual%20studio) şablonlar ve uzantılar için gidilen yerdir.

 Şablonlar, belirli bir uygulama, denetim, kitaplık veya sınıf oluşturmak için gereken proje yapısını ve temel dosyaları içerir. Şablonlardan birine benzeyen bir yazılım geliştirmek istediğinizde, şablonu temel alan bir proje oluşturun ve ardından bu projedeki dosyaları değiştirin.

> [!NOTE]
> Bu şablon mimarisi projeler [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] için desteklenmez.

 Daha fazla bilgi için [bkz.](../../extensibility/internals/adding-project-and-project-item-templates.md)

## <a name="properties-and-options"></a>Özellikler ve Seçenekler
 **Özellikler** penceresi tek veya birden çok seçili öğenin özelliklerini görüntüler: [Genişletme Özellikleri](../../extensibility/internals/extending-properties.md) Seçenekleri sayfaları, programlama dili veya VSPackage: Seçenekler ve [Seçenekler Sayfaları](../../extensibility/internals/options-and-options-pages.md)gibi belirli bir bileşenle ilgili seçenekler kümeleri içerir. Ayarlar genellikle dış anumarası ile ilgili içe aktarılabilen ve dışa aktarılabilen özelliklerdir: [Kullanıcı Ayarları desteği.](../../extensibility/internals/support-for-user-settings.md)

## <a name="visual-studio-services"></a>Görsel Stüdyo Hizmetleri
 Bir hizmet, bileşenlerin tüketilmesi için belirli bir arabirim kümesi sağlar. Visual Studio uzantıları da dahil olmak üzere herhangi bir bileşen tarafından kullanılabilecek bir hizmet kümesi sağlar. Örneğin, Visual Studio hizmetleri araç pencerelerini dinamik olarak gösterilmesini veya gizli olmasını, Yardım, durum çubuğu veya UI etkinliklerine erişimi etkinleştirir. Visual Studio düzenleyicisi ayrıca düzenleyici uzantıları tarafından içe aktarılabilen hizmetler de sağlar. Daha fazla bilgi için [bkz.](../../extensibility/using-and-providing-services.md)

## <a name="debugger"></a>Hata Ayıklayıcısı
 Hata ayıklama, dile özgü hata ayıklama bileşenlerinin kullanıcı arabirimidir. Yeni bir dil hizmeti oluşturduysanız, hata ayıklama için belirli bir hata ayıklama altyapısı oluşturmanız gerekir. Daha fazla bilgi için [Visual Studio Debugger Genişletilebilirliği](../../extensibility/debugger/visual-studio-debugger-extensibility.md)bölümüne bakın.

## <a name="source-control"></a>Kaynak Denetimi
 Kaynak denetimi eklentisi veya VSPackage uygulama hakkında bilgi için [Kaynak Denetimi'ne](../../extensibility/internals/source-control.md)bakın.

## <a name="wizards"></a>Sihirbazlar
 Sihirbazın, kullanıcılarınızın bu tür de yeni bir proje oluşturduklarında doğru kararları almalarına yardımcı olabilmesi için, yeni bir proje türüyle birlikte bir sihirbaz oluşturabilirsiniz. Daha fazla bilgi için [bkz.](../../extensibility/internals/wizards.md)

## <a name="custom-tools"></a>Özel Araçlar
 Özel araçlar, bir aracı projedeki bir öğeyle ilişkilendirmenize ve dosya kaydedildiğinde bu aracı çalıştırmanıza izin sağlar. Daha fazla bilgi için [Bkz. Özel Araçlar.](../../extensibility/internals/custom-tools.md)

## <a name="vssdk-utilities"></a>VSSDK Yardımcı Programları
 VSSDK, VSPackages'in farklı yönleriyle çalışmak için ihtiyaç duyabileceğiniz bir dizi yardımcı program içerir. Daha fazla bilgi için [VSSDK Yardımcı Programları'na](../../extensibility/internals/vssdk-utilities.md)bakın.

## <a name="using-windows-installer"></a>Windows Yükleyici kullanma
 Bazı durumlarda VSIX yükleyicisi yerine Windows Yükleyici'yi kullanmanız gerekebilir: örneğin, kayıt defterine yazmanız gerekebilir. Uzantılarınızla Windows Installer'ı kullanma hakkında daha fazla bilgi için Windows [Installer ile VSPackages Yükleme'ye](../../extensibility/internals/installing-vspackages-with-windows-installer.md)bakın.

## <a name="help-viewer"></a>Yardım Görüntüleyici
 Kendi yardımınızı ve F1 sayfalarınızı Yardım Görüntüleyici'ye entegre edebilirsiniz. Daha fazla bilgi için [Microsoft Yardım Görüntüleyici SDK'ya](../../extensibility/internals/microsoft-help-viewer-sdk.md)bakın.
