---
title: Visual Studio SDK içinde | Microsoft Docs
description: Visual Studio mimarisi, bileşenler, hizmetler, şemalar ve yardımcı programlar dahil Visual Studio SDK 'daki uzantılar hakkında bilgi edinin.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 73bbb1beb30677711b8b517262b48465e7529585
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98205339"
---
# <a name="inside-the-visual-studio-sdk"></a>Visual Studio SDK’nın İçinde

Bu bölümde Visual Studio mimarisi, bileşenler, hizmetler, şemalar, yardımcı programlar ve gibi Visual Studio uzantıları hakkında ayrıntılı bilgiler sağlanmaktadır.

## <a name="extensibility-architecture"></a>Genişletilebilirlik mimarisi
 Aşağıdaki çizimde, Visual Studio genişletilebilirlik mimarisi gösterilmektedir. VSPackages, IDE 'de hizmet olarak paylaşılan uygulama işlevlerini sağlar. Standart IDE, <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> IDE Pencereleme işlevselliğine erişim sağlayan gibi çok çeşitli hizmetler de sunar.

 ![Ortam Mimarisi grafiği](../../extensibility/internals/media/environment.gif "ortam") Visual Studio mimarisinin Genelleştirilmiş görünümü

## <a name="vspackages"></a>VSPackage’lar
 VSPackages, UI öğeleri, hizmetler, projeler, düzenleyiciler ve tasarımcılarla Visual Studio 'Yu oluşturan ve genişleten yazılım modüllerdir. VSPackages, Visual Studio 'nun merkezi mimari birimidir. Daha fazla bilgi için bkz. [VSPackages](../../extensibility/internals/vspackages.md).

## <a name="visual-studio-shell"></a>Visual Studio Kabuğu
 Visual Studio Kabuğu, temel işlevleri sağlar ve bileşen VSPackages ve MEF uzantıları arasında çapraz iletişim desteği sağlar. Daha fazla bilgi için bkz. [Visual Studio Kabuğu](../../extensibility/internals/visual-studio-shell.md).

## <a name="user-experience-guidelines"></a>Kullanıcı Deneyimi Yönergeleri
 Visual Studio için yeni özellikler tasarlamayı planlıyorsanız, tasarım ve kullanılabilirlik ipuçları için şu yönergelere göz atalım: [Visual Studio Kullanıcı deneyimi yönergeleri](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).

## <a name="commands"></a>Komutlar
 Komutlar, bir belge yazdırmak, bir görünümü yenilemek veya yeni bir dosya oluşturmak gibi görevleri gerçekleştiren işlevlerdir.

 Visual Studio 'Yu genişlettiğinizde, komutlar oluşturabilir ve bunları Visual Studio Kabuğu ile kaydedebilirsiniz. Bu komutların IDE 'de nasıl görüneceğini (örneğin, bir menü veya araç çubuğunda) belirtebilirsiniz. Genellikle **Araçlar** menüsünde özel bir komut görünür ve araç penceresi görüntüleme komutu, **Görünüm** menüsünün **diğer Windows** alt menüsünde görüntülenir.

 Bir komut oluşturduğunuzda, bunun için de bir olay işleyicisi oluşturmanız gerekir. Olay işleyicisi, komutun ne zaman görünür veya etkin olduğunu belirler, metnini değiştirmenize olanak sağlar ve etkinleştirildiğinde komutun uygun şekilde yanıt vermesini garanti eder. Çoğu örnekte, IDE komutları arabirimini kullanarak işler <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> . Visual Studio 'daki komutlar, yerel seçime göre ve genel seçime bağlı olarak en dıştaki içeriğe devam eden en içteki komut bağlamından başlayarak işlenir. Ana menüye eklenen komutlar, komut dosyası oluşturma için hemen kullanılabilir.

 Daha fazla bilgi için bkz. [Komutlar, menüler ve araç çubukları](../../extensibility/internals/commands-menus-and-toolbars.md).

## <a name="menus-and-toolbars"></a>Menüler ve araç çubukları
 Menüler ve araç çubukları, kullanıcıların komutları çağırmasına yönelik bir yol sağlar. Menüler, genellikle en üstteki bir araç penceresinde tek metin öğeleri olarak görüntülenen komut satırlarıdır. Alt menüler, Kullanıcı küçük bir ok içeren komutlara tıkladığında görünen ikincil menülerdir. Bağlam menüleri, bir Kullanıcı belirli kullanıcı arabirimi öğelerini sağ tıklattığında görüntülenir. Bazı ortak menü adları **Dosya**, **düzenleme**, **görüntüleme** ve **pencere**. Daha fazla bilgi için bkz. [genişletme menüleri ve komutları](../../extensibility/extending-menus-and-commands.md).

 Araç çubukları, düğme ve açılan kutular, liste kutuları ve metin kutuları gibi düğmelerin ve diğer denetimlerin satır veya sütunlarıdır. Araç çubuğu düğmeleri genellikle **Açık dosya** komutu için klasör simgesi veya **Print** komutu için bir yazıcı gibi simge görüntülerine sahiptir. Tüm araç çubuğu öğeleri komutlarla ilişkilendirilir. Bir araç çubuğu düğmesine tıkladığınızda, ilişkili komutu çalışır. Açılan bir denetim olması durumunda, açılan listedeki her öğe farklı bir komutla ilişkilendirilir. Splitter denetimi gibi bazı araç çubuğu denetimleri hybrilar. Denetimin bir tarafı bir araç çubuğu düğmesidir ve diğer kenar tıklandığında birkaç komut görüntüleyen aşağı oktur.

## <a name="tool-windows"></a>Araç Pencereleri
 Araç pencereleri, bilgileri göstermek için IDE 'de kullanılır. **Araç kutusu**, **Çözüm Gezgini**, **Özellikler** penceresi ve **Web tarayıcısı** araç pencerelerinin örnekleridir.

 Araç pencereleri genellikle kullanıcının etkileşime girebileceği çeşitli denetimler sunar. Örneğin, **Özellikler** penceresi, kullanıcının belirli bir amaca yönelik nesnelerin özelliklerini ayarlayabilmenizi sağlar. **Özellikler** penceresi bu anlamda özelleştirilmiştir, ancak aynı zamanda genel olarak birçok farklı durumda kullanılabilir. Benzer şekilde, metin tabanlı çıkış sağladığından **Çıkış** penceresi özelleştirilmiştir, ancak Visual Studio 'daki pek çok alt sistemi Visual Studio kullanıcısına çıkış sağlamak üzere kullanabileceğinden, genel olarak.

 Visual Studio 'nun çeşitli araç pencerelerini içeren aşağıdaki resmini göz önünde bulundurun:

 ![Ekran görüntüsü](../../extensibility/internals/media/t1gui.png "T1gui")

 Bazı araç pencereleri, Çözüm Gezgini araç penceresini görüntüleyen ve diğer araç pencerelerini gizleyen ve sekmeler ' i tıklatarak kullanılabilir hale getiren tek bir bölmede birlikte yerleştirildi. Resimde, tek bir bölmede birlikte yerleştirilen **hata listesi** ve **Çıkış** penceresi olmak üzere iki diğer araç pencereleri gösterilmektedir.

 Ayrıca, çeşitli düzenleyici pencereleri gösteren ana belge bölmesi de gösterilir. Araç pencereleri genellikle yalnızca bir örneğe sahip olsa da (örneğin, yalnızca bir **Çözüm Gezgini** açabilirsiniz), düzenleyici pencerelerinin her biri ayrı bir belgeyi düzenlemek için kullanılan ancak hepsi aynı bölmeye yerleştirilmiş olan birden fazla örneğe sahip olabilir. Resimde, tek form Tasarımcısı penceresi olmak üzere iki düzenleyici Windows içeren bir belge bölmesi görüntülenir. Belge bölmesindeki tüm pencereler sekmeler ' i tıklatarak kullanılabilir, ancak EditorPane.cs dosyasını içeren Düzenleyici penceresi görünür ve etkin olur.

 Visual Studio 'Yu genişlettiğinizde, Visual Studio kullanıcılarının uzantlarınızla etkileşime girmesine izin veren araç pencereleri oluşturabilirsiniz. Ayrıca, Visual Studio kullanıcılarının belgeleri düzenlemesine izin veren kendi düzenleyicilerinizi de oluşturabilirsiniz. Araç pencereleri ve düzenleyicilerimizin Visual Studio ile tümleştirileceği için, onları sabitlemek veya bir sekmede doğru bir şekilde görünmesi için programlayabilirsiniz. Visual Studio 'da doğru şekilde kaydedildiğinde, Visual Studio 'daki araç pencereleri ve Belge pencerelerinin tipik özellikleri otomatik olarak olur. Daha fazla bilgi için bkz. [araç pencerelerini genişletme ve özelleştirme](../../extensibility/extending-and-customizing-tool-windows.md).

## <a name="document-windows"></a>Belge Pencereleri
 Belge penceresi, birden çok belge arabirimi (MDI) penceresinin çerçeveli bir alt penceresidir. Belge pencereleri genellikle metin düzenleyicileri, form Düzenleyicileri (tasarımcı olarak da bilinir) veya denetim denetimleri barındırmak için kullanılır, ancak diğer işlevsel türleri de barındırabilir. **Yeni dosya** iletişim kutusu, Visual Studio 'nun sağladığı belge pencerelerinin örneklerini içerir.

 Çoğu düzenleyici, bir programlama diline veya HTML sayfaları, çerçeve kümeleri, C++ dosyaları ya da üstbilgi dosyaları gibi bir dosya türüne özeldir. **Yeni dosya** iletişim kutusunda bir şablon seçerek Kullanıcı, şablonla ilişkili dosya türü için düzenleyici için bir belge penceresi oluşturur. Bir kullanıcı var olan bir dosyayı açtığında bir belge penceresi de oluşturulur.

 Belge pencereleri MDI istemci alanı ile kısıtlıdır. Her belge penceresinde üst kısımdaki bir sekme bulunur ve sekme sırası MDI alanında açık olabilecek diğer pencereler ile bağlantılıdır. Belge penceresinin sekmesine sağ tıklamak, MDI alanını birden çok yatay veya dikey sekme grubuna bölme seçeneklerini içeren bir kısayol menüsü görüntüler. MDI alanının bölünmesi, birden fazla dosyanın aynı anda görüntülenmesine olanak sağlar. Daha fazla bilgi için bkz. [belge pencereleri](../../extensibility/internals/document-windows.md).

## <a name="editors"></a>Düzenleyiciler
 Visual Studio Düzenleyicisi onu özelleştirmenize ve Managed Extensibility Framework (MEF) yoluyla kendi içerik türüne göre kullanmanıza olanak sağlar. Çoğu durumda, kabuğu genişletmek için bir VSPackage oluşturmanız gerekmez, ancak kabuktan Özellikler (örneğin, bir menü komutu veya kısayol tuşu) dahil etmek istiyor olsanız da bir MEF uzantısını VSPackage ile birleştirebilirsiniz.

 Özel bir düzenleyici de oluşturabilirsiniz; örneğin, bir veritabanına okumak ve yazmak isterseniz ya da bir tasarımcı kullanmak istiyorsanız. Not defteri veya Microsoft WordPad gibi bir harici düzenleyici de kullanabilirsiniz. Daha fazla bilgi için bkz. [Düzenleyici ve dil hizmeti uzantıları](../../extensibility/editor-and-language-service-extensions.md).

## <a name="language-services"></a>Dil Hizmetleri
 Visual Studio Düzenleyicisi 'nin yeni programlama anahtar sözcüklerini ve hatta yeni bir programlama dilini desteklemesini istiyorsanız, bir dil hizmeti oluşturursunuz. Her dil hizmeti, belirli düzenleyici özelliklerini tamamen, kısmen veya hiç bir şekilde uygulayabilir. Dil hizmeti, nasıl yapılandırıldığına bağlı olarak, söz dizimi vurgulaması, küme ayracı eşleştirme, IntelliSense desteği ve düzenleyicideki diğer özellikler sağlayabilir.

 Bir dil hizmetinin kalp bir ayrıştırıcısıdır ve bir tarayıcısıdır. Bir tarayıcı (veya sözcük temelli çözümleyici), kaynak dosyayı belirteç olarak bilinen öğelere böler ve bir Ayrıştırıcı Bu belirteçler arasında ilişkiler oluşturur. Bir dil hizmeti oluşturduğunuzda, Visual Studio 'nun dilin belirteçlerini ve dilbilgisini anlayabilmesi için ayrıştırıcısı ve tarayıcıyı uygulamanız gerekir. Yönetilen veya yönetilmeyen dil hizmetleri oluşturabilirsiniz. Daha fazla bilgi için bkz. [eski dil hizmeti genişletilebilirliği](../../extensibility/internals/legacy-language-service-extensibility.md).

## <a name="projects"></a>Projeler

Visual Studio 'da, projeler, geliştiricilerin kaynak kodu ve diğer kaynakları düzenlemek ve derlemek için kullandığı kapsayıcılardır. Projeler, kaynak kodu, Web Hizmetleri ve veritabanlarına yönelik başvuruları ve diğer kaynakları düzenlemenize, oluşturmanıza, hata ayıklamanıza ve dağıtmanıza olanak tanır. VSPackages, proje türleri, proje alt türleri ve özel araçlar sağlayarak Visual Studio proje sistemini genişletebilir.

Projeler aynı zamanda bir uygulama oluşturmak için birlikte çalışan bir veya daha fazla proje gruplandırması olan bir *çözümde* birlikte toplanabilir. Çözümle ilgili proje ve durum bilgileri, metin tabanlı [Çözüm (. sln) dosyası](solution-dot-sln-file.md) ve ikili [çözüm Kullanıcı seçeneği (. suo) dosyası](solution-user-options-dot-suo-file.md)olmak üzere iki çözüm dosyasında depolanır. Bu dosyalar, önceki Visual Basic sürümlerinde kullanılan grup (. vbg) dosyalarına ve C++ ' ın önceki sürümlerinde kullanılan çalışma alanı (. DSW) ve Kullanıcı seçenekleri (. opt) dosyalarına benzer.

Daha fazla bilgi için bkz. [Projeler](../../extensibility/internals/projects.md) ve [çözümler](../../extensibility/internals/solutions-overview.md).

## <a name="project-and-item-templates"></a>Proje ve Öğe Şablonları
 Visual Studio önceden tanımlanmış proje şablonlarını ve proje öğesi şablonlarını içerir. Ayrıca kendi şablonlarınızı yapabilir veya topluluktaki şablonlar alabilir ve ardından bunları Visual Studio ile tümleştirebilirsiniz. [MSDN Kod Galerisi](https://code.msdn.microsoft.com/site/search?query=visual%20studio) , şablonlar ve uzantılara gidecek yerdir.

 Şablonlar, belirli bir uygulama, denetim, kitaplık veya sınıf türü oluşturmak için gereken proje yapısını ve temel dosyaları içerir. Şablonlardan birine benzeyen yazılımlar geliştirmek istediğinizde, şablonu temel alan bir proje oluşturun ve ardından bu projedeki dosyaları değiştirin.

> [!NOTE]
> Bu şablon mimarisi projeler için desteklenmez [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] .

 Daha fazla bilgi için bkz. [Proje ve proje öğesi şablonları ekleme](../../extensibility/internals/adding-project-and-project-item-templates.md).

## <a name="properties-and-options"></a>Özellikler ve Seçenekler
 **Özellikler** penceresi, seçilen tek veya birden çok öğenin özelliklerini görüntüler: [özellikleri genişletme](../../extensibility/internals/extending-properties.md) seçenekleri sayfaları, programlama dili veya VSPackage: [Options ve Options sayfaları](../../extensibility/internals/options-and-options-pages.md)gibi belirli bir bileşene ait seçenek kümelerini içerir. Ayarlar, genel olarak içeri aktarılabilir ve verilebileceğini kullanıcı ARABIRIMI ile ilgili özelliklerdir: [Kullanıcı ayarları Için destek](../../extensibility/internals/support-for-user-settings.md).

## <a name="visual-studio-services"></a>Visual Studio Hizmetleri
 Bir hizmet, bileşenlerin kullanması için belirli bir arabirim kümesi sağlar. Visual Studio, uzantılar da dahil olmak üzere herhangi bir bileşen tarafından kullanılabilen bir hizmet kümesi sağlar. Örneğin, Visual Studio Hizmetleri araç pencerelerini dinamik olarak göstermek veya gizli hale getirmek, yardım, durum çubuğu veya UI olaylarına erişimi etkinleştirir. Visual Studio Düzenleyicisi, Düzenleyici uzantıları tarafından içeri aktarılabilecek hizmetler de sağlar. Daha fazla bilgi için bkz. [Hizmetleri kullanma ve sağlama](../../extensibility/using-and-providing-services.md).

## <a name="debugger"></a>Hata Ayıklayıcısı
 Hata ayıklayıcı dile özgü hata ayıklama bileşenlerinin kullanıcı arabirimidir. Yeni bir dil hizmeti oluşturduysanız, hata ayıklayıcıya bağlamak için belirli bir hata ayıklama altyapısı oluşturmanız gerekir. Daha fazla bilgi için bkz. [Visual Studio hata ayıklayıcı genişletilebilirliği](../../extensibility/debugger/visual-studio-debugger-extensibility.md).

## <a name="source-control"></a>Kaynak Denetimi
 Kaynak denetimi eklentisi veya VSPackage uygulama hakkında daha fazla bilgi için bkz. [kaynak denetimi](../../extensibility/internals/source-control.md).

## <a name="wizards"></a>Sihirbazlar
 Sihirbazın, kullanıcılarınızın bu türden yeni bir proje oluşturduklarında doğru kararlar vermesine yardımcı olması için, yeni bir proje türüyle birlikte bir sihirbaz oluşturabilirsiniz. Daha fazla bilgi için bkz. [Sihirbazlar](../../extensibility/internals/wizards.md).

## <a name="custom-tools"></a>Özel Araçlar
 Özel araçlar, bir aracı projedeki bir öğeyle ilişkilendirmenize ve dosyayı her kaydedildiğinde bu aracı çalıştırmanızı sağlar. Daha fazla bilgi için bkz. [özel araçlar](../../extensibility/internals/custom-tools.md).

## <a name="vssdk-utilities"></a>VSSDK Yardımcı Programları
 VSSDK, VSPackages 'ın farklı yönlerini kullanarak çalışabilmek için ihtiyacınız olabilecek bir yardımcı program kümesi içerir. Daha fazla bilgi için bkz. [VSSDK yardımcı programları](../../extensibility/internals/vssdk-utilities.md).

## <a name="using-windows-installer"></a>Windows Installer kullanma
 Bazı durumlarda, VSıX yükleyicisi yerine Windows Installer kullanmanız gerekebilir: Örneğin, kayıt defterine yazmanız gerekebilir. Uzantılarınız ile Windows Installer kullanma hakkında daha fazla bilgi için, bkz. [Windows Installer Ile VSPackages yükleme](../../extensibility/internals/installing-vspackages-with-windows-installer.md).

## <a name="help-viewer"></a>Yardım Görüntüleyicisi
 Yardım Görüntüleyicisi 'Nde kendi yardım ve F1 sayfalarınızı tümleştirebilirsiniz. Daha fazla bilgi için bkz. [SDK Microsoft Yardım Görüntüleyicisi](../../extensibility/internals/microsoft-help-viewer-sdk.md).
