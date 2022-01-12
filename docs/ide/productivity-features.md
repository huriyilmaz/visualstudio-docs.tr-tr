---
title: Üretkenlik kılavuzu
description: Kod yazmanıza, kodda hata ayıklamanıza ve Visual Studio yardımcı olan klavye kısayolları ve üretkenlik özellikleri hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 4/29/2020
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: d76f4a1f0f004b51fca0b39895839d76376aa9b9
ms.sourcegitcommit: d38d1b083322019663fec7d1d85a4cda456aadca
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2021
ms.locfileid: "135534023"
---
# <a name="productivity-guide-for-visual-studio"></a>Visual Studio için üretkenlik kılavuzu

Kod yazarken zaman kazanmak için doğru yerdesiniz. Bu üretkenlik kılavuzu, tek bir sayfada Visual Studio, kod yazma, kodda hata ayıklama, hataları işleme ve klavye kısayollarını kullanmaya başlamanıza &mdash; yardımcı olacak ipuçları içerir.

Yararlı klavye kısayolları hakkında bilgi için [bkz. Üretkenlik kısayolları.](../ide/productivity-shortcuts.md) Komut kısayollarının tam listesi için bkz. [Varsayılan klavye kısayolları.](../ide/default-keyboard-shortcuts-in-visual-studio.md)

## <a name="get-started"></a>başlarken

Komutlar, ayarlar, belgeler ve yükleme seçenekleri gibi ihtiyacınız olan her şeyi hızla arayarak menülerde zaman kazanmak. Daha kolay ezberlemek için arama sonuçlarınız içindeki Visual Studio klavye kısayollarına bakın. 

- **Görev listesini kullanan sahte kod.** Bir kodu tamamlamak için yeterli gereksinimleriniz yoksa, ve veya özel belirteçleri kullanan kod açıklamalarını izlemek ve sizi doğrudan kodda önceden tanımlanmış bir konuma alan kısayolları yönetmek için Görev Listesi'i `TODO` `HACK` kullanın. Daha fazla bilgi için [bkz. Görev Listesi.](../ide/using-the-task-list.md)

- **kısayollarını Çözüm Gezgini kullanın.** Yeni bir kod Visual Studio yeni bir kod tabanına hız kazanmak için bu kısayollar kullanışlı olacaktır. Kısayolların tam listesi için bkz. [Visual Studio.](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_solutionexplorerGLOBAL)

- **[içinde klavye kısayollarını tanımlama ve Visual Studio.](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)** Visual Studio komutları için kısayollar tanımlayabilir, bu kısayolları özelleştirebilir ve başkalarının kullanması için dışarı aktarabilirsiniz. Seçenekler iletişim kutusunda klavye kısayolunu istediğiniz zaman bulabilir ve değiştirebilirsiniz.

- **Daha Visual Studio hale.** Visual Studio ekran okuyucularla ve diğer yardımcı teknolojilerle uyumlu yerleşik erişilebilirlik özelliklerine sahiptir. Kullanılabilir [özelliklerin tam listesi için Visual Studio](../ide/reference/accessibility-tips-and-tricks.md) ipuçları ve püf noktalarına bakın. 

- **Ürün Yaşam Döngüsü Visual Studio Bakım'a göz at.** Visual Studio güncelleştirmelerini, Enterprise ve Professional müşterileri için destek seçeneklerini, Visual Studio'nin eski sürümlerini ve Visual Studio hizmeti kapsamında yer almayan bileşenleri nasıl alasınız hakkında bilgi için [bkz. Visual Studio  Ürün Yaşam Döngüsü ve Bakım.](/visualstudio/releases/2019/servicing) 

- **Visual Studio'NuGet yükleme ve yönetme.** NuGet Paket Yöneticisi üzerinde Visual Studio kullanıcı arabirimi Windows proje ve çözümlerde paketleri kolayca yüklemenizi, kaldırmanızı ve NuGet güncelleştirmenizi sağlar. Daha fazla bilgi için bkz. NuGet Paket Yöneticisi [kullanarak Visual Studio yükleme ve yönetme.](/nuget/consume-packages/install-use-packages-visual-studio)

## <a name="write-code"></a>Kod yazma

Aşağıdaki özellikleri kullanarak kodu daha hızlı yazın.

- **Kolaylık komutlarını kullanın.** Visual Studio düzenleme görevlerini daha hızlı gerçekleştirmeye yardımcı olacak çeşitli komutlar içerir. Örneğin, bir kod satırı kopyalamak zorunda kalmadan kolayca yinelemek, imleci yeniden konumlandırmak ve ardından yapıştırmak için bir komut seçebilirsiniz. Yineleneni   >  **Düzenle'yi** seçin veya **Ctrl** + **E**,**V tuşlarına basın.** Ayrıca, Gelişmiş Genişletme Seçimini Düzenle veya Gelişmiş Anlaşma Seçimini Düzenle'yi seçerek ya da Shift Alt veya Shift Alt tuşlarına basarak bir metin seçimini hızla genişletebilirsiniz  >    >     >    >    +  + **=** veya  + **daraltmak için** + **-** .

- **IntelliSense kullanın.** Düzenleyiciye kod girerken Liste Üyeleri, Parametre Bilgileri, Hızlı Bilgi, İmza Yardımı ve Tam Sözcük gibi IntelliSense bilgileri görüntülenir. Bu özellikler metinlerin belirsiz eşleşmesini destekler; Örneğin, Liste Üyeleri için sonuç listeleri yalnızca girdiğiniz karakterlerle başlamayı değil, aynı zamanda adlarının herhangi bir yerinde karakter birleşimini içeren girişleri de içerir. Daha fazla bilgi için [bkz. IntelliSense kullanma.](../ide/using-intellisense.md)

- **Kod girerken IntelliSense seçeneklerinin otomatik olarak eklemesini değiştirme.** IntelliSense'i öneri moduna değiştirerek, IntelliSense seçeneklerinin yalnızca açıkça seçerseniz ekli olduğunu belirtebilirsiniz.

     Öneri modunu etkinleştirmek için **Ctrl** Alt Ara Çubuğu tuşlarını seçin veya menü çubuğunda IntelliSense Tamamlama Modunu +  +    >    >  **Düzenle'yi seçin.**

- **Kod parçacıklarını kullanın.** Yerleşik kod parçacıklarını kullanabilir veya kendi kod parçacıklarınızı oluşturabilirsiniz.

     Kod parçacığı eklemek için menü çubuğunda IntelliSense Kod ParçacığıNı Düzenle veya Ile Çevrele'yi seçin ya da kısayol menüsünü bir dosyada açıp Kod Parçacığı Ekleme Kod Parçacığı veya Ile Çevrele'yi  >    >      >   **seçin.** Daha fazla bilgi için [bkz. Kod Parçacıkları.](../ide/code-snippets.md)

- **Satır içi kod hatalarını düzeltin.** Hızlı Eylemler, tek bir eylemle kodu kolayca yeniden düzenlemenizi, oluşturmanizi veya başka bir şekilde değiştirmenizi sağlar. Bu eylemler, tornavida Tornavida simgesi veya ampul Ampul simgesi simgeleri kullanılarak veya Alt Enter veya ![ ](media/screwdriver-icon.png) ![ ](media/light-bulb-icon.png)  +  Ctrl tuşlarına basılarak  + **uygulanabilir.** İmleciniz uygun kod satırına geldiğinde. Daha [fazla bilgi için](quick-actions.md) bkz. Hızlı Eylemler.

- **Kod öğesinin tanımını gösterme ve düzenleme.** Üye, değişken veya yerel gibi bir kod öğesinin tanımlandığı modülü hızlıca gösterebilir ve düzenleyebilirsiniz.

    Açılır pencerede bir tanım açmak için, öğesini vurgulayın, **ardından Alt** F12 tuşlarını seçin veya öğenin kısayol menüsünü açıp Tanıma Göz +  **At'ı seçin.** Bir tanımı ayrı bir kod penceresinde açmak için öğenin kısayol menüsünü açın ve Tanıma **Git'i seçin.**

- **Örnek uygulamaları kullanın.** Microsoft Geliştirici Network'den örnek uygulamaları indirip yükleyerek [uygulama geliştirmeyi hızlandırabilirsiniz.](https://code.msdn.microsoft.com/) Ayrıca belirli bir teknoloji veya programlama kavramını öğrenmek için bu alana yönelik bir Örnek Paketi indirip keşfedersiniz.

- **Biçimlendirme/Yeni Satırlar ile küme ayracı biçimlendirmesini değiştirme.** Yeni **satırlar**  da dahil olmak üzere kod düzenleyicisinde kod biçimlendirme seçeneklerini ayarlamak için Biçimlendirme seçenekleri sayfasını kullanın. C# içinde bu ayarı kullanma hakkında daha fazla bilgi için bkz. Seçenekler iletişim kutusu: Metin Düzenleyici > C# > Kod [Stili > Biçimlendirme.](../ide/reference/options-text-editor-csharp-formatting.md) C++ için [bkz. C++ kodlama tercihlerinizi Visual Studio.](/cpp/ide/how-to-set-preferences) Python için bkz. [Python kodunu biçimlendirme.](../python/formatting-python-code.md)

- **Girintilemenizi Sekmeler ile değiştirme.** Farklı düzenleyicilerde ve IDE'lerde aynı proje üzerinde çalışan birden çok geliştirici için tutarlı kodlama stilleri uygulamak için her kod tabanına uyarlanmış özel düzenleyici ayarlarını kullanın. Tüm takımınız aynı dil kurallarına, adlandırma kurallarına ve biçimlendirme kurallarına uygun olduğundan emin olur. Bu özel ayarlar taşınabilir ve kodunuzla birlikte taşınır, kodlama stillerini uygulamanın dışında bile Visual Studio. Daha fazla bilgi için [bkz. Seçenekler, Metin Düzenleyici, Tüm Diller, Sekmeler.](../ide/reference/options-text-editor-all-languages-tabs.md#tabs)

## <a name="navigate-within-your-code-and-the-ide"></a>Kodunuz ve IDE içinde gezinme

Çeşitli teknikleri kullanarak kodundaki belirli konumları daha hızlı bulabilir ve bu konumlara geçebilirsiniz. Ayrıca, tercihlerinize bağlı olarak Visual Studio pencerenizin düzenini değiştirebilirsiniz. 

- **Kod satırlarını yer işaretlerine ekleyin.** Bir dosyadaki belirli kod satırlarına hızla gitmek için yer işaretlerini kullanabilirsiniz.

    Yer işareti ayarlamak için menü çubuğunda Yer İşaretlerini Düzenle Yer  >  **İşaretlerini**  >  **Değiştir'i seçin.** Bir çözümün tüm yer işaretlerini Yer İşaretleri **penceresinde görüntüebilirsiniz.** Daha fazla bilgi için [bkz. Kodda yer işaretlerini ayarlama.](../ide/setting-bookmarks-in-code.md)

- **bir dosyasında sembol tanımları için arama.** Sembol tanımlarını ve dosya adlarını bulmak için bir çözüm içinde arama yapmak için aramanız gerekir, ancak arama sonuçları ad alanlarını veya yerel değişkenleri içermez.

   Bu özele erişmek için menü çubuğunda Düzenle'yi  >  **seçin.**

- **Kodunuzun genel yapısına göz atma.** Bu **Çözüm Gezgini,** projeleriniz içinde sınıflarda, türleriyle üyelerinde arama ve göz atabilirsiniz. Ayrıca sembolleri arayabilir, bir yöntemin Çağrı Hiyerarşisi'ne bakabilirsiniz, sembol başvurularını bulabilir ve diğer görevleri gerçekleştirebilirsiniz. içinde bir kod öğesi **Çözüm Gezgini,** ilişkili dosya **önizleme** sekmesinde açılır ve imleç dosyasındaki öğeye taşınır. Daha fazla bilgi için [bkz. Kodun yapısını görüntüleme.](../ide/viewing-the-structure-of-code.md)

- **Eşleme moduyla dosyada bir konuma atlayın.** Harita modu, kaydırma çubuğunda kod satırlarını görüntüler. Bu görüntüleme modu hakkında daha fazla bilgi için [bkz. Nasıl 2. Sayfa: Kaydırma çubuğunu özelleştirme.](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md#map-mode)

- **Kod eşlemesi ile kod yapınızı anlama.** Kod eşlemeleri, kodunuz genelinde bağımlılıkları görselleştirmenize ve dosya ve kod satırlarını okumadan nasıl uyum içinde olduğunu görmenize yardımcı olabilir. Daha fazla bilgi için [bkz. Kod eşlemeleri ile bağımlılıkları eşleme.](../modeling/map-dependencies-across-your-solutions.md)

- **Düzenle/Son Dosyaya Git ile sık kullanılan dosyalara bakın.** Belirtilen öğeleri hızla bulumanıza Visual Studio için kodda odaklanmış bir arama gerçekleştirmek için git komutlarını kullanın. Ayrıntılı yönergeler için [bkz. Git komutlarını kullanarak kod bulma.](../ide/go-to.md)

- **Sol [Özellikler penceresi](../ide/reference/properties-window.md) sağ tarafa doğru hareket ettirin.** Daha tanıdık bir pencere düzeni arıyorsanız, F4 tuşuna Özellikler penceresi Visual Studio pencere düzenini **hareket ettirebilirsiniz.**

## <a name="find-items-faster"></a>Öğeleri daha hızlı bulma

Yalnızca geçerli göreviniz için ilgili bilgileri göstermek için araç pencerelerinin içeriğini filtrelemeye ek olarak IDE'de komutlar, dosyalar ve seçenekler için arama yapabilirsiniz.

- **Araç pencerelerinin içeriğini filtrele.** Araç **Kutusu,** Özellikler penceresi ve Çözüm Gezgini gibi birçok araç  penceresinin içeriğinde arama Çözüm Gezgini, ancak yalnızca adları belirttiğiniz karakterleri içeren öğeleri görüntüebilirsiniz.

- **Yalnızca ele almak istediğiniz hataları görüntüler.** Hata Listesi araç **çubuğunda** Filtre **düğmesini seçerseniz,** Hata Listesi penceresinde görünen hata **sayısını azaltabilirsiniz.** Yalnızca düzenleyicide açık olan dosyalarda hataları, yalnızca geçerli dosyada yer alan hataları veya yalnızca geçerli proje hatalarını görüntüebilirsiniz. Belirli hataları bulmak için Hata **Listesi penceresinde** arama da bulabilirsiniz.

- **İletişim kutularını, menü komutlarını, seçenekleri ve daha fazlasını bulun.** Arama kutusuna bulmaya çalıştığın öğeler için anahtar sözcükleri veya tümcecikleri girin. Örneğin, yeni proje girersiniz aşağıdaki **seçenekler görüntülenir:**

   ::: moniker range="vs-2017"

   ![Hızlı Başlat 'yeni proje' için sonuçlar](../ide/media/productivity_quicklaunch.png)

   **Hızlı Başlat** proje oluşturma, projeye yeni öğe ekleme ve Seçenekler iletişim kutusundaki  Projeler ve Çözümler  sayfasındaki bağlantıları görüntüler. Arama sonuçları proje dosyalarını ve araç pencerelerini de içerebilir.

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   !['Yeni proje' için arama sonuçları](../ide/media/vs-2019/productivity-quick-launch-new-project.png)

   ::: moniker-end

   Doğrudan arama kutusuna atlamak için **Ctrl** + **Q** tuşlarına basın.

## <a name="debug-code"></a>Kod hatalarını ayıklama

Hata ayıklama çok zaman tüketir, ancak aşağıdaki ipuçları işlemi hızlandırmak için size yardımcı olabilir.

- **Hata ayıklayıcısı Visual Studio kullanın.** Bu Visual Studio, uygulamanıza *hata* ayıklarken genellikle uygulamayı hata ayıklayıcı modunda çalıştırabilirsiniz. Hata ayıklayıcısı, kodunuzun çalışırken ne yaptığını görmek için birçok yol sağlar. Başlarken [kılavuzu için bkz. Visual Studio](../debugger/debugger-feature-tour.md) Hata Ayıklayıcısı'nda ilk bakış. 

- **Aynı sayfayı, uygulamayı veya siteyi farklı tarayıcılarda test edin.** Kodunuzun hata ayıklaması yapılırken, Birlikte Gözat iletişim kutusunu açmak zorunda kalmadan Sayfa [Denetçisi (Visual Studio)](/previous-versions/hh974728(v=vs.140))dahil olmak üzere yüklü web tarayıcıları **arasında kolayca geçiş** yapabilirsiniz. Hata Ayıklamayı **Başlat** düğmesinin yanındaki Standart  araç çubuğunda  yer alan Hata Ayıklama Hedefi listesini kullanarak, hata ayıklarken veya sayfalarda hata ayıklarken hangi tarayıcıyı kullanmakta olduğunu hızla doğrulayabilirsiniz.

    ![Web tarayıcısı hata ayıklama seçeneklerini belirleyin](../ide/media/webbrowserdropdowntoolbar.png)

- **Geçici kesme noktaları ayarlayın.** Geçerli kod satırına geçici bir kesme noktası oluşturabilir ve hata ayıklayıcıyı aynı anda başlatabilirsiniz. Bu kod satırına isabet edinca hata ayıklayıcı kesme moduna girer. Daha fazla bilgi için [bkz. Hata ayıklayıcı ile kodda gezinme.](../debugger/navigating-through-code-with-the-debugger.md)

    Bu özelliği kullanmak için Ctrl F10 tuşlarını seçin veya üzerinde kesme yapmak istediğiniz kod satırı kısayol menüsünü açın ve ardından **Imleçte** +  **Çalıştır'ı seçin.**

- **Hata ayıklama sırasında yürütme noktasını taşıma.** Geçerli yürütme noktasını kodun farklı bir bölümüne taşımak ve ardından hata ayıklamayı bu noktadan yeniden başlatmak için kullanabilirsiniz. Bu teknik, o bölüme ulaşmak için gereken tüm adımları yeniden oluşturmak zorunda kalmadan kod bölümünün hata ayıklaması yapmak için kullanışlıdır. Daha fazla bilgi için [bkz. Hata ayıklayıcı ile kodda gezinme.](../debugger/navigating-through-code-with-the-debugger.md)

     Yürütme noktasını taşımak için, sarı ok ucu aynı kaynak dosyada sonraki deyimi ayarlamak istediğiniz konuma sürükleyin ve ardından hata ayıklamaya devam etmek için **F5** tuşunu seçin.

- **değişkenleri için değer bilgilerini yakalama.** Hata ayıklama tamam olduktan sonra değişkenin bilinen son değerine erişmek için kodundaki bir değişkene Bir DataTip ekleyebilir ve sabitebilirsiniz. Daha fazla bilgi için [bkz. Veri kaynağında veri İpuçları.](../debugger/view-data-values-in-data-tips-in-the-code-editor.md)

     DataTip eklemek için hata ayıklayıcının kesme modunda olması gerekir. İmleci değişkenin üzerine yerleştirin ve ardından görüntülenen DataTip'in sabitleme düğmesini seçin. Hata ayıklama durdurulurken, kaynak dosyada değişkeni içeren kod çizgisinin yanında mavi bir pin simgesi görünür. Mavi pine işaret ediyorsanız, en son hata ayıklama oturumundan değişkenin değeri görüntülenir.

- **Hemen penceresinin temizlerini açın.** Tasarım zamanında Veya girerek [Hemen penceresinin](../ide/reference/immediate-window.md) içeriğini `>cls` silebilirsiniz `>Edit.ClearAll`

     Ek komutlar hakkında daha fazla bilgi için [bkz. Visual Studio diğer adları.](../ide/reference/visual-studio-command-aliases.md)

- **[CodeLens ile kod değişikliklerini ve diğer geçmişi bulun.](../ide/find-code-changes-and-other-history-with-codelens.md)** CodeLens, düzenleyiciden ayrılmadan kodunuza ne olduğunu bulurken çalışmanıza &mdash; odaklanmanıza olanak sağlar. Bir kod parçasına, kodunuzdaki değişikliklere, bağlantılı hatalara, iş öğelerine, kod incelemelerine ve birim testlerine başvurular bulabilirsiniz.

- **Diğer Live Share gerçek zamanlı olarak hata ayıklamak için hata ayıklamayı kullanın.** Live Share, kullandığınız programlama dillerinden veya oluşturduğunuz uygulama türlerinden bağımsız olarak başkalarıyla gerçek zamanlı işbirliği yaparak kodu düzenlemenize ve hataları ayıklamanıza olanak tanır. Daha fazla bilgi için [bkz. Visual Studio Live Share?](/visualstudio/liveshare/)

- **Küçük kodu yazmak ve test etmek için Etkileşimli Pencere kullanın.** Visual Studio rastgele kod girmenize ve hemen sonuçları görmenize olanak sağlayan etkileşimli bir read-evaluate-print-loop (REPL) penceresi sağlar. Bu kodlama yolu, API'leri ve kitaplıkları öğrenmenize, denemenize ve projelerinize dahil etmek için etkileşimli olarak çalışma kodu geliştirmenize yardımcı olur. Python için [bkz. Python ile çalışma Etkileşimli penceresi.](../python/python-interactive-repl-in-visual-studio.md) Etkileşimli Pencere özelliği C# için de kullanılabilir. 

## <a name="access-visual-studio-tools"></a>Erişim Visual Studio araçları

Bu aracı Geliştirici Komut İstemi veya görev çubuğuna sabitler Visual Studio veya başka bir araç Başlat menüsü erişebilirsiniz.

::: moniker range="vs-2017"

1. Windows Gezgini'nde *%ProgramData%\Microsoft\Windows\Start Menu\Programs\Visual Studio 2017\Visual Studio Araçları*.

::: moniker-end

::: moniker range=">=vs-2019"

1. Windows Gezgini'nde *%ProgramData%\Microsoft\Windows\Start Menu\Programs\Visual Studio 2019\Visual Studio Araçları*.

::: moniker-end

2. Geliştirici Komut İstemi için bağlam menüsüne sağ tıklayın veya açın ve **ardından Başlat'a** Sabitle veya Görev **çubuğuna** **sabitle'yi seçin.**

## <a name="manage-files-toolbars-and-windows"></a>Dosyaları, araç çubuklarını ve pencereleri yönetme

Herhangi bir anda, bir uygulama geliştirirken birden çok kod dosyası üzerinde çalışıyor ve birkaç araç pencereleri arasında taşınıyor olabilir. Aşağıdaki ipuçlarını kullanarak düzenli bir şekilde devam yapabilirsiniz:

- **Sık sık kullanmakta olduğu dosyaları düzenleyicide görünür durumda tutma.** Düzenleyicide kaç dosyanın açık olduğuna bakılmaksızın görünür kalmaları için dosyaları sekmenin sol tarafına sabitleyebilirsiniz.

   Bir dosyayı sabitlemek için dosyanın sekmesini seçin ve ardından Durumu Sabitle **düğmesini** seçin.

- **Belgeleri ve pencereleri diğer izleyicilere taşıma.** Uygulama geliştirirken birden fazla izleyici kullanıyorsanız, düzenleyicide açık olan dosyaları başka bir izleyiciye hareket ettirerek, uygulamanın bölümleri üzerinde daha kolay çalışabilirsiniz. Ayrıca hata ayıklayıcı pencereleri gibi araç pencerelerini başka bir izleyiciye ve sekme dock belgesine ve araç pencerelerini birlikte taşınarak "sallar" oluşturabilirsiniz. Daha fazla bilgi için [bkz. Windows'da pencere düzenlerini Visual Studio.](../ide/customizing-window-layouts-in-visual-studio.md)

   Ayrıca başka bir örnek oluşturarak ve başka bir izleyiciye **Çözüm Gezgini** dosyaları daha kolay yönetebilirsiniz. öğesinin başka bir **Çözüm Gezgini** oluşturmak için, öğesinde bir **kısayol Çözüm Gezgini** açın ve görünümde yeni **Çözüm Gezgini seçin.**

- **içinde görünen yazı tiplerini Visual Studio.** IDE'de metin için kullanılan yazı tipi yüzünü, boyutunu ve rengini değiştirebilirsiniz. Örneğin, düzenleyicide belirli kod öğelerinin rengini, araç pencerelerde veya IDE'nin tamamlarında yazı tipi yüzünü özelleştirebilirsiniz. Daha fazla bilgi için [bkz. Nasıl kullanılır: Yazı tiplerini ve renkleri değiştirme](../ide/how-to-change-fonts-and-colors-in-visual-studio.md) ve [Nasıl kullanılır: Düzenleyicide yazı tiplerini ve renkleri değiştirme.](../ide/reference/how-to-change-fonts-and-colors-in-the-editor.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio ipuçları ve püf noktaları blog gönderisi](https://devblogs.microsoft.com/visualstudio/visual-studio-tips-and-tricks/)
- [Sık kullanılan komutlar için varsayılan klavye kısayolları](default-keyboard-shortcuts-in-visual-studio.md)
- [Nasıl yapabilirsiniz: Menüleri ve araç çubuklarını özelleştirme](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md)
- [Adım adım kılavuz: Basit bir uygulama oluşturma](../get-started/csharp/tutorial-wpf.md)
- [Erişilebilirlik ipuçları ve püf noktaları](../ide/reference/accessibility-tips-and-tricks.md)