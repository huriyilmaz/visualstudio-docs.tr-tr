---
title: Üretkenlik Kılavuzu
description: Visual Studio 'daki klavye kısayolları ve üretkenlik özellikleri hakkında bilgi edinmek için, kodu etkin bir şekilde yazmanıza, hata ayıklamanıza ve hataları işlemenize yardımcı olabilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 4/29/2020
ms.topic: conceptual
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 181ce2071d780c9ef481d281f543c49d65262078
ms.sourcegitcommit: 6d88913a8b5a9e5eda01d3f95205b4d138f440f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2021
ms.locfileid: "107296787"
---
# <a name="productivity-guide-for-visual-studio"></a>Visual Studio için üretkenlik Kılavuzu

Kodu yazarken zaman kazanmak istiyorsanız, doğru yerde olursunuz. Bu üretkenlik Kılavuzu, Visual Studio kullanmaya başlamanıza, kod yazmanıza, kod hata ayıklamanıza, hataları işlemeye ve tek bir sayfada klavye kısayollarını kullanmanıza yardımcı olabilecek ipuçları içerir &mdash; .

Faydalı klavye kısayolları hakkında daha fazla bilgi için bkz. [üretkenlik kısayolları](../ide/productivity-shortcuts.md). Komut kısayollarının tüm listesi için bkz. [varsayılan klavye kısayolları](../ide/default-keyboard-shortcuts-in-visual-studio.md).

## <a name="get-started"></a>başlarken

Komutlar, ayarlar, belgeler ve Install seçenekleri de dahil olmak üzere ihtiyacınız olan her şeyi hızlıca arayarak menüler aracılığıyla zaman ayırarak tasarruf edin. Visual Studio 'da arama sonuçlarınızda bulunan komutlara yönelik klavye kısayollarına bakın. böylece bunları daha kolay bir şekilde yeniden deneyebilirsiniz. 

- **Görev listesini kullanan sahte kod**. Kod parçasını tamamlamaya yetecek kadar gereksinimleriniz yoksa, ve gibi belirteçleri kullanan kod açıklamalarını izlemek için Görev Listesi kullanın `TODO` `HACK` ve sizi doğrudan kodda önceden tanımlanmış bir konuma götürür kısayolları yönetin. Daha fazla bilgi için bkz. [görev listesi kullanma](../ide/using-the-task-list.md).

- **Çözüm Gezgini kısayollarını kullanın**. Visual Studio 'ya yeni başladıysanız, bu kısayollar yararlı olur ve yeni bir kod tabanında hızlanırken size zaman kazandırır. Kısayolların tam listesi için bkz. [Visual Studio 'Da varsayılan klavye kısayolları](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_solutionexplorerGLOBAL).

- **[Visual Studio 'da klavye kısayollarını belirleyip özelleştirin](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)**. Visual Studio komutları için kısayollar tanımlayabilir, bu kısayolları özelleştirebilir ve başkalarının kullanması için dışarı aktarabilirsiniz. Seçenekler iletişim kutusunda her zaman bir klavye kısayolunu bulabilir ve değiştirebilirsiniz.

- **Visual Studio 'yu daha erişilebilir hale getirin**. Visual Studio, ekran okuyucular ve diğer yardımcı teknolojilerle uyumlu yerleşik erişilebilirlik özelliklerine sahiptir. Kullanılabilir özelliklerin tam listesi için bkz. [Visual Studio Için erişilebilirlik ipuçları ve püf noktaları](../ide/reference/accessibility-tips-and-tricks.md) . 

- **Visual Studio ürün yaşam döngüsünü ve bakımını inceleyin**. Visual Studio güncelleştirmelerini alma hakkında daha fazla bilgi için, Enterprise ve Professional müşterilerine yönelik destek seçenekleri, Visual Studio 'nun eski sürümleri için destek ve Visual Studio hizmetinin kapsamadığı bileşenler için bkz. [Visual Studio ürün yaşam döngüsü ve bakımı](/visualstudio/releases/2019/servicing). 

- **Visual Studio 'Da NuGet paketlerini yükleyip yönetin**. Windows üzerinde Visual Studio 'daki NuGet Paket Yöneticisi Kullanıcı arabirimi, projelerde ve çözümlerde NuGet paketlerini kolayca yüklemenize, kaldırmanıza ve güncelleştirmenize olanak tanır. Daha fazla bilgi için bkz. [NuGet paket yöneticisini kullanarak Visual Studio 'da paketleri yükleyip yönetme](/nuget/consume-packages/install-use-packages-visual-studio).

## <a name="write-code"></a>Kod yazma

Aşağıdaki özellikleri kullanarak daha hızlı bir şekilde kod yazın.

- **Kullanışlı komutları kullanın**. Visual Studio, yaygın Düzenle görevleri daha hızlı gerçekleştirmenize yardımcı olacak çeşitli komutlar içerir. Örneğin, bir kod satırını kopyalamak zorunda kalmadan kolayca çoğaltmak için bir komut seçebilirsiniz, imleci yeniden konumlandırabilirsiniz ve yapıştırın. Yinelemeyi **Düzenle**  >   ' yi seçin veya **CTRL** + **E**,**V** tuşlarına basın. Ayrıca   >  ,**Gelişmiş**  >  **Genişlet seçimini** Düzenle veya   >  **Gelişmiş**  >  **sözleşme seçimini** Düzenle ' yi seçerek veya **SHIFT** + **alt** + **=** veya **SHIFT** + **alt** + **-** tuşlarına basarak bir metin seçimini hızlıca genişletebilir veya dağıtabilirsiniz.

- **IntelliSense kullanın**. Düzenleyicide kod girerken, liste üyeleri, parametre bilgileri, hızlı bilgi, Imza yardımı ve tüm kelime gibi IntelliSense bilgileri görüntülenir. Bu özellikler, metnin belirsiz eşleşmesini destekler; Örneğin, liste üyeleri için sonuç listeleri yalnızca girdiğiniz karakterlerle başlayan girişleri değil, aynı zamanda adlarının herhangi bir yerindeki karakter kombinasyonunu içeren girdileri de içerir. Daha fazla bilgi için bkz. [IntelliSense 'ı kullanma](../ide/using-intellisense.md).

- **Kod girerken IntelliSense seçeneklerinin otomatik olarak eklenmesini değiştirin**. IntelliSense 'i öneri moduna geçirerek, IntelliSense seçeneklerinin yalnızca açıkça seçtiğiniz durumlarda ekleneceğini belirtebilirsiniz.

     Öneri modunu etkinleştirmek için **CTRL** + **alt** + **Ara çubuğu** tuşlarını seçin veya menü çubuğunda IntelliSense **Düzenle**  >    >  **tamamlama modunu** seçin.

- **Kod parçacıklarını kullanın**. Yerleşik kod parçacıklarını kullanabilir veya kendi kod parçacıklarınızı oluşturabilirsiniz.

     Bir kod parçacığı eklemek için, menü çubuğunda IntelliSense **düzenleme**  >    >  **kod parçacığı Ekle** veya **ile Çevrele**' yi seçin veya kısayol menüsünü bir dosyada açın ve **kod parçacığı**  >  **Ekle parçacık** veya **ile çevreleyin**' i seçin. Daha fazla bilgi için bkz. [kod parçacıkları](../ide/code-snippets.md).

- **Kod hatalarını satır Içinde düzeltir**. Hızlı Eylemler, tek bir eylem ile kodu kolayca yeniden düzenleme, oluşturma veya başka şekilde değiştirmenize olanak sağlar. Bu eylemler, Screwdriver ![ screwsürücü simgesi ](media/screwdriver-icon.png) veya hafif Ampul ampul ![ simgesi ](media/light-bulb-icon.png) simgeleri kullanılarak veya **alt** + **ENTER** ya da **CTRL** tuşlarına basarak uygulanabilir + **.** imlecinizin uygun kod satırında olması durumunda. Daha fazla bilgi için bkz. [hızlı eylemler](quick-actions.md) .

- **Bir kod öğesinin tanımını görüntüleyin ve düzenleyin**. Üye, değişken veya yerel gibi bir kod öğesinin tanımlandığı modülü hızlıca gösterebilir ve düzenleyebilirsiniz.

    Bir tanımı açılır pencerede açmak için, öğeyi vurgulayın, sonra **alt** + **F12** tuşlarını seçin veya öğe için kısayol menüsünü açın ve ardından **Gözat**' ı seçin. Ayrı bir kod penceresinde bir tanımı açmak için, öğe için kısayol menüsünü açın ve ardından **Tanıma Git**' i seçin.

- **Örnek uygulamaları kullanın**. [Microsoft Developer Network](https://code.msdn.microsoft.com/)'ten örnek uygulamalar indirerek ve yükleyerek uygulama geliştirmeyi hızlandırabilirsiniz. Ayrıca, bu alana yönelik bir örnek paketi indirerek ve inceleyerek belirli bir teknoloji veya programlama kavramı de öğrenebilirsiniz.

- **Biçimlendirme/yeni satırlarla küme ayracı biçimlendirmesini değiştirin**. Yeni satırlar dahil olmak üzere kod düzenleyicisinde biçimlendirme kodu seçeneklerini ayarlamak için **biçimlendirme**  seçenekleri sayfasını kullanın. Bu ayarın C# ' de nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [Seçenekler iletişim kutusu: metin düzenleyici > C# > kod stili > biçimlendirme](../ide/reference/options-text-editor-csharp-formatting.md). C++ için bkz. [Visual Studio 'Da c++ kodlama tercihlerinizi ayarlama](/cpp/ide/how-to-set-preferences). Python için bkz. [Python kodunu biçimlendirme](../python/formatting-python-code.md).

- **Girintilerinizi sekmelerle değiştirin**. Farklı düzenleyicilerde ve sdes 'lerde aynı projede çalışan birden çok geliştirici için tutarlı kodlama stillerini zorlamak üzere her kod tabanına uyarlanmış özel düzenleyici ayarlarını kullanın. Tüm takımınızın aynı dil kurallarına, adlandırma kurallarına ve biçimlendirme kurallarına uyduğundan emin olun. Bu özel ayarlar taşınabilir olduğundan ve kodunuzla birlikte gezindiğinden, Visual Studio dışında bile kodlama stillerini zorunlu kılabilirsiniz. Daha fazla bilgi için bkz. [Seçenekler, metin düzenleyici, tüm diller, sekmeler](../ide/reference/options-text-editor-all-languages-tabs.md#tabs).

## <a name="navigate-within-your-code-and-the-ide"></a>Kodunuzda ve IDE 'de gezinme

Kodunuzda belirli konumları daha hızlı bir şekilde bulmak ve taşımak için çeşitli teknikler kullanabilirsiniz. Tercihlerinize göre Visual Studio pencerelerinin yerleşimini de değiştirebilirsiniz. 

- **Kod satırları yer işareti**. Bir dosyadaki belirli kod satırlarına hızlıca gezinmek için yer işaretlerini kullanabilirsiniz.

    Bir yer işareti ayarlamak için, menü çubuğunda   >  **yer imlerini** Düzenle yer işaretlerini Seç  >  **yer işaretini** seçin. Bir çözümün tüm yer imlerini **yer işaretleri** penceresinde görüntüleyebilirsiniz. Daha fazla bilgi için bkz. [koddaki yer Imlerini ayarlama](../ide/setting-bookmarks-in-code.md).

- **Bir dosyada sembol tanımlarını arayın**. Sembol tanımlarını ve dosya adlarını bulmak için bir çözüm içinde arama yapabilirsiniz, ancak arama sonuçları ad alanları veya yerel değişkenler içermez.

   Bu özelliğe erişmek için, menü çubuğunda,   >  **Git 'e git**' i seçin.

- **Kodunuzun genel yapısına gözatın**. **Çözüm Gezgini**, Koleksiyonlarınızda sınıfları ve bunların türlerini ve üyelerini arayabilir ve bunlara gözatabilirler. Ayrıca sembolleri arayabilir, yöntemin Çağrı hiyerarşisini görüntüleyebilir, sembol başvurularını bulabilir ve diğer görevleri gerçekleştirebilirsiniz. **Çözüm Gezgini** bir kod öğesi seçerseniz, ilişkili dosya bir **Önizleme** sekmesinde açılır ve imleç dosyadaki öğeye gider. Daha fazla bilgi için bkz. [kod yapısını görüntüleme](../ide/viewing-the-structure-of-code.md).

- **Eşleme modundaki bir dosyadaki konuma atlayın**. Harita modu, kod satırlarını, kaydırma çubuğunda küçük olarak görüntüler. Bu görüntü modu hakkında daha fazla bilgi için bkz. [nasıl yapılır: kaydırma çubuğunu özelleştirme](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md#map-mode).

- Kod **eşlemesiyle kod yapınızı anlayın**. Kod haritaları kodunuzda bağımlılıkları görselleştirmenize yardımcı olabilir ve dosya ve kod satırları arasında okuma yapmadan nasıl sığdığını görürsünüz. Daha fazla bilgi için bkz. [kod eşlemeleriyle harita bağımlılıkları](../modeling/map-dependencies-across-your-solutions.md).

- **En son dosyayı Düzenle/git ile sık kullanılan dosyalara bakın**. Belirli öğeleri hızlı bir şekilde bulmanıza yardımcı olması için kodunuzda odaklanmış bir arama gerçekleştirmek üzere Visual Studio 'daki git komutlarını kullanın. Ayrıntılı yönergeler için bkz. [Go komutunu kullanarak kodu bulma](../ide/go-to.md).

- **[Özellikler penceresi](../ide/reference/properties-window.md) sağ tarafa taşıyın**. Daha tanıdık bir pencere düzeni arıyorsanız, **F4** tuşuna basarak Visual Studio 'daki Özellikler penceresi taşıyabilirsiniz.

## <a name="find-items-faster"></a>Öğeleri daha hızlı bulun

Araç pencerelerinin içeriğini yalnızca geçerli göreviniz için ilgili bilgileri gösterecek şekilde filtrelemeye ek olarak komutlar, dosyalar ve seçenekler için IDE genelinde arama yapabilirsiniz.

- **Araç pencerelerinin Içeriğini filtreleyin**. **Araç kutusu**, **özellikler** penceresi ve **Çözüm Gezgini** gibi birçok araç penceresinin içeriği içinde arama yapabilirsiniz ancak yalnızca adları belirttiğiniz karakterleri içeren öğeleri görüntüleyebilirsiniz.

- **Yalnızca ele almak istediğiniz hataları görüntüleyin**. **Hata listesi** araç çubuğunda **filtre** düğmesini seçerseniz, **hata listesi** penceresinde görüntülenen hata sayısını azaltabilirsiniz. Yalnızca düzenleyicide açık olan dosyalardaki hataları, yalnızca geçerli dosyadaki hataları veya yalnızca geçerli projedeki hataları görüntüleyebilirsiniz. Ayrıca, belirli hataları bulmak için **hata listesi** penceresi içinde arama yapabilirsiniz.

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

- **Visual Studio hata ayıklayıcısı araçları 'Nı kullanın**. Visual Studio bağlamında, uygulamanızda *hata ayıklarken*, genellikle uygulamayı hata ayıklayıcı modunda çalıştırdığınız anlamına gelir. Hata ayıklayıcı, çalışma sırasında kodunuzun ne yaptığını görmek için birçok yol sunar. Başlamak için bir kılavuz için bkz. [Visual Studio hata ayıklayıcısına](../debugger/debugger-feature-tour.md) bakın. 

- **Aynı sayfayı, uygulamayı veya siteyi farklı tarayıcılarda test edin**. Kodunuzun hatalarını ayıkladığınızda, [sayfa denetçisi (Visual Studio)](/previous-versions/hh974728(v=vs.140))dahil olmak üzere yüklü Web tarayıcıları arasında kolayca geçiş **yapabilirsiniz iletişim kutusunu** açmaya gerek yoktur. Hata ayıklama **Başlat** düğmesinin yanındaki **Standart** araç çubuğunda bulunan **hata ayıklama hedefi** listesini kullanabilirsiniz. Bu işlem, hata ayıklama veya sayfaları görüntüleme olarak hangi tarayıcıyı kullandığınızı hızlıca doğrulamak için kullanılır.

    ![Web tarayıcısı hata ayıklama seçeneklerini belirleyin](../ide/media/webbrowserdropdowntoolbar.png)

- **Geçici kesme noktaları ayarlayın**. Geçerli kod satırında geçici bir kesme noktası oluşturabilir ve hata ayıklayıcıyı eşzamanlı olarak başlatabilirsiniz. Bu kod satırını vurduktan sonra, hata ayıklayıcı kesme moduna girer. Daha fazla bilgi için bkz. [hata ayıklayıcıyla kod Içinde gezinme](../debugger/navigating-through-code-with-the-debugger.md).

    Bu özelliği kullanmak için **CTRL** + **F10** tuşlarını seçin veya kesmek istediğiniz kod satırı için kısayol menüsünü açın ve ardından **imlece Çalıştır**' ı seçin.

- **Hata ayıklama sırasında yürütme noktasını taşıyın**. Geçerli yürütme noktasını kodun farklı bir bölümüne taşıyabilir ve sonra bu noktadan hata ayıklamayı yeniden başlatabilirsiniz. Bu teknik, bu bölüme ulaşmak için gereken adımların tümünü yeniden oluşturmak zorunda kalmadan kod bölümünün hatalarını ayıklamak istiyorsanız kullanışlıdır. Daha fazla bilgi için bkz. [hata ayıklayıcıyla kod Içinde gezinme](../debugger/navigating-through-code-with-the-debugger.md).

     Yürütme noktasını taşımak için, sarı ok ucunu aynı kaynak dosyasında bir sonraki ifadeyi ayarlamak istediğiniz konuma sürükleyin ve sonra hata ayıklamaya devam etmek için **F5** tuşunu seçin.

- **Değişkenler için değer bilgilerini yakalayın**. Kodunuzda bir değişkene bir DataTip ekleyebilir ve hata ayıklama işlemi tamamlandıktan sonra değişken için bilinen son değere erişebilmek üzere onu sabitleyebilir. Daha fazla bilgi için bkz. [veri İpuçlarında veri değerlerini görüntüleme](../debugger/view-data-values-in-data-tips-in-the-code-editor.md).

     Bir DataTip eklemek için, hata ayıklayıcı kesme modunda olmalıdır. İmleci değişkenine yerleştirin ve ardından görüntülenen veri Ipucunda sabitle düğmesini seçin. Hata ayıklama durdurulduğunda, değişkeni içeren kod satırının yanına kaynak dosyada mavi bir pin simgesi görünür. Mavi PIN 'e işaret ederseniz, en son hata ayıklama oturumundan değişkenin değeri görünür.

- **Hemen penceresini temizleyin**. Tasarım zamanında, veya girerek [hemen pencerenin](../ide/reference/immediate-window.md) içeriğini silebilirsiniz. `>cls``>Edit.ClearAll`

     Ek komutlar hakkında daha fazla bilgi için bkz. [Visual Studio komut diğer adları](../ide/reference/visual-studio-command-aliases.md).

- **[CodeLens ile kod değişikliklerini ve diğer geçmişi bulun](../ide/find-code-changes-and-other-history-with-codelens.md)**. CodeLens, Düzenleyiciden çıkmadan kodunuzda ne olduğunu öğrenirken çalışmanıza odaklanmanızı sağlar &mdash; . Kod parçasına, kodunuzda değişikliklere, bağlantılı hatalara, iş öğelerine, kod incelemelerine ve birim testlerine yönelik başvuruları bulabilirsiniz.

- **Diğer kişilerle gerçek zamanlı hata ayıklamak için Live Share kullanın**. Live Share, kullandığınız programlama dillerinden veya oluşturduğunuz uygulama türlerinden bağımsız olarak başkalarıyla gerçek zamanlı işbirliği yaparak kodu düzenlemenize ve hataları ayıklamanıza olanak tanır. Daha fazla bilgi için bkz. [Visual Studio Live Share nedir?](/visualstudio/liveshare/)

- **Küçük kod yazmak ve test etmek Için etkileşimli pencere kullanın**. Visual Studio, rastgele bir kod girmenize ve anında sonuçları görebilmenizi sağlayan etkileşimli bir okuma-değerlendirme-Yazdır-döngüsü (REPL) penceresi sağlar. Bu kodlama yöntemi, API 'Leri ve kitaplıkları öğrenmenize ve denemenize ve etkileşimli olarak, projelerinize dahil etmek üzere çalışma kodu geliştirmenize yardımcı olur. Python için bkz. [Python etkileşimli penceresiyle çalışma](../python/python-interactive-repl-in-visual-studio.md). Etkileşimli pencere özelliği C# için de kullanılabilir. 

## <a name="access-visual-studio-tools"></a>Visual Studio araçlarına erişin

Geliştirici Komut İstemi veya başka bir Visual Studio aracına hızlı bir şekilde, Başlat menüsüne veya görev çubuğuna sabitlemeyi sağlayabilirsiniz.

::: moniker range="vs-2017"

1. Windows Gezgini 'nde *%ProgramData%\Microsoft\Windows\Start Menu\Programs\Visual Studio 2017 \ Visual Studio Araçları* konumuna gidin.

::: moniker-end

::: moniker range=">=vs-2019"

1. Windows Gezgini 'nde *%ProgramData%\Microsoft\Windows\Start Menu\Programs\Visual Studio 2019 \ Visual Studio Araçları* konumuna gidin.

::: moniker-end

2. **Geliştirici komut istemi** için sağ tıklayın veya bağlam menüsünü açın, sonra başlatmak veya **görev çubuğuna sabitlemek** **için Sabitle** ' yi seçin.

## <a name="manage-files-toolbars-and-windows"></a>Dosyaları, araç çubuklarını ve pencereleri yönetme

Herhangi bir zamanda birden fazla kod dosyasında çalışıyor olabilir ve bir uygulama geliştirirken çeşitli araç pencereleri arasında hareket edebilirsiniz. Aşağıdaki ipuçlarını kullanarak düzeninizi izleyebilirsiniz:

- **Sık kullandığınız dosyaları düzenleyicide görünür tutun**. Düzenleyicide kaç dosya açık olursa olsun, görünür kalması için dosyaları sekmenin sol tarafına sabitleyebilirsiniz.

   Bir dosyayı sabitlemek için dosyanın sekmesini seçin ve ardından **pin durumunu aç** düğmesini seçin.

- **Belgeleri ve pencereleri diğer Izleyicilere taşıyın**. Uygulama geliştirirken birden fazla izleyici kullanırsanız, düzenleyicide açık olan dosyaları başka bir monitöre taşıyarak uygulamanızın bölümlerinde daha kolay çalışabilirsiniz. Ayrıca, hata ayıklayıcı pencereleri gibi araç pencerelerini başka bir monitöre ve sekmeye yerleştir belge ve araç pencerelerini birlikte "Rafts" oluşturmak için de taşıyabilirsiniz. Daha fazla bilgi için bkz. [Visual Studio 'da pencere düzenlerini özelleştirme](../ide/customizing-window-layouts-in-visual-studio.md).

   Ayrıca, başka bir **Çözüm Gezgini** örneği oluşturup başka bir monitöre taşıyarak dosyaları daha kolay bir şekilde yönetebilirsiniz. **Çözüm Gezgini** başka bir örneğini oluşturmak için **Çözüm Gezgini** bir kısayol menüsü açın ve sonra **Yeni Çözüm Gezgini Görünüm**' ü seçin.

- **Visual Studio 'da görünen yazı tiplerini özelleştirin**. IDE 'deki metin için kullanılan yazı tipini, boyutunu ve rengi değiştirebilirsiniz. Örneğin, düzenleyicideki belirli kod öğelerinin rengini ve araç pencereleri ya da IDE genelinde yazı tipi yüzünü özelleştirebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: yazı tiplerini ve renkleri değiştirme](../ide/how-to-change-fonts-and-colors-in-visual-studio.md) ve [nasıl yapılır: düzenleyicideki yazı tiplerini ve renkleri değiştirme](../ide/reference/how-to-change-fonts-and-colors-in-the-editor.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio ipuçları ve püf noktaları blog gönderisi](https://devblogs.microsoft.com/visualstudio/visual-studio-tips-and-tricks/)
- [Sık kullanılan komutlar için varsayılan klavye kısayolları](../ide/default-keyboard-shortcuts-for-frequently-used-commands-in-visual-studio.md)
- [Nasıl yapılır: menüleri ve araç çubuklarını özelleştirme](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md)
- [İzlenecek yol: basit bir uygulama oluşturma](../get-started/csharp/tutorial-wpf.md)
- [Erişilebilirlik ipuçları ve püf noktaları](../ide/reference/accessibility-tips-and-tricks.md)