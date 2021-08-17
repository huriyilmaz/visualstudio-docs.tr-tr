---
title: Üretkenlik kılavuzu
description: Kod yazmanıza, kod hatalarını ayıklamanıza ve hataları işlemeye Visual Studio klavye kısayolları ve üretkenlik özellikleri hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 4/29/2020
ms.topic: conceptual
author: j-martens
ms.author: jmartens
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 42316256751a61b468198eb09472fe4c8c24f280
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122062465"
---
# <a name="productivity-guide-for-visual-studio"></a>Visual Studio için üretkenlik kılavuzu

Kod yazarken zaman kazanmak için doğru yerdesiniz. Bu üretkenlik kılavuzu, tek bir sayfada Visual Studio, kod yazma, kodda hata ayıklama, hataları işleme ve klavye kısayollarını kullanmaya başlamanıza &mdash; yardımcı olacak ipuçları içerir.

Yararlı klavye kısayolları hakkında bilgi için [bkz. Üretkenlik kısayolları.](../ide/productivity-shortcuts.md) Komut kısayollarının tam listesi için bkz. [Varsayılan klavye kısayolları.](../ide/default-keyboard-shortcuts-in-visual-studio.md)

## <a name="get-started"></a>başlarken

Komutlar, ayarlar, belgeler ve yükleme seçenekleri gibi ihtiyacınız olan her şeyi hızla arayarak menülerde zaman kazanmak. Daha kolay ezberlemek için arama sonuçlarınız içindeki Visual Studio klavye kısayollarına bakın. 

- **Görev listesini kullanan sahte kod.** Bir kod parçasını tamamlamak için yeterli gereksinimleriniz yoksa, Görev Listesi gibi belirteçleri veya özel belirteçleri kullanan kod açıklamalarını izlemek ve sizi doğrudan kodda önceden tanımlanmış bir konuma alan kısayolları yönetmek için Görev Listesi `TODO` `HACK` kullanın. Daha fazla bilgi için [bkz. Görev Listesi.](../ide/using-the-task-list.md)

- **kısayollarını Çözüm Gezgini kullanın.** Yeni bir kod Visual Studio yeni bir kod tabanına hız kazanmak için bu kısayollar kullanışlı olacaktır. Kısayolların tam listesi için [bkz. Visual Studio.](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_solutionexplorerGLOBAL)

- **[içinde klavye kısayollarını tanımlama ve Visual Studio.](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)** Visual Studio komutları için kısayollar tanımlayabilir, bu kısayolları özelleştirebilir ve başkalarının kullanması için dışarı aktarabilirsiniz. Seçenekler iletişim kutusunda klavye kısayolunu istediğiniz zaman bulabilir ve değiştirebilirsiniz.

- **Daha Visual Studio hale.** Visual Studio ekran okuyucularla ve diğer yardımcı teknolojilerle uyumlu yerleşik erişilebilirlik özelliklerine sahiptir. Kullanılabilir [özelliklerin tam listesi için Visual Studio](../ide/reference/accessibility-tips-and-tricks.md) ipuçları ve püf noktalarına bakın. 

- **Ürün Yaşam Döngüsü Visual Studio Bakım'a göz at.** Visual Studio güncelleştirmelerini, Enterprise ve Professional müşterileri için destek seçeneklerini, Visual Studio'nin eski sürümlerini ve Visual Studio hizmeti kapsamında yer almayan bileşenlerin nasıl alın hakkında bilgi için bkz. [Visual Studio Ürün](/visualstudio/releases/2019/servicing)Yaşam Döngüsü ve Bakım. 

- **Visual Studio'NuGet yükleme ve yönetme.** NuGet Paket Yöneticisi üzerinde Visual Studio kullanıcı arabirimi Windows proje ve çözümlerde paketleri kolayca yüklemenizi, kaldırmanızı ve NuGet güncelleştirmenizi sağlar. Daha fazla bilgi için bkz. Visual Studio [kullanarak NuGet Paket Yöneticisi.](/nuget/consume-packages/install-use-packages-visual-studio)

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

- **Örnek uygulamaları kullanın.** Microsoft Geliştirici Network'den örnek uygulamaları indirip [yükleyerek uygulama geliştirmeyi hızlandırabilirsiniz.](https://code.msdn.microsoft.com/) Ayrıca belirli bir teknoloji veya programlama kavramını öğrenmek için bu alana yönelik bir Örnek Paketi indirip keşfedersiniz.

- **Biçimlendirme/Yeni Satırlar ile küme ayracı biçimlendirmesini değiştirme.** Yeni **satırlar**  da dahil olmak üzere kod düzenleyicisinde kod biçimlendirme seçeneklerini ayarlamak için Biçimlendirme seçenekleri sayfasını kullanın. C# içinde bu ayarı kullanma hakkında daha fazla bilgi için bkz. Seçenekler iletişim kutusu: Metin Düzenleyici [> C# > Kod Stili > Biçimlendirme.](../ide/reference/options-text-editor-csharp-formatting.md) C++ için [bkz. C++ kodlama tercihlerinizi Visual Studio.](/cpp/ide/how-to-set-preferences) Python için bkz. [Python kodunu biçimlendirme.](../python/formatting-python-code.md)

- **Girintilemenizi Sekmeler ile değiştirme.** Farklı düzenleyicilerde ve IDE'lerde aynı proje üzerinde çalışan birden çok geliştirici için tutarlı kodlama stilleri uygulamak için her kod tabanına uyarlanmış özel düzenleyici ayarlarını kullanın. Tüm takımınız aynı dil kurallarına, adlandırma kurallarına ve biçimlendirme kurallarına uygun olduğundan emin olur. Bu özel ayarlar taşınabilir ve kodunuzla birlikte ilerlene bir uygulama olduğu için kod stillerini uygulamanın dışında bile Visual Studio. Daha fazla bilgi için [bkz. Seçenekler, Metin Düzenleyici, Tüm Diller, Sekmeler.](../ide/reference/options-text-editor-all-languages-tabs.md#tabs)

## <a name="navigate-within-your-code-and-the-ide"></a>Kodunuz ve IDE içinde gezinme

Çeşitli teknikleri kullanarak kodundaki belirli konumları daha hızlı bulabilir ve bu konumlara geçebilirsiniz. Ayrıca, tercihlerinize bağlı olarak Visual Studio pencerenizin düzenini değiştirebilirsiniz. 

- **Kod satırlarını yer işaretlerine ekleyin.** Bir dosyadaki belirli kod satırlarına hızla gitmek için yer işaretlerini kullanabilirsiniz.

    Yer işareti ayarlamak için menü çubuğunda Yer İşaretlerini Düzenle Yer  >  **İşaretlerini**  >  **Değiştir'i seçin.** Bir çözümün tüm yer işaretlerini Yer İşaretleri **penceresinde görüntüebilirsiniz.** Daha fazla bilgi için [bkz. Kodda yer işaretlerini ayarlama.](../ide/setting-bookmarks-in-code.md)

- **bir dosyasında sembol tanımları için arama.** Sembol tanımlarını ve dosya adlarını bulmak için bir çözüm içinde arama yapmak için aramanız gerekir, ancak arama sonuçları ad alanlarını veya yerel değişkenleri içermez.

   Bu özele erişmek için menü çubuğunda Düzenle'yi  >  **seçin.**

- **Kodunuzun genel yapısına göz atma.** Bu **Çözüm Gezgini** projelerinde sınıflarda, türleriyle üyelerinde arama ve göz atabilirsiniz. Ayrıca sembolleri arayabilir, bir yöntemin Çağrı Hiyerarşisi'ne bakabilirsiniz, sembol başvurularını bulabilir ve diğer görevleri gerçekleştirebilirsiniz. içinde bir kod öğesi **Çözüm Gezgini,** ilişkili dosya **önizleme** sekmesinde açılır ve imleç dosyasındaki öğeye taşınır. Daha fazla bilgi için [bkz. Kodun yapısını görüntüleme.](../ide/viewing-the-structure-of-code.md)

- **Eşleme moduyla dosyada bir konuma atlayın.** Harita modu, kaydırma çubuğunda kod satırlarını görüntüler. Bu görüntüleme modu hakkında daha fazla bilgi için [bkz. Nasıl 2. Sayfa: Kaydırma çubuğunu özelleştirme.](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md#map-mode)

- **Kod eşlemesi ile kod yapınızı anlama.** Kod eşlemeleri, kodunuz genelinde bağımlılıkları görselleştirmenize ve dosya ve kod satırlarını okumadan nasıl uyum içinde olduğunu görmenize yardımcı olabilir. Daha fazla bilgi için [bkz. Kod eşlemeleri ile bağımlılıkları eşleme.](../modeling/map-dependencies-across-your-solutions.md)

- **Düzenle/Son Dosyaya Git ile sık kullanılan dosyalara bakın.** Belirtilen öğeleri hızla bulumanıza Visual Studio için kodda odaklanmış bir arama gerçekleştirmek için git komutlarını kullanın. Ayrıntılı yönergeler için [bkz. Git komutlarını kullanarak kod bulma.](../ide/go-to.md)

- **Sol [Özellikler penceresi](../ide/reference/properties-window.md) sağ tarafa doğru hareket ettirin.** Daha tanıdık bir pencere düzeni arıyorsanız, F4 tuşuna basarak Özellikler penceresi **Visual Studio'yi hareket ettirebilirsiniz.**

## <a name="find-items-faster"></a>Öğeleri daha hızlı bulma

Yalnızca geçerli göreviniz için ilgili bilgileri göstermek için araç pencerelerinin içeriğini filtrelemeye ek olarak IDE'de komutlar, dosyalar ve seçenekler için arama yapabilirsiniz.

- **Araç pencerelerinin içeriğini filtrele.** Araç **Kutusu,** Özellikler penceresi ve Çözüm Gezgini gibi birçok araç  penceresinin içeriğinde arama Çözüm Gezgini, ancak yalnızca adları belirttiğiniz karakterleri içeren öğeleri görüntüebilirsiniz.

- **Yalnızca ele almak istediğiniz hataları görüntüler.** Hata Listesi araç **çubuğunda** Filtre **düğmesini seçerseniz,** Hata Listesi penceresinde görünen hata **sayısını azaltabilirsiniz.** Yalnızca düzenleyicide açık olan dosyalardaki hataları, yalnızca geçerli dosyadaki hataları veya yalnızca geçerli projedeki hataları görüntüleyebilirsiniz. Ayrıca, belirli hataları bulmak için **hata listesi** penceresi içinde arama yapabilirsiniz.

- **İletişim kutularını, menü komutlarını, seçenekleri ve daha fazlasını bulun**. Arama kutusuna bulmaya çalıştığınız öğeler için anahtar sözcükler veya ifadeler girin. Örneğin, **Yeni proje** girdiğinizde aşağıdaki seçenekler görüntülenir:

   ::: moniker range="vs-2017"

   ![' Yeni proje ' için hızlı başlatma sonuçları](../ide/media/productivity_quicklaunch.png)

   **Hızlı başlatma** , yeni bir proje oluşturmak, projeye yeni bir öğe eklemek ve **Seçenekler** Iletişim kutusundaki **Projeler ve çözümler** sayfasına diğerleri arasında bağlantılar görüntüler. Arama sonuçları, proje dosyalarını ve araç pencerelerini de içerebilir.

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![' Yeni proje ' için arama sonuçları](../ide/media/vs-2019/productivity-quick-launch-new-project.png)

   ::: moniker-end

    + Doğrudan arama kutusuna gitmek için CTRL **Q** tuşlarına basın.

## <a name="debug-code"></a>Kod hatalarını ayıklama

Hata ayıklama çok fazla zaman alabilir, ancak aşağıdaki ipuçları süreci hızlandırabilmeniz için size yardımcı olabilir.

- **Visual Studio hata ayıklayıcı araçları kullanın**. Visual Studio bağlamında, uygulamanızda *hata ayıklarken*, genellikle uygulamayı hata ayıklayıcı modunda çalıştırdığınız anlamına gelir. Hata ayıklayıcı, çalışma sırasında kodunuzun ne yaptığını görmek için birçok yol sunar. başlamak için bir kılavuz için [Visual Studio hata ayıklayıcıya](../debugger/debugger-feature-tour.md) bakın. 

- **Aynı sayfayı, uygulamayı veya siteyi farklı tarayıcılarda test edin**. kodunuzun hatalarını ayıkladığınızda, [sayfa denetçisi (Visual Studio)](/previous-versions/hh974728(v=vs.140))dahil olmak üzere yüklü web tarayıcıları arasında kolayca geçiş **yapabilirsiniz iletişim kutusunu** açmaya gerek kalmadan. Hata ayıklama **Başlat** düğmesinin yanındaki **Standart** araç çubuğunda bulunan **hata ayıklama hedefi** listesini kullanabilirsiniz. Bu işlem, hata ayıklama veya sayfaları görüntüleme olarak hangi tarayıcıyı kullandığınızı hızlıca doğrulamak için kullanılır.

    ![Web tarayıcısı hata ayıklama seçeneklerini belirleyin](../ide/media/webbrowserdropdowntoolbar.png)

- **Geçici kesme noktaları ayarlayın**. Geçerli kod satırında geçici bir kesme noktası oluşturabilir ve hata ayıklayıcıyı eşzamanlı olarak başlatabilirsiniz. Bu kod satırını vurduktan sonra, hata ayıklayıcı kesme moduna girer. Daha fazla bilgi için bkz. [hata ayıklayıcıyla kod Içinde gezinme](../debugger/navigating-through-code-with-the-debugger.md).

    Bu özelliği kullanmak için **CTRL** + **F10** tuşlarını seçin veya kesmek istediğiniz kod satırı için kısayol menüsünü açın ve ardından **imlece Çalıştır**' ı seçin.

- **Hata ayıklama sırasında yürütme noktasını taşıyın**. Geçerli yürütme noktasını kodun farklı bir bölümüne taşıyabilir ve sonra bu noktadan hata ayıklamayı yeniden başlatabilirsiniz. Bu teknik, bu bölüme ulaşmak için gereken adımların tümünü yeniden oluşturmak zorunda kalmadan kod bölümünün hatalarını ayıklamak istiyorsanız kullanışlıdır. Daha fazla bilgi için bkz. [hata ayıklayıcıyla kod Içinde gezinme](../debugger/navigating-through-code-with-the-debugger.md).

     Yürütme noktasını taşımak için, sarı ok ucunu aynı kaynak dosyasında bir sonraki ifadeyi ayarlamak istediğiniz konuma sürükleyin ve sonra hata ayıklamaya devam etmek için **F5** tuşunu seçin.

- **Değişkenler için değer bilgilerini yakalayın**. Kodunuzda bir değişkene bir DataTip ekleyebilir ve hata ayıklama işlemi tamamlandıktan sonra değişken için bilinen son değere erişebilmek üzere onu sabitleyebilir. daha fazla bilgi için bkz. veri [İpuçları veri değerlerini görüntüleme](../debugger/view-data-values-in-data-tips-in-the-code-editor.md).

     Bir DataTip eklemek için, hata ayıklayıcı kesme modunda olmalıdır. İmleci değişkenine yerleştirin ve ardından görüntülenen veri Ipucunda sabitle düğmesini seçin. Hata ayıklama durdurulduğunda, değişkeni içeren kod satırının yanına kaynak dosyada mavi bir pin simgesi görünür. Mavi PIN 'e işaret ederseniz, en son hata ayıklama oturumundan değişkenin değeri görünür.

- **Hemen penceresini temizleyin**. Tasarım zamanında, veya girerek [hemen pencerenin](../ide/reference/immediate-window.md) içeriğini silebilirsiniz. `>cls``>Edit.ClearAll`

     ek komutlar hakkında daha fazla bilgi için [Visual Studio komut diğer adları](../ide/reference/visual-studio-command-aliases.md)bölümüne bakın.

- **[CodeLens ile kod değişikliklerini ve diğer geçmişi bulun](../ide/find-code-changes-and-other-history-with-codelens.md)**. CodeLens, Düzenleyiciden çıkmadan kodunuzda ne olduğunu öğrenirken çalışmanıza odaklanmanızı sağlar &mdash; . Kod parçasına, kodunuzda değişikliklere, bağlantılı hatalara, iş öğelerine, kod incelemelerine ve birim testlerine yönelik başvuruları bulabilirsiniz.

- **diğer kişilerle gerçek zamanlı hata ayıklamak için Live Share kullanın**. Live Share, kullandığınız programlama dillerinden veya oluşturduğunuz uygulama türlerinden bağımsız olarak başkalarıyla gerçek zamanlı işbirliği yaparak kodu düzenlemenize ve hataları ayıklamanıza olanak tanır. Daha fazla bilgi için bkz. [Visual Studio Live Share nedir?](/visualstudio/liveshare/)

- **Küçük kod yazmak ve test etmek Için etkileşimli pencere kullanın**. Visual Studio rastgele kod girmenizi ve anında sonuçları görmenizi sağlayan etkileşimli bir okuma-değerlendirme-yazdır-döngüsü (REPL) penceresi sağlar. Bu kodlama yöntemi, API 'Leri ve kitaplıkları öğrenmenize ve denemenize ve etkileşimli olarak, projelerinize dahil etmek üzere çalışma kodu geliştirmenize yardımcı olur. Python için bkz. [Python etkileşimli penceresiyle çalışma](../python/python-interactive-repl-in-visual-studio.md). Etkileşimli pencere özelliği C# için de kullanılabilir. 

## <a name="access-visual-studio-tools"></a>erişim Visual Studio araçları

Geliştirici Komut İstemi veya Başlat menüsü ya da görev çubuğuna sabitlemeyi yaparsanız, başka bir Visual Studio aracına hızlı bir şekilde erişebilirsiniz.

::: moniker range="vs-2017"

1. Windows Explorer 'da *%programdata%\microsoft\ Windows \start Menu\Programs\ Visual Studio 2017 \ Visual Studio Araçları* gidin.

::: moniker-end

::: moniker range=">=vs-2019"

1. Windows Explorer 'da *%programdata%\microsoft\ Windows \start Menu\Programs\ Visual Studio 2019 \ Visual Studio Araçları* gidin.

::: moniker-end

2. **Geliştirici komut istemi** için sağ tıklayın veya bağlam menüsünü açın, sonra başlatmak veya **görev çubuğuna sabitlemek** **için Sabitle** ' yi seçin.

## <a name="manage-files-toolbars-and-windows"></a>Dosyaları, araç çubuklarını ve pencereleri yönetme

Herhangi bir zamanda birden fazla kod dosyasında çalışıyor olabilir ve bir uygulama geliştirirken çeşitli araç pencereleri arasında hareket edebilirsiniz. Aşağıdaki ipuçlarını kullanarak düzeninizi izleyebilirsiniz:

- **Sık kullandığınız dosyaları düzenleyicide görünür tutun**. Düzenleyicide kaç dosya açık olursa olsun, görünür kalması için dosyaları sekmenin sol tarafına sabitleyebilirsiniz.

   Bir dosyayı sabitlemek için dosyanın sekmesini seçin ve ardından **pin durumunu aç** düğmesini seçin.

- **Belgeleri ve pencereleri diğer Izleyicilere taşıyın**. Uygulama geliştirirken birden fazla izleyici kullanırsanız, düzenleyicide açık olan dosyaları başka bir monitöre taşıyarak uygulamanızın bölümlerinde daha kolay çalışabilirsiniz. Ayrıca, hata ayıklayıcı pencereleri gibi araç pencerelerini başka bir monitöre ve sekmeye yerleştir belge ve araç pencerelerini birlikte "Rafts" oluşturmak için de taşıyabilirsiniz. Daha fazla bilgi için bkz. [Visual Studio pencere düzenlerini özelleştirme](../ide/customizing-window-layouts-in-visual-studio.md).

   Ayrıca, başka bir **Çözüm Gezgini** örneği oluşturup başka bir monitöre taşıyarak dosyaları daha kolay bir şekilde yönetebilirsiniz. **Çözüm Gezgini** başka bir örneğini oluşturmak için **Çözüm Gezgini** bir kısayol menüsü açın ve sonra **Yeni Çözüm Gezgini Görünüm**' ü seçin.

- **Visual Studio görünen yazı tiplerini özelleştirin**. IDE 'deki metin için kullanılan yazı tipini, boyutunu ve rengi değiştirebilirsiniz. Örneğin, düzenleyicideki belirli kod öğelerinin rengini ve araç pencereleri ya da IDE genelinde yazı tipi yüzünü özelleştirebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: yazı tiplerini ve renkleri değiştirme](../ide/how-to-change-fonts-and-colors-in-visual-studio.md) ve [nasıl yapılır: düzenleyicideki yazı tiplerini ve renkleri değiştirme](../ide/reference/how-to-change-fonts-and-colors-in-the-editor.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio ipuçları ve püf noktaları blog gönderisi](https://devblogs.microsoft.com/visualstudio/visual-studio-tips-and-tricks/)
- [Sık kullanılan komutlar için varsayılan klavye kısayolları](../ide/default-keyboard-shortcuts-for-frequently-used-commands-in-visual-studio.md)
- [Nasıl yapılır: menüleri ve araç çubuklarını özelleştirme](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md)
- [İzlenecek yol: basit bir uygulama oluşturma](../get-started/csharp/tutorial-wpf.md)
- [Erişilebilirlik ipuçları ve püf noktaları](../ide/reference/accessibility-tips-and-tricks.md)