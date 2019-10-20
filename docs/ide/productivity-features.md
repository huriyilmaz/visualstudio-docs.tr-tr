---
title: Üretkenlik ipuçları
ms.date: 2/21/2019
ms.topic: conceptual
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c0ac256d9878df45404dc62f1080e12bb6e7f002
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666782"
---
# <a name="productivity-tips-for-visual-studio"></a>Visual Studio için üretkenlik ipuçları

Bu makalelerde, kodunuzu daha hızlı ve verimli bir şekilde yazmanıza, gezinmenize ve hata ayıklamanıza yardımcı olan Visual Studio özelliklerine yönelik ipuçları ele alınmaktadır.

Faydalı klavye kısayolları hakkında daha fazla bilgi için bkz. [üretkenlik kısayolları](../ide/productivity-shortcuts.md). Komut kısayollarının tüm listesi için bkz. [varsayılan klavye kısayolları](../ide/default-keyboard-shortcuts-in-visual-studio.md).

## <a name="write-code"></a>Kod Yaz

Aşağıdaki özellikleri kullanarak daha hızlı bir şekilde kod yazın.

- **Kullanışlı komutları kullanın**. Visual Studio, yaygın Düzenle görevleri daha hızlı gerçekleştirmenize yardımcı olacak çeşitli komutlar içerir. Örneğin, bir kod satırını kopyalamak zorunda kalmadan kolayca çoğaltmak için bir komut seçebilirsiniz, imleci yeniden konumlandırabilirsiniz ve yapıştırın. **Düzenle**  > **Yinele** seçeneğini belirleyin veya **CTRL** +**E**,**V**tuşlarına basın. Ayrıca, **düzenle**  > **Gelişmiş**  > **seçimi genişlet** veya  > **Gelişmiş**  > **sözleşme seçimini** **Düzenle** ' yi seçerek veya  **SHIFT** 1**alt** 3 **5** veya **SHIFT** 7**alt** 9 **1**.

- **IntelliSense kullanın**. Düzenleyicide kod girerken, liste üyeleri, parametre bilgileri, hızlı bilgi, Imza yardımı ve tüm kelime gibi IntelliSense bilgileri görüntülenir. Bu özellikler, metnin belirsiz eşleşmesini destekler; Örneğin, liste üyeleri için sonuç listeleri yalnızca girdiğiniz karakterlerle başlayan girişleri değil, aynı zamanda adlarının herhangi bir yerindeki karakter bileşimini içeren girdileri de içerir. Daha fazla bilgi için bkz. [IntelliSense 'ı kullanma](../ide/using-intellisense.md).

- **Kod girerken IntelliSense seçeneklerinin otomatik olarak eklenmesini değiştirin**. IntelliSense 'i öneri moduna geçirerek, IntelliSense seçeneklerinin yalnızca açıkça seçtiğiniz durumlarda ekleneceğini belirtebilirsiniz.

     Öneri modunu etkinleştirmek için **Ctrl** +**alt** +**Ara çubuğu** tuşlarını seçin veya menü çubuğunda,  > **IntelliSense** ' i seçin  > **tamamlama modunu** **Düzenle** ' yi seçin.

- **Kod parçacıklarını kullanın**. Yerleşik kod parçacıklarını kullanabilir veya kendi kod parçacıklarınızı oluşturabilirsiniz.

     Bir kod parçacığı eklemek için, menü çubuğunda **düzenle**  > **IntelliSense** ' i seçin  > **kod parçacığı ekleyin** veya **ile çevreleyin**veya kısayol menüsünü bir dosyada açın ve **kod** parçacığı  > **kod parçacığı** **Ekle ' yi seçin. Ile çevreleyin**. Daha fazla bilgi için bkz. [kod parçacıkları](../ide/code-snippets.md).

- **Kod hatalarını satır Içinde düzeltir**. Hızlı Eylemler, tek bir eylem ile kodu kolayca yeniden düzenleme, oluşturma veya başka şekilde değiştirmenize olanak sağlar. Bu eylemler, Screwdriver ![Screwdriver simgesi ](media/screwdriver-icon.png) veya hafif ampul ![Light ampul simgesi ](media/light-bulb-icon.png) simgeleri kullanılarak veya **Alt** +**enter** veya **CTRL** + tuşlarına basarak uygulanabilir **.** imlecinizin uygun kod satırında olması durumunda. Daha fazla bilgi için bkz. [hızlı eylemler](quick-actions.md) .

- **Bir kod öğesinin tanımını görüntüleyin ve düzenleyin**. Üye, değişken veya yerel gibi bir kod öğesinin tanımlandığı modülü hızlıca gösterebilir ve düzenleyebilirsiniz.

    Bir tanımı açılır pencerede açmak için, öğeyi vurgulayın, sonra **Alt** +**F12** tuşlarını seçin veya öğe için kısayol menüsünü açın ve ardından **Gözat**' ı seçin. Ayrı bir kod penceresinde bir tanımı açmak için, öğe için kısayol menüsünü açın ve ardından **Tanıma Git**' i seçin.

- **Örnek uygulamaları kullanın**. [Microsoft Developer Network](https://code.msdn.microsoft.com/)'ten örnek uygulamalar indirerek ve yükleyerek uygulama geliştirmeyi hızlandırabilirsiniz. Ayrıca, bu alana yönelik bir örnek paketi indirerek ve inceleyerek belirli bir teknoloji veya programlama kavramı de öğrenebilirsiniz.

## <a name="navigate-within-your-code"></a>Kodunuzun içinde gezinme

Kodunuzda belirli konumları daha hızlı bir şekilde bulmak ve taşımak için çeşitli teknikler kullanabilirsiniz.

- **Kod satırları yer işareti**. Bir dosyadaki belirli kod satırlarına hızlıca gezinmek için yer işaretlerini kullanabilirsiniz.

    Bir yer işareti ayarlamak için, menü çubuğunda  > **yer Işaretlerini** **Düzenle**  > **yer işaretini aç**' ı seçin. Bir çözümün tüm yer imlerini **yer işaretleri** penceresinde görüntüleyebilirsiniz. Daha fazla bilgi için bkz. [koddaki yer Imlerini ayarlama](../ide/setting-bookmarks-in-code.md).

- **Bir dosyada sembol tanımlarını arayın**. Sembol tanımlarını ve dosya adlarını bulmak için bir çözüm içinde arama yapabilirsiniz, ancak arama sonuçları ad alanları veya yerel değişkenler içermez.

   Bu özelliğe erişmek için, menü çubuğunda **Düzenle** ' yi seçin  > **Git**' i seçin.

- **Kodunuzun genel yapısına gözatın**. **Çözüm Gezgini**, Koleksiyonlarınızda sınıfları ve bunların türlerini ve üyelerini arayabilir ve bunlara gözatabilirler. Ayrıca sembolleri arayabilir, yöntemin Çağrı hiyerarşisini görüntüleyebilir, sembol başvurularını bulabilir ve diğer görevleri gerçekleştirebilirsiniz. **Çözüm Gezgini**bir kod öğesi seçerseniz, ilişkili dosya bir **Önizleme** sekmesinde açılır ve imleç dosyadaki öğeye gider. Daha fazla bilgi için bkz. [kod yapısını görüntüleme](../ide/viewing-the-structure-of-code.md).

## <a name="find-items-faster"></a>Öğeleri daha hızlı bulun

Araç pencerelerinin içeriğini yalnızca geçerli göreviniz için ilgili bilgileri gösterecek şekilde filtrelemeye ek olarak komutlar, dosyalar ve seçenekler için IDE genelinde arama yapabilirsiniz.

- **Araç pencerelerinin Içeriğini filtreleyin**. **Araç kutusu**, **özellikler** penceresi ve **Çözüm Gezgini**gibi birçok araç penceresinin içeriği içinde arama yapabilirsiniz ancak yalnızca adları belirttiğiniz karakterleri içeren öğeleri görüntüleyebilirsiniz.

- **Yalnızca ele almak istediğiniz hataları görüntüleyin**. **Hata listesi** araç çubuğunda **filtre** düğmesini seçerseniz, **hata listesi** penceresinde görüntülenen hata sayısını azaltabilirsiniz. Yalnızca düzenleyicide açık olan dosyalardaki hataları, yalnızca geçerli dosyadaki hataları veya yalnızca geçerli projedeki hataları görüntüleyebilirsiniz. Ayrıca, belirli hataları bulmak için **hata listesi** penceresi içinde arama yapabilirsiniz.

- **İletişim kutularını, menü komutlarını, seçenekleri ve daha fazlasını bulun**. Arama kutusuna bulmaya çalıştığınız öğeler için anahtar sözcükler veya ifadeler girin. Örneğin, **Yeni proje**girdiğinizde aşağıdaki seçenekler görüntülenir:

   ::: moniker range="vs-2017"

   ![' Yeni proje ' için hızlı başlatma sonuçları](../ide/media/productivity_quicklaunch.png)

   **Hızlı başlatma** , yeni bir proje oluşturmak, projeye yeni bir öğe eklemek ve **Seçenekler** Iletişim kutusundaki **Projeler ve çözümler** sayfasına diğerleri arasında bağlantılar görüntüler. Arama sonuçları, proje dosyalarını ve araç pencerelerini de içerebilir.

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![' Yeni proje ' için arama sonuçları](../ide/media/vs-2019/productivity-quick-launch-new-project.png)

   ::: moniker-end

   **Ctrl** +**Q** tuşlarına basarak arama kutusuna doğrudan atlayın.

## <a name="debug-code"></a>Hata ayıklama kodu

Hata ayıklama çok fazla zaman alabilir, ancak aşağıdaki ipuçları süreci hızlandırabilmeniz için size yardımcı olabilir.

- **Aynı sayfayı, uygulamayı veya siteyi farklı tarayıcılarda test edin**. Kodunuzun hatalarını ayıkladığınızda, [sayfa denetçisi (Visual Studio)](https://msdn.microsoft.com/Library/65880969-1ad2-47be-85b9-bb12c81bf209)dahil olmak üzere yüklü Web tarayıcıları arasında kolayca geçiş **yapabilirsiniz iletişim kutusunu** açmaya gerek yoktur. Hata ayıklama **Başlat** düğmesinin yanındaki **Standart** araç çubuğunda bulunan **hata ayıklama hedefi** listesini kullanabilirsiniz. Bu işlem, hata ayıklama veya sayfaları görüntüleme olarak hangi tarayıcıyı kullandığınızı hızlıca doğrulamak için kullanılır.

    ![Web tarayıcısı hata ayıklama seçeneklerini belirleyin](../ide/media/webbrowserdropdowntoolbar.png)

- **Geçici kesme noktaları ayarlayın**. Geçerli kod satırında geçici bir kesme noktası oluşturabilir ve hata ayıklayıcıyı eşzamanlı olarak başlatabilirsiniz. Bu kod satırını vurduktan sonra, hata ayıklayıcı kesme moduna girer. Daha fazla bilgi için bkz. [hata ayıklayıcıyla kod Içinde gezinme](../debugger/navigating-through-code-with-the-debugger.md).

    Bu özelliği kullanmak için **Ctrl** +**F10** tuşlarını seçin veya kesmek istediğiniz kod satırı için kısayol menüsünü açın ve ardından **imlece Çalıştır**' ı seçin.

- **Hata ayıklama sırasında yürütme noktasını taşıyın**. Geçerli yürütme noktasını kodun farklı bir bölümüne taşıyabilir ve sonra bu noktadan hata ayıklamayı yeniden başlatabilirsiniz. Bu teknik, bu bölüme ulaşmak için gereken adımların tümünü yeniden oluşturmak zorunda kalmadan kod bölümünün hatalarını ayıklamak istiyorsanız kullanışlıdır. Daha fazla bilgi için bkz. [hata ayıklayıcıyla kod Içinde gezinme](../debugger/navigating-through-code-with-the-debugger.md).

     Yürütme noktasını taşımak için, sarı ok ucunu aynı kaynak dosyasında bir sonraki ifadeyi ayarlamak istediğiniz konuma sürükleyin ve sonra hata ayıklamaya devam etmek için **F5** tuşunu seçin.

- **Değişkenler için değer bilgilerini yakalayın**. Kodunuzda bir değişkene bir DataTip ekleyebilir ve hata ayıklama işlemi tamamlandıktan sonra değişken için bilinen son değere erişebilmek üzere onu sabitleyebilir. Daha fazla bilgi için bkz. [veri İpuçlarında veri değerlerini görüntüleme](../debugger/view-data-values-in-data-tips-in-the-code-editor.md).

     Bir DataTip eklemek için, hata ayıklayıcı kesme modunda olmalıdır. İmleci değişkenine yerleştirin ve ardından görüntülenen veri Ipucunda sabitle düğmesini seçin. Hata ayıklama durdurulduğunda, değişkeni içeren kod satırının yanına kaynak dosyada mavi bir pin simgesi görünür. Mavi PIN 'e işaret ederseniz, en son hata ayıklama oturumundan değişkenin değeri görünür.

- **Hemen penceresini temizleyin**. Tasarım zamanında `>cls` veya `>Edit.ClearAll` girerek [hemen pencerenin](../ide/reference/immediate-window.md) içeriklerini silebilirsiniz.

     Ek komutlar hakkında daha fazla bilgi için bkz. [Visual Studio komut diğer adları](../ide/reference/visual-studio-command-aliases.md).

## <a name="access-visual-studio-tools"></a>Visual Studio araçlarına erişin

Geliştirici Komut İstemi veya başka bir Visual Studio aracına hızlı bir şekilde, Başlat menüsüne veya görev çubuğuna sabitlemeyi sağlayabilirsiniz.

::: moniker range="vs-2017"

1. Windows Gezgini 'nde *%ProgramData%\Microsoft\Windows\Start Menu\Programs\Visual Studio 2017 \ Visual Studio Araçları*konumuna gidin.

::: moniker-end

::: moniker range=">=vs-2019"

1. Windows Gezgini 'nde *%ProgramData%\Microsoft\Windows\Start Menu\Programs\Visual Studio 2019 \ Visual Studio Araçları*konumuna gidin.

::: moniker-end

2. **Geliştirici komut istemi**için sağ tıklayın veya bağlam menüsünü açın, sonra başlatmak veya **görev çubuğuna sabitlemek** **için Sabitle** ' yi seçin.

## <a name="manage-files-toolbars-and-windows"></a>Dosyaları, araç çubuklarını ve pencereleri yönetme

Herhangi bir zamanda birden fazla kod dosyasında çalışıyor olabilir ve bir uygulama geliştirirken çeşitli araç pencereleri arasında hareket edebilirsiniz. Aşağıdaki ipuçlarını kullanarak düzeninizi izleyebilirsiniz:

- **Sık kullandığınız dosyaları düzenleyicide görünür tutun**. Düzenleyicide kaç dosya açık olursa olsun, görünür kalması için dosyaları sekmenin sol tarafına sabitleyebilirsiniz.

   Bir dosyayı sabitlemek için dosyanın sekmesini seçin ve ardından **pin durumunu aç** düğmesini seçin.

- **Belgeleri ve pencereleri diğer Izleyicilere taşıyın**. Uygulama geliştirirken birden fazla izleyici kullanırsanız, düzenleyicide açık olan dosyaları başka bir monitöre taşıyarak uygulamanızın bölümlerinde daha kolay çalışabilirsiniz. Ayrıca, hata ayıklayıcı pencereleri gibi araç pencerelerini başka bir monitöre ve sekmeye yerleştir belge ve araç pencerelerini birlikte "Rafts" oluşturmak için de taşıyabilirsiniz. Daha fazla bilgi için bkz. [Visual Studio 'da pencere düzenlerini özelleştirme](../ide/customizing-window-layouts-in-visual-studio.md).

   Ayrıca, başka bir **Çözüm Gezgini** örneği oluşturup başka bir monitöre taşıyarak dosyaları daha kolay bir şekilde yönetebilirsiniz. **Çözüm Gezgini**başka bir örneğini oluşturmak için **Çözüm Gezgini**bir kısayol menüsü açın ve sonra **Yeni Çözüm Gezgini Görünüm**' ü seçin.

- **Visual Studio 'da görünen yazı tiplerini özelleştirin**. IDE 'deki metin için kullanılan yazı tipini, boyutunu ve rengi değiştirebilirsiniz. Örneğin, düzenleyicideki belirli kod öğelerinin rengini ve araç pencereleri ya da IDE genelinde yazı tipi yüzünü özelleştirebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: yazı tiplerini ve renkleri değiştirme](../ide/how-to-change-fonts-and-colors-in-visual-studio.md) ve [nasıl yapılır: düzenleyicideki yazı tiplerini ve renkleri değiştirme](../ide/reference/how-to-change-fonts-and-colors-in-the-editor.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio ipuçları ve püf noktaları blog gönderisi](https://devblogs.microsoft.com/visualstudio/visual-studio-tips-and-tricks/)
- [Sık kullanılan komutlar için varsayılan klavye kısayolları](../ide/default-keyboard-shortcuts-for-frequently-used-commands-in-visual-studio.md)
- [Nasıl yapılır: menüleri ve araç çubuklarını özelleştirme](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md)
- [İzlenecek yol: basit bir uygulama oluşturma](../get-started/csharp/tutorial-wpf.md)
- [Erişilebilirlik ipuçları ve püf noktaları](../ide/reference/accessibility-tips-and-tricks.md)
