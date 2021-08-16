---
title: Üretkenlik Kılavuzu
description: kodu verimli bir şekilde yazmanıza, kodda hata ayıklamanıza ve hataları işlemeye yardımcı olabilecek Visual Studio ' deki klavye kısayolları ve üretkenlik özellikleri hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 4/29/2020
ms.topic: conceptual
author: j-martens
ms.author: jmartens
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: a4666b08d927cc1fe42fbee6d730d55f0f764582eaf5311d7573bc5f8f91239f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121372983"
---
# <a name="productivity-guide-for-visual-studio"></a>Visual Studio için üretkenlik Kılavuzu

Kodu yazarken zaman kazanmak istiyorsanız, doğru yerde olursunuz. bu üretkenlik kılavuzu Visual Studio, kod yazma, hata ayıklama kodu, hataları işleme ve klavye kısayollarını tek bir sayfada kullanma konusunda yardımcı olabilecek ipuçları içerir &mdash; .

Faydalı klavye kısayolları hakkında daha fazla bilgi için bkz. [üretkenlik kısayolları](../ide/productivity-shortcuts.md). Komut kısayollarının tüm listesi için bkz. [varsayılan klavye kısayolları](../ide/default-keyboard-shortcuts-in-visual-studio.md).

## <a name="get-started"></a>başlarken

Komutlar, ayarlar, belgeler ve Install seçenekleri de dahil olmak üzere ihtiyacınız olan her şeyi hızlıca arayarak menüler aracılığıyla zaman ayırarak tasarruf edin. arama sonuçlarınızda bulunan komutlara yönelik klavye kısayollarına bakın Visual Studio, böylece daha kolay bir şekilde daha fazla bilgi alabilirsiniz. 

- **Görev listesini kullanan sahte kod**. Kod parçasını tamamlamaya yetecek kadar gereksinimleriniz yoksa, ve gibi belirteçleri kullanan kod açıklamalarını izlemek için Görev Listesi kullanın `TODO` `HACK` ve sizi doğrudan kodda önceden tanımlanmış bir konuma götürür kısayolları yönetin. Daha fazla bilgi için bkz. [görev listesi kullanma](../ide/using-the-task-list.md).

- **Çözüm Gezgini kısayollarını kullanın**. Visual Studio yeni başladıysanız, bu kısayollar yararlı olur ve yeni bir kod tabanında hızlanırken size zaman kazandırır. Kısayolların tam listesi için, bkz. [Visual Studio varsayılan klavye kısayolları](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_solutionexplorerGLOBAL).

- **[Visual Studio klavye kısayollarını belirleyip özelleştirin](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)**. Visual Studio komutları için kısayollar tanımlayabilir, bu kısayolları özelleştirebilir ve başkalarının kullanması için dışarı aktarabilirsiniz. Seçenekler iletişim kutusunda her zaman bir klavye kısayolunu bulabilir ve değiştirebilirsiniz.

- **Visual Studio daha erişilebilir hale getirin**. Visual Studio, ekran okuyucular ve diğer yardımcı teknolojilerle uyumlu yerleşik erişilebilirlik özelliklerine sahiptir. kullanılabilir özelliklerin tam listesi için bkz. [Visual Studio için erişilebilirlik ipuçları ve püf noktaları](../ide/reference/accessibility-tips-and-tricks.md) . 

- **ürün yaşam döngüsünü ve bakımını Visual Studio** göz atın. Visual Studio güncelleştirmelerini alma hakkında daha fazla bilgi için Enterprise ve Professional müşterilere yönelik destek seçenekleri, Visual Studio daha eski sürümleri ve Visual Studio hizmeti kapsamında bulunmayan bileşenler için bkz. [Visual Studio ürün yaşam döngüsü ve bakımı](/visualstudio/releases/2019/servicing). 

- **Visual Studio NuGet paketlerini yükleyip yönetin**. Windows üzerinde Visual Studio NuGet Paket Yöneticisi kullanıcı arabirimi, projelerinde ve çözümlerinde NuGet paketlerini kolayca yüklemenize, kaldırmanıza ve güncelleştirmenize olanak tanır. daha fazla bilgi için, [NuGet Paket Yöneticisi kullanarak Visual Studio paketleri yükleyip yönetme](/nuget/consume-packages/install-use-packages-visual-studio)konusuna bakın.

## <a name="write-code"></a>Kod yazma

Aşağıdaki özellikleri kullanarak daha hızlı bir şekilde kod yazın.

- **Kullanışlı komutları kullanın**. Visual Studio, yaygın düzenlenen görevleri daha hızlı gerçekleştirmenize yardımcı olacak çeşitli komutlar içerir. Örneğin, bir kod satırını kopyalamak zorunda kalmadan kolayca çoğaltmak için bir komut seçebilirsiniz, imleci yeniden konumlandırabilirsiniz ve yapıştırın. Yinelemeyi **Düzenle**  >   ' yi seçin veya **CTRL** + **E**,**V** tuşlarına basın. Ayrıca   >  ,**Gelişmiş**  >  **Genişlet seçimini** Düzenle veya   >  **Gelişmiş**  >  **sözleşme seçimini** Düzenle ' yi seçerek veya **SHIFT** + **alt** + **=** veya **SHIFT** + **alt** + **-** tuşlarına basarak bir metin seçimini hızlıca genişletebilir veya dağıtabilirsiniz.

- **IntelliSense kullanın**. Düzenleyicide kod girerken, liste üyeleri, parametre bilgileri, hızlı bilgi, Imza yardımı ve tüm kelime gibi IntelliSense bilgileri görüntülenir. Bu özellikler, metnin belirsiz eşleşmesini destekler; Örneğin, liste üyeleri için sonuç listeleri yalnızca girdiğiniz karakterlerle başlayan girişleri değil, aynı zamanda adlarının herhangi bir yerindeki karakter kombinasyonunu içeren girdileri de içerir. Daha fazla bilgi için bkz. [IntelliSense 'ı kullanma](../ide/using-intellisense.md).

- **Kod girerken IntelliSense seçeneklerinin otomatik olarak eklenmesini değiştirin**. IntelliSense 'i öneri moduna geçirerek, IntelliSense seçeneklerinin yalnızca açıkça seçtiğiniz durumlarda ekleneceğini belirtebilirsiniz.

     Öneri modunu etkinleştirmek için **CTRL** + **alt** + **Ara çubuğu** tuşlarını seçin veya menü çubuğunda IntelliSense **Düzenle**  >    >  **tamamlama modunu** seçin.

- **Kod parçacıklarını kullanın**. Yerleşik kod parçacıklarını kullanabilir veya kendi kod parçacıklarınızı oluşturabilirsiniz.

     Bir kod parçacığı eklemek için, menü çubuğunda IntelliSense **düzenleme**  >    >  **kod parçacığı Ekle** veya **ile Çevrele**' yi seçin veya kısayol menüsünü bir dosyada açın ve **kod parçacığı**  >  **Ekle parçacık** veya **ile çevreleyin**' i seçin. Daha fazla bilgi için bkz. [kod parçacıkları](../ide/code-snippets.md).

- **Kod hatalarını satır Içinde düzeltir**. Hızlı Eylemler, tek bir eylem ile kodu kolayca yeniden düzenleme, oluşturma veya başka şekilde değiştirmenize olanak sağlar. Bu eylemler, Screwdriver ![ screwsürücü simgesi ](media/screwdriver-icon.png) veya hafif Ampul ampul ![ simgesi ](media/light-bulb-icon.png) simgeleri kullanılarak veya **alt** + **ENTER** ya da **CTRL** tuşlarına basarak uygulanabilir + **.** imlecinizin uygun kod satırında olması durumunda. Daha fazla bilgi için bkz. [hızlı eylemler](quick-actions.md) .

- **Bir kod öğesinin tanımını görüntüleyin ve düzenleyin**. Üye, değişken veya yerel gibi bir kod öğesinin tanımlandığı modülü hızlıca gösterebilir ve düzenleyebilirsiniz.

    Bir tanımı açılır pencerede açmak için, öğeyi vurgulayın, sonra **alt** + **F12** tuşlarını seçin veya öğe için kısayol menüsünü açın ve ardından **Gözat**' ı seçin. Ayrı bir kod penceresinde bir tanımı açmak için, öğe için kısayol menüsünü açın ve ardından **Tanıma Git**' i seçin.

- **Örnek uygulamaları kullanın**. [Microsoft Developer Network](https://code.msdn.microsoft.com/)'ten örnek uygulamalar indirerek ve yükleyerek uygulama geliştirmeyi hızlandırabilirsiniz. Ayrıca, bu alana yönelik bir örnek paketi indirerek ve inceleyerek belirli bir teknoloji veya programlama kavramı de öğrenebilirsiniz.

- **Biçimlendirme/yeni satırlarla küme ayracı biçimlendirmesini değiştirin**. Yeni satırlar dahil olmak üzere kod düzenleyicisinde biçimlendirme kodu seçeneklerini ayarlamak için **biçimlendirme**  seçenekleri sayfasını kullanın. Bu ayarın C# ' de nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [Seçenekler iletişim kutusu: metin düzenleyici > C# > kod stili > biçimlendirme](../ide/reference/options-text-editor-csharp-formatting.md). C++ için bkz. [Visual Studio c++ kodlama tercihlerinizi ayarlama](/cpp/ide/how-to-set-preferences). Python için bkz. [Python kodunu biçimlendirme](../python/formatting-python-code.md).

- **Girintilerinizi sekmelerle değiştirin**. Farklı düzenleyicilerde ve sdes 'lerde aynı projede çalışan birden çok geliştirici için tutarlı kodlama stillerini zorlamak üzere her kod tabanına uyarlanmış özel düzenleyici ayarlarını kullanın. Tüm takımınızın aynı dil kurallarına, adlandırma kurallarına ve biçimlendirme kurallarına uyduğundan emin olun. Bu özel ayarlar taşınabilir olduğundan ve kodunuzla birlikte gezindiğinden, Visual Studio dışında bile kodlama stillerini zorunlu kılabilirsiniz. Daha fazla bilgi için bkz. [Seçenekler, metin düzenleyici, tüm diller, sekmeler](../ide/reference/options-text-editor-all-languages-tabs.md#tabs).

## <a name="navigate-within-your-code-and-the-ide"></a>Kodunuzda ve IDE 'de gezinme

Kodunuzda belirli konumları daha hızlı bir şekilde bulmak ve taşımak için çeşitli teknikler kullanabilirsiniz. tercihlerinize göre Visual Studio pencerelerinin yerleşimini de değiştirebilirsiniz. 

- **Kod satırları yer işareti**. Bir dosyadaki belirli kod satırlarına hızlıca gezinmek için yer işaretlerini kullanabilirsiniz.

    Bir yer işareti ayarlamak için, menü çubuğunda   >  **yer imlerini** Düzenle yer işaretlerini Seç  >  **yer işaretini** seçin. Bir çözümün tüm yer imlerini **yer işaretleri** penceresinde görüntüleyebilirsiniz. Daha fazla bilgi için bkz. [koddaki yer Imlerini ayarlama](../ide/setting-bookmarks-in-code.md).

- **Bir dosyada sembol tanımlarını arayın**. Sembol tanımlarını ve dosya adlarını bulmak için bir çözüm içinde arama yapabilirsiniz, ancak arama sonuçları ad alanları veya yerel değişkenler içermez.

   Bu özelliğe erişmek için, menü çubuğunda,   >  **Git 'e git**' i seçin.

- **Kodunuzun genel yapısına gözatın**. **Çözüm Gezgini**, Koleksiyonlarınızda sınıfları ve bunların türlerini ve üyelerini arayabilir ve bunlara gözatabilirler. Ayrıca sembolleri arayabilir, yöntemin Çağrı hiyerarşisini görüntüleyebilir, sembol başvurularını bulabilir ve diğer görevleri gerçekleştirebilirsiniz. **Çözüm Gezgini** bir kod öğesi seçerseniz, ilişkili dosya bir **Önizleme** sekmesinde açılır ve imleç dosyadaki öğeye gider. Daha fazla bilgi için bkz. [kod yapısını görüntüleme](../ide/viewing-the-structure-of-code.md).

- **Eşleme modundaki bir dosyadaki konuma atlayın**. Harita modu, kod satırlarını, kaydırma çubuğunda küçük olarak görüntüler. Bu görüntü modu hakkında daha fazla bilgi için bkz. [nasıl yapılır: kaydırma çubuğunu özelleştirme](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md#map-mode).

- Kod **eşlemesiyle kod yapınızı anlayın**. Kod haritaları kodunuzda bağımlılıkları görselleştirmenize yardımcı olabilir ve dosya ve kod satırları arasında okuma yapmadan nasıl sığdığını görürsünüz. Daha fazla bilgi için bkz. [kod eşlemeleriyle harita bağımlılıkları](../modeling/map-dependencies-across-your-solutions.md).

- **En son dosyayı Düzenle/git ile sık kullanılan dosyalara bakın**. belirtilen öğeleri hızlı bir şekilde bulmanıza yardımcı olması için kodunuzda odaklanmış bir arama gerçekleştirmek üzere Visual Studio içindeki komutlara git ' i kullanın. Ayrıntılı yönergeler için bkz. [Go komutunu kullanarak kodu bulma](../ide/go-to.md).

- **[Özellikler penceresi](../ide/reference/properties-window.md) sağ tarafa taşıyın**. daha tanıdık bir pencere düzeni arıyorsanız **F4** tuşuna basarak Visual Studio Özellikler penceresi taşıyabilirsiniz.

## <a name="find-items-faster"></a>Öğeleri daha hızlı bulun

Araç pencerelerinin içeriğini yalnızca geçerli göreviniz için ilgili bilgileri gösterecek şekilde filtrelemeye ek olarak komutlar, dosyalar ve seçenekler için IDE genelinde arama yapabilirsiniz.

- **Araç pencerelerinin Içeriğini filtreleyin**. **Araç kutusu**, **özellikler** penceresi ve **Çözüm Gezgini** gibi birçok araç penceresinin içeriği içinde arama yapabilirsiniz ancak yalnızca adları belirttiğiniz karakterleri içeren öğeleri görüntüleyebilirsiniz.

- **Yalnızca ele almak istediğiniz hataları görüntüleyin**. **Hata listesi** araç çubuğunda **filtre** düğmesini seçerseniz, **hata listesi** penceresinde görüntülenen hata sayısını azaltabilirsiniz. Yalnızca düzenleyicide açık olan dosyalarda hataları, yalnızca geçerli dosyada yer alan hataları veya yalnızca geçerli proje hatalarını görüntüebilirsiniz. Belirli hataları bulmak için Hata **Listesi penceresinde** arama da bulabilirsiniz.

- **İletişim kutularını, menü komutlarını, seçenekleri ve daha fazlasını bulun.** Arama kutusuna bulmaya çalıştığın öğeler için anahtar sözcükleri veya tümcecikleri girin. Örneğin, yeni proje girersiniz aşağıdaki **seçenekler görüntülenir:**

   ::: moniker range="vs-2017"

   ![Hızlı Başlat 'yeni proje' için sonuçlar](../ide/media/productivity_quicklaunch.png)

   **Hızlı Başlat** proje oluşturma, projeye yeni öğe ekleme ve Seçenekler iletişim kutusundaki Projeler  ve Çözümler sayfasındaki bağlantıları görüntüler.  Arama sonuçları proje dosyalarını ve araç pencerelerini de içerebilir.

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   !['Yeni proje' için arama sonuçları](../ide/media/vs-2019/productivity-quick-launch-new-project.png)

   ::: moniker-end

   Doğrudan arama kutusuna atlamak için **Ctrl** + **Q** tuşlarına basın.

## <a name="debug-code"></a>Kod hatalarını ayıklama

Hata ayıklama çok zaman tüketir, ancak aşağıdaki ipuçları işlemi hızlandırmak için size yardımcı olabilir.

- **Hata ayıklayıcısı Visual Studio kullanın.** Bu Visual Studio, uygulamanıza *hata* ayıklarken genellikle uygulamayı hata ayıklayıcı modunda çalıştırabilirsiniz. Hata ayıklayıcısı, kodunuzun çalışırken ne yaptığını görmek için birçok yol sağlar. Başlarken [kılavuzu için bkz. Visual Studio](../debugger/debugger-feature-tour.md) Hata Ayıklayıcısı'nda ilk bakış. 

- **Aynı sayfayı, uygulamayı veya siteyi farklı tarayıcılarda test edin.** Kodunuzun hata ayıklaması yapılırken, Birlikte Gözat iletişim kutusunu açmak zorunda kalmadan Sayfa [Denetçisi (Visual Studio)](/previous-versions/hh974728(v=vs.140))dahil olmak üzere yüklü web tarayıcıları **arasında kolayca** geçiş yapabilirsiniz. Hata Ayıklamayı **Başlat** düğmesinin yanındaki Standart  araç çubuğundaki  Hata Ayıklama Hedefi listesini kullanarak hata ayıklarken veya sayfalarda hata ayıklarken hangi tarayıcıyı kullanmakta olduğunu hızla doğrulayabilirsiniz.

    ![Web tarayıcısı hata ayıklama seçeneklerini belirleyin](../ide/media/webbrowserdropdowntoolbar.png)

- **Geçici kesme noktaları ayarlayın.** Geçerli kod satırına geçici bir kesme noktası oluşturabilir ve hata ayıklayıcıyı aynı anda başlatabilirsiniz. Bu kod satırına isabet edinca hata ayıklayıcı kesme moduna girer. Daha fazla bilgi için [bkz. Hata ayıklayıcı ile kodda gezinme.](../debugger/navigating-through-code-with-the-debugger.md)

    Bu özelliği kullanmak için Ctrl F10 tuşlarını seçin veya üzerinde kesme yapmak istediğiniz kod satırı kısayol menüsünü açın ve ardından **Imleçte** +  **Çalıştır'ı seçin.**

- **Hata ayıklama sırasında yürütme noktasını taşıma.** Geçerli yürütme noktasını kodun farklı bir bölümüne taşımak ve ardından hata ayıklamayı bu noktadan yeniden başlatmak için kullanabilirsiniz. Bu teknik, o bölüme ulaşmak için gereken tüm adımları yeniden oluşturmak zorunda kalmadan kod bölümünün hata ayıklaması yapmak için kullanışlıdır. Daha fazla bilgi için [bkz. Hata ayıklayıcı ile kodda gezinme.](../debugger/navigating-through-code-with-the-debugger.md)

     Yürütme noktasını taşımak için, sarı ok ucu aynı kaynak dosyada sonraki deyimi ayarlamak istediğiniz konuma sürükleyin ve ardından hata ayıklamaya devam etmek için **F5** tuşunu seçin.

- **değişkenleri için değer bilgilerini yakalama.** Hata ayıklama tamam olduktan sonra değişkenin bilinen son değerine erişmek için kodundaki bir değişkene Bir DataTip ekleyebilir ve sabitebilirsiniz. Daha fazla bilgi için [bkz. Veri kaynağında veri İpuçları.](../debugger/view-data-values-in-data-tips-in-the-code-editor.md)

     DataTip eklemek için hata ayıklayıcının kesme modunda olması gerekir. İmleci değişkenin üzerine yerleştirin ve ardından görüntülenen DataTip'in sabitleme düğmesini seçin. Hata ayıklama durdurulurken, kaynak dosyada değişkeni içeren kod çizgisinin yanında mavi bir sabitleme simgesi görünür. Mavi pine işaret ediyorsanız, en son hata ayıklama oturumundan değişkenin değeri görüntülenir.

- **Hemen penceresinin temizlerini açın.** Tasarım zamanında Veya girerek [Hemen penceresinin](../ide/reference/immediate-window.md) içeriğini `>cls` silebilirsiniz `>Edit.ClearAll`

     Ek komutlar hakkında daha fazla bilgi için [bkz. Visual Studio diğer adları.](../ide/reference/visual-studio-command-aliases.md)

- **[CodeLens ile kod değişikliklerini ve diğer geçmişi bulun.](../ide/find-code-changes-and-other-history-with-codelens.md)** CodeLens, düzenleyiciden ayrılmadan kodunuza ne olduğunu bulurken çalışmanıza &mdash; odaklanmanıza olanak sağlar. Bir kod parçasına, kodunuzdaki değişikliklere, bağlantılı hatalara, iş öğelerine, kod incelemelerine ve birim testlerine başvurular bulabilirsiniz.

- **Diğer Live Share gerçek zamanlı olarak hata ayıklamak için Live Share kullanın.** Live Share, kullandığınız programlama dillerinden veya oluşturduğunuz uygulama türlerinden bağımsız olarak başkalarıyla gerçek zamanlı işbirliği yaparak kodu düzenlemenize ve hataları ayıklamanıza olanak tanır. Daha fazla bilgi için [bkz. Visual Studio Live Share?](/visualstudio/liveshare/)

- **Küçük kodu yazmak ve test etmek için Etkileşimli Pencere kullanın.** Visual Studio rastgele kod girmenize ve hemen sonuçları görmenize olanak sağlayan etkileşimli bir read-evaluate-print-loop (REPL) penceresi sağlar. Bu kodlama yolu, API'leri ve kitaplıkları öğrenmenize, denemenize ve projelerinize dahil etmek için etkileşimli olarak çalışma kodu geliştirmenize yardımcı olur. Python için [bkz. Python ile çalışma Etkileşimli penceresi.](../python/python-interactive-repl-in-visual-studio.md) Etkileşimli Pencere özelliği C# için de kullanılabilir. 

## <a name="access-visual-studio-tools"></a>Erişim Visual Studio araçları

Bu aracı Geliştirici Komut İstemi veya görev çubuğuna sabitler Visual Studio veya başka bir Başlat menüsü erişebilirsiniz.

::: moniker range="vs-2017"

1. Windows Gezgini'nde *%ProgramData%\Microsoft\Windows\Start Menu\Programs\Visual Studio 2017\Visual Studio Araçları .*

::: moniker-end

::: moniker range=">=vs-2019"

1. Windows Gezgini'nde *%ProgramData%\Microsoft\Windows\Start Menu\Programs\Visual Studio 2019\Visual Studio Araçları*.

::: moniker-end

2. öğesinin bağlam menüsüne sağ tıklayın veya Geliştirici Komut İstemi  ve ardından **Başlat'a** Sabitle veya Görev çubuğuna **sabitle'yi seçin.**

## <a name="manage-files-toolbars-and-windows"></a>Dosyaları, araç çubuklarını ve pencereleri yönetme

Herhangi bir anda, bir uygulama geliştirirken birden çok kod dosyası üzerinde çalışıyor ve birkaç araç pencereleri arasında taşınıyor olabilir. Aşağıdaki ipuçlarını kullanarak düzenli bir şekilde devam yapabilirsiniz:

- **Sık sık kullanmakta olduğu dosyaları düzenleyicide görünür durumda tutma.** Düzenleyicide kaç dosyanın açık olduğuna bakılmaksızın görünür kalmaları için dosyaları sekmenin sol tarafına sabitleyebilirsiniz.

   Bir dosyayı sabitlemek için dosyanın sekmesini seçin ve ardından Durumu Sabitle **düğmesini** seçin.

- **Belgeleri ve pencereleri diğer izleyicilere taşıma.** Uygulama geliştirirken birden fazla izleyici kullanıyorsanız, düzenleyicide açık olan dosyaları başka bir izleyiciye hareket ettirerek, uygulamanın bölümleri üzerinde daha kolay çalışabilirsiniz. Ayrıca hata ayıklayıcı pencereleri gibi araç pencerelerini başka bir izleyiciye ve sekme dock belgesine ve araç pencerelerini birlikte taşınarak "sallar" oluşturabilirsiniz. Daha fazla bilgi için [bkz. Windows'da pencere düzenlerini Visual Studio.](../ide/customizing-window-layouts-in-visual-studio.md)

   Ayrıca başka bir örnek oluşturarak ve başka bir izleyiciye **Çözüm Gezgini** dosyaları daha kolay yönetebilirsiniz. öğesinin başka bir **Çözüm Gezgini** oluşturmak için, öğesinde bir **kısayol Çözüm Gezgini** açın ve Görünüm'Çözüm Gezgini **seçin.**

- **içinde görünen yazı tiplerini Visual Studio.** IDE'de metin için kullanılan yazı tipi yüzünü, boyutunu ve rengini değiştirebilirsiniz. Örneğin, düzenleyicide belirli kod öğelerinin rengini, araç pencerelerde veya IDE'nin tamamlarında yazı tipi yüzünü özelleştirebilirsiniz. Daha fazla bilgi için [bkz. Nasıl kullanılır: Yazı tiplerini ve renkleri değiştirme](../ide/how-to-change-fonts-and-colors-in-visual-studio.md) ve [Nasıl kullanılır: Düzenleyicide yazı tiplerini ve renkleri değiştirme.](../ide/reference/how-to-change-fonts-and-colors-in-the-editor.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio ipuçları ve püf noktaları blog gönderisi](https://devblogs.microsoft.com/visualstudio/visual-studio-tips-and-tricks/)
- [Sık kullanılan komutlar için varsayılan klavye kısayolları](../ide/default-keyboard-shortcuts-for-frequently-used-commands-in-visual-studio.md)
- [Nasıl yapabilirsiniz: Menüleri ve araç çubuklarını özelleştirme](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md)
- [Adım adım kılavuz: Basit bir uygulama oluşturma](../get-started/csharp/tutorial-wpf.md)
- [Erişilebilirlik ipuçları ve püf noktaları](../ide/reference/accessibility-tips-and-tricks.md)