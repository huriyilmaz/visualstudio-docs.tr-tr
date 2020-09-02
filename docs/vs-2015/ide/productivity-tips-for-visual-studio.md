---
title: Üretkenlik Ipuçları | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: ccc5e543-7dcf-465c-97dd-e133e869800c
caps.latest.revision: 32
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a5b2f2e2dc00eda388b2a2d075924fa72f9eff1a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670307"
---
# <a name="productivity-tips-for-visual-studio"></a>Visual Studio için Üretkenlik İpuçları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu ipuçlarını izleyerek Visual Studio 'da kodunuzda daha hızlı ve verimli bir şekilde yazma, gezinme ve hata ayıklama işlemlerini gerçekleştirebilirsiniz. Yaygın klavye kısayolları hakkında daha fazla bilgi için bkz. [ipuçları ve püf noktaları](../ide/tips-and-tricks-for-visual-studio.md). Daha kapsamlı bir liste için bkz. klavye kısayollarını ve [varsayılan klavye kısayollarını](../ide/default-keyboard-shortcuts-in-visual-studio.md) [tanımlama ve özelleştirme](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md) .

 Bu konu aşağıdaki bölümleri içermektedir:

 [Visual Studio Araçları erişme](../ide/productivity-tips-for-visual-studio.md#BKMK_Access)

 [Kod yazma](../ide/productivity-tips-for-visual-studio.md#BKMK_Writing)

 [Kodunuzun Içinde gezinme](../ide/productivity-tips-for-visual-studio.md#BKMK_Navigating)

 [Öğeleri daha hızlı bulma](../ide/productivity-tips-for-visual-studio.md#BKMK_Finding)

 [Hata ayıklama kodu](../ide/productivity-tips-for-visual-studio.md#BKMK_Debugging)

 [Dosyaları, araç çubuklarını ve pencereleri yönetme](../ide/productivity-tips-for-visual-studio.md#BKMK_Managing)

## <a name="accessing-visual-studio-tools"></a><a name="BKMK_Access"></a> Visual Studio Araçları erişme
 Başlangıç ekranına veya görev çubuğuna sabitederseniz Geliştirici Komut İstemi veya başka bir araca daha kolay erişebilirsiniz.

1. Başlangıç ekranından girin `Visual Studio Tools` ve Enter tuşunu seçin.

2. **Dosya Gezgini**'nde, istediğiniz öğenin kısayol menüsünü açın:

    - Derleme Bildirimleri

    - Hata ayıklanabilir Paket Yöneticisi

    - VS2013 için Geliştirici Komut İstemi

    - Microsoft Geri Bildirim İstemcisi 2013

    - VS2013 ARM Çapraz Araçları Komut İstemi

    - VS2013 x64 çapraz araçları komut Istemi

    - VS2013 x64 Yerel Araçları Komut İstemi

    - VS2013 x86 Yerel Araçları Komut İstemi

3. Başlatmak veya **görev çubuğuna sabitlemek** **Için sabitle ' yi** seçin.

## <a name="writing-code"></a><a name="BKMK_Writing"></a> Kod yazma
 Aşağıdaki özellikleri kullanarak daha hızlı bir şekilde kod yazın.

- **Örnek uygulamaları kullanın**. MSDN Kod Galerisi 'nden örnek uygulamalar indirerek ve yükleyerek uygulama geliştirmeyi hızlandırabilirsiniz. Ayrıca, bu alana yönelik bir örnek paketi indirerek ve inceleyerek belirli bir teknoloji veya programlama kavramı de öğrenebilirsiniz.

- **IntelliSense kullanın**. Düzenleyicide kod girerken, liste üyeleri, parametre bilgileri, hızlı bilgi, Imza yardımı ve tüm kelime gibi IntelliSense bilgileri görüntülenir. Bu özellikler, metnin belirsiz eşleşmesini destekler; Örneğin, liste üyeleri için sonuç listeleri yalnızca girdiğiniz karakterlerle başlayan girişleri değil, aynı zamanda adlarının herhangi bir yerindeki karakter bileşimini içeren girdileri de içerir. Daha fazla bilgi için bkz. [IntelliSense kullanma](../ide/using-intellisense.md).

- **Kod girerken IntelliSense seçeneklerinin otomatik olarak eklenmesini değiştirin**. IntelliSense 'i öneri moduna geçirerek, IntelliSense seçeneklerinin yalnızca açıkça seçtiğiniz durumlarda ekleneceğini belirtebilirsiniz.

     Öneri modunu etkinleştirmek için Ctrl + Alt + ara çubuğu tuşlarını seçin veya menü çubuğunda **Düzenle**, **IntelliSense**, **tamamlama modunu aç**' ı seçin.

- **Kod parçacıklarını kullanın**. Yerleşik kod parçacıklarını kullanabilir veya kendi kod parçacıklarınızı oluşturabilirsiniz.

     Bir kod parçacığı eklemek için, menü çubuğunda **Düzenle**, **IntelliSense**, **kod parçacığı Ekle** ' yi seçin veya kısayol menüsünü bir dosyada açın ve **kod parçacığı Ekle**' yi seçin. Daha fazla bilgi için bkz. [kod parçacıkları](../ide/code-snippets.md).

- **Kod hatalarını satır Içinde düzeltir**. Akıllı Etiketler, bir kod satırı altında mavi veya kırmızı kutular olarak görünür. Akıllı etiket seçeneklerini kutulardan birine işaret ederek veya işaretçiyi kod satırına yerleştirerek CTRL + seçeneğini belirleyerek görüntüleyebilirsiniz. (Period) anahtarları.

     Mavi kutular kodunuzdaki hataları düzeltmenize yönelik yollar önerir.

     Şekil 1: hata akıllı etiketleri

     ![Akıllı etiket önerilerini hata](../ide/media/productivity-bluesmarttags.png "Productivity_BlueSmartTags")

     Kırmızı kutular, kodunuzu yeniden düzenleme yolları önerir.

     Şekil 2: akıllı etiketleri yeniden düzenleme

     ![Akıllı etiket önerilerini yeniden Düzenle](../ide/media/productivity-redsmarttags.png "Productivity_RedSmartTags")

- **Bir kod öğesinin tanımını görüntüleyin ve düzenleyin**. Üye, değişken veya yerel gibi bir kod öğesinin tanımlandığı modülü hızlıca gösterebilir ve düzenleyebilirsiniz.

     Bir tanımı açılır pencerede açmak için, öğeyi vurgulayın, sonra alt + F12 tuşlarını seçin veya öğe için kısayol menüsünü açın ve ardından **Gözat**' ı seçin. Ayrı bir kod penceresinde bir tanımı açmak için, öğe için kısayol menüsünü açın ve ardından **Tanıma Git**' i seçin.

## <a name="navigating-within-your-code"></a><a name="BKMK_Navigating"></a> Kodunuzun Içinde gezinme
 Kodunuzda belirli konumları daha hızlı bir şekilde bulmak ve taşımak için çeşitli teknikler kullanabilirsiniz.

- **Kod satırları yer işareti**. Bir dosyadaki belirli kod satırlarına hızlıca gezinmek için yer işaretlerini kullanabilirsiniz.

     Bir yer işareti ayarlamak için, menü çubuğunda **Düzenle**, **yer Işaretleri**, **yer işaretini aç**' ı seçin. Bir çözümün tüm yer imlerini **yer işaretleri** penceresinde görüntüleyebilirsiniz. Daha fazla bilgi için bkz. [koddaki yer Imlerini ayarlama](../ide/setting-bookmarks-in-code.md).

- **Bir dosyada sembol tanımlarını arayın**. Sembol tanımlarını ve dosya adlarını bulmak için bir çözüm içinde arama yapabilirsiniz, ancak arama sonuçları ad alanları veya yerel değişkenler içermez.

     Bu özelliğe erişmek için, menü çubuğunda **Düzenle**' yi seçin, **öğesine gidin**.

- **Kodunuzun genel yapısına gözatın**. **Çözüm Gezgini**, Koleksiyonlarınızda sınıfları ve bunların türlerini ve üyelerini arayabilir ve bunlara gözatabilirler. Ayrıca sembolleri arayabilir, yöntemin Çağrı hiyerarşisini görüntüleyebilir, sembol başvurularını bulabilir ve diğer görevleri gerçekleştirebilirsiniz. **Çözüm Gezgini**bir kod öğesi seçerseniz, ilişkili dosya bir **Önizleme** sekmesinde açılır ve imleç dosyadaki öğeye gider. Daha fazla bilgi için bkz. [kod yapısını görüntüleme](../ide/viewing-the-structure-of-code.md).

## <a name="finding-items-faster"></a><a name="BKMK_Finding"></a> Öğeleri daha hızlı bulma
 Araç pencerelerinin içeriğini yalnızca geçerli göreviniz için ilgili bilgileri gösterecek şekilde filtrelemeye ek olarak komutlar, dosyalar ve seçenekler için IDE genelinde arama yapabilirsiniz.

- **Araç pencerelerinin Içeriğini filtreleyin**. **Araç kutusu**, **özellikler** penceresi ve **Çözüm Gezgini**gibi birçok araç penceresinin içeriği içinde arama yapabilirsiniz ancak yalnızca adları belirttiğiniz karakterleri içeren öğeleri görüntüleyebilirsiniz.

- **Yalnızca ele almak istediğiniz hataları görüntüleyin**. **Hata listesi** araç çubuğunda **filtre** düğmesini seçerseniz, **hata listesi** penceresinde görüntülenen hata sayısını azaltabilirsiniz. Yalnızca düzenleyicide açık olan dosyalardaki hataları, yalnızca geçerli dosyadaki hataları veya yalnızca geçerli projedeki hataları görüntüleyebilirsiniz. Ayrıca, belirli hataları bulmak için Hata Listesi penceresi içinde arama yapabilirsiniz.

- **İletişim kutularını, menü komutlarını ve seçenekleri bulun**. [Hızlı Başlat, ortam, Seçenekler Iletişim kutusunda](../ide/reference/quick-launch-environment-options-dialog-box.md) , bulmayı denediğiniz öğeler için anahtar sözcükler veya ifadeler girin. Örneğin, aşağıdaki seçenekler şunu girerseniz görüntülenir `new project` :

     Şekil 3: için hızlı başlatma sonuçları listesi `new project`

     ![' Yeni proje ' için hızlı başlatma sonuçları](../ide/media/productivity-quicklaunch.png "Productivity_QuickLaunch")

     **Hızlı başlatma** , **Yeni proje** Iletişim kutusu, **Yeni öğe Ekle** Iletişim kutusu ve **Seçenekler** iletişim kutusundaki projeler ve çözümler sayfası bağlantılarını diğerleri arasında görüntüler. Hızlı başlatma sonuçları, proje dosyalarını ve araç pencerelerini de içerebilir.

## <a name="debugging-code"></a><a name="BKMK_Debugging"></a> Hata ayıklama kodu
 Hata ayıklama çok fazla zaman alabilir, ancak aşağıdaki ipuçları süreci hızlandırabilmeniz için size yardımcı olabilir.

- **Aynı sayfayı, uygulamayı veya siteyi farklı tarayıcılarda test edin**. Kodunuzun hatalarını ayıkladığınızda, [sayfa denetçisi (Visual Studio)](https://msdn.microsoft.com/library/65880969-1ad2-47be-85b9-bb12c81bf209)dahil olmak üzere yüklü Web tarayıcıları arasında kolayca geçiş **yapabilirsiniz iletişim kutusunu** açmaya gerek yoktur. Hata ayıklama **Başlat** düğmesinin yanındaki **Standart** araç çubuğunda bulunan **hata ayıklama hedefi** listesini kullanabilirsiniz. Bu işlem, hata ayıklama veya sayfaları görüntüleme olarak hangi tarayıcıyı kullandığınızı hızlıca doğrulamak için kullanılır.

     ![Web tarayıcısı hata ayıklama seçeneklerini belirleyin](../ide/media/webbrowserdropdowntoolbar.png "WebBrowserDropDownToolbar")

- **Geçici kesme noktaları ayarlayın**. Geçerli kod satırında geçici bir kesme noktası oluşturabilir ve hata ayıklayıcıyı eşzamanlı olarak başlatabilirsiniz. Bu kod satırını vurduktan sonra, hata ayıklayıcı kesme moduna girer. Daha fazla bilgi için bkz. [hata ayıklayıcıyla kod aracılığıyla gezinme](../debugger/navigating-through-code-with-the-debugger.md).

     Bu özelliği kullanmak için CTRL + F10 tuşlarını seçin veya kesmek istediğiniz kod satırı için kısayol menüsünü açın ve ardından **Imlece Çalıştır**' ı seçin.

- **Hata ayıklama sırasında yürütme noktasını taşıyın**. Geçerli yürütme noktasını kodun farklı bir bölümüne taşıyabilir ve sonra bu noktadan hata ayıklamayı yeniden başlatabilirsiniz. Bu teknik, bu bölüme ulaşmak için gereken adımların tümünü yeniden oluşturmak zorunda kalmadan kod bölümünün hatalarını ayıklamak istiyorsanız kullanışlıdır. Daha fazla bilgi için bkz. [hata ayıklayıcıyla kod aracılığıyla gezinme](../debugger/navigating-through-code-with-the-debugger.md).

     Yürütme noktasını taşımak için, sarı ok ucunu aynı kaynak dosyasında bir sonraki ifadeyi ayarlamak istediğiniz konuma sürükleyin ve sonra hata ayıklamaya devam etmek için F5 tuşunu seçin.

- **Değişkenler için değer bilgilerini yakalayın**. Kodunuzda bir değişkene bir DataTip ekleyebilir ve hata ayıklama işlemi tamamlandıktan sonra değişken için bilinen son değere erişebilmek üzere onu sabitleyebilir. Daha fazla bilgi için bkz. [veri İpuçlarında veri değerlerini görüntüleme](../debugger/view-data-values-in-data-tips-in-the-code-editor.md).

     Bir DataTip eklemek için, hata ayıklayıcı kesme modunda olmalıdır. İmleci değişkenine yerleştirin ve ardından görüntülenen veri Ipucunda sabitle düğmesini seçin. Hata ayıklama durdurulduğunda, değişkeni içeren kod satırının yanına kaynak dosyada mavi bir pin simgesi görünür. Mavi PIN 'e işaret ederseniz, en son hata ayıklama oturumundan değişkenin değeri görünür.

- **Hemen penceresini temizleyin**. Tasarım zamanında, veya girerek [hemen pencerenin](../ide/reference/immediate-window.md) içeriğini silebilirsiniz. `>cls``>Edit.ClearAll`

     Ek komutlar hakkında daha fazla bilgi için bkz. [Visual Studio komut diğer adları](../ide/reference/visual-studio-command-aliases.md).

## <a name="managing-files-toolbars-and-windows"></a><a name="BKMK_Managing"></a> Dosyaları, araç çubuklarını ve pencereleri yönetme
 Herhangi bir zamanda birden fazla kod dosyasında çalışıyor olabilir ve bir uygulama geliştirirken çeşitli araç pencereleri arasında hareket edebilirsiniz. Aşağıdaki ipuçlarını kullanarak düzeninizi izleyebilirsiniz.

- **Sık kullandığınız dosyaları düzenleyicide görünür tutun**. Düzenleyicide kaç dosya açık olursa olsun, görünür kalması için dosyaları sekmenin sol tarafına sabitleyebilirsiniz.

     Bir dosyayı sabitlemek için dosyanın sekmesini seçin ve ardından **pin durumunu aç** düğmesini seçin.

- **Belgeleri ve pencereleri diğer Izleyicilere taşıyın**. Uygulama geliştirirken birden fazla izleyici kullanırsanız, düzenleyicide açık olan dosyaları başka bir monitöre taşıyarak uygulamanızın bölümlerinde daha kolay çalışabilirsiniz. Ayrıca, hata ayıklayıcı pencereleri gibi araç pencerelerini başka bir monitöre ve sekmeye yerleştir belge ve araç pencerelerini birlikte "Rafts" oluşturmak için de taşıyabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: pencereleri düzenleme ve yerleştirme](../misc/how-to-arrange-and-dock-windows.md).

     Ayrıca, başka bir **Çözüm Gezgini** örneği oluşturup başka bir monitöre taşıyarak dosyaları daha kolay bir şekilde yönetebilirsiniz. **Çözüm Gezgini**başka bir örneğini oluşturmak için **Çözüm Gezgini**bir kısayol menüsü açın ve sonra **Yeni Çözüm Gezgini Görünüm**' ü seçin.

- **Visual Studio 'da görünen yazı tiplerini özelleştirin**. IDE 'deki metin için kullanılan yazı tipini, boyutunu ve rengi değiştirebilirsiniz. Örneğin, düzenleyicideki belirli kod öğelerinin rengini ve araç pencereleri ya da IDE genelinde yazı tipi yüzünü özelleştirebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: yazı tiplerini ve renkleri değiştirme](../ide/how-to-change-fonts-and-colors-in-visual-studio.md) ve [nasıl yapılır: düzenleyicideki yazı tiplerini ve renkleri değiştirme](../ide/reference/how-to-change-fonts-and-colors-in-the-editor.md).

## <a name="see-also"></a>Ayrıca Bkz.
 [Sık kullanılan komutlar Için varsayılan klavye kısayolları](../ide/default-keyboard-shortcuts-for-frequently-used-commands-in-visual-studio.md) [nasıl yapılır: menüleri ve araç çubuklarını özelleştirme](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md) [Izlenecek yol: basit bir uygulama](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md) [erişilebilirlik ipuçları ve püf noktaları](../ide/reference/accessibility-tips-and-tricks.md) oluşturma
