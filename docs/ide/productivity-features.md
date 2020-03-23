---
title: Üretkenlik ipuçları
ms.date: 2/21/2019
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fd85565ee573015737ab815258914bec89ab9369
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596989"
---
# <a name="productivity-tips-for-visual-studio"></a>Visual Studio için verimlilik ipuçları

Bu makaleler, kodunuzu daha hızlı ve verimli bir şekilde yazmanıza, gezinmenize ve hata ayıklamanıza yardımcı olan Visual Studio özellikleriyle ilgili ipuçlarını tartışır.

Yararlı klavye kısayolları hakkında daha fazla bilgi için [Bkz. Verimlilik kısayolları.](../ide/productivity-shortcuts.md) Komut kısayollarının tam listesi için [Varsayılan klavye kısayolları'na](../ide/default-keyboard-shortcuts-in-visual-studio.md)bakın.

## <a name="write-code"></a>Kod yazma

Aşağıdaki özellikleri kullanarak kodu daha hızlı yazın.

- **Kolaylık komutlarını kullanın.** Visual Studio, yaygın düzenleme görevlerini daha hızlı gerçekleştirmenize yardımcı olacak çeşitli komutlar içerir. Örneğin, bir kodu kopyalamak, imleci yeniden konumlandırmak ve sonra yapıştırmak zorunda kalmadan kodu kolayca çoğaltmak için bir komut seçebilirsiniz. **Yinelenen'i** **Edit'i** > seçin veya **Ctrl**+**E**,**V**tuşuna basın. Ayrıca,**Gelişmiş**Genişletme Seçimini Edit'i seçerek veya > **Gelişmiş** > **Sözleşme****Seçimini** +**-**+ **=**  >  **Edit'i** > seçerek veya **Shift**+Alt veya **Shift**+ **Edit****Alt'a** basarak metin seçimini hızla genişletebilir veya sözleşmeye dahil edebilirsiniz.**Alt**

- **IntelliSense kullanın.** Editöre kod girdiğinizde, Liste Üyeleri, Parametre Bilgileri, Hızlı Bilgi, İmza Yardımı ve Tam Word gibi IntelliSense bilgileri görüntülenir. Bu özellikler metnin bulanık eşleştirilmesini destekler; örneğin, Liste Üyeleri için sonuç listeleri yalnızca girdiğiniz karakterlerle başlayan girişleri değil, adlarının herhangi bir yerinde karakter birleşimini içeren girişleri de içerir. Daha fazla bilgi için Bkz. [IntelliSense'i kullan.](../ide/using-intellisense.md)

- **Kodu girerken IntelliSense seçeneklerinin otomatik eklemesini değiştirin.** IntelliSense'i öneri moduna geçerek, IntelliSense seçeneklerinin yalnızca açıkça seçerseniz eklenmiş olduğunu belirtebilirsiniz.

     Öneri modunu etkinleştirmek için **Ctrl**+**Alt**+**Spacebar** tuşlarını seçin veya menü çubuğunda**IntelliSense** > **Geçiş Tamamlama Modunu** **Edit'i** > seçin.

- **Kod parçacıkları kullanın.** Yerleşik parçacıkları kullanabilir veya kendi parçacıklarınızı oluşturabilirsiniz.

     Menü çubuğuna bir parçacık eklemek için,**IntelliSense** > **Ekle Snippet'i** veya **Surround'u** **Edit'i** > seçin veya bir dosyadaki kısayol menüsünü açın ve **Snippet** > **Ekle Snippet** veya Surround **With'i**seçin. Daha fazla bilgi için [Kod Parçacıkları'na](../ide/code-snippets.md)bakın.

- **Kod hatalarını satır satır düzeltme.** Hızlı Eylemler, kodu tek bir eylemle kolayca yeniden düzenlemenize, oluşturmanıza veya başka bir şekilde değiştirmenize izin sağlar. Bu işlemler tornavida ![simgesi](media/screwdriver-icon.png) veya ampul ![Ampul simge](media/light-bulb-icon.png) simgeleri kullanılarak veya **Alt**+**Enter** veya **Ctrl**+tuşuna basarak**uygulanabilir.** imleciniz uygun kod satırında olduğunda. Daha fazla bilgi için [Hızlı Eylemler'e](quick-actions.md) bakın.

- **Kod öğesinin tanımını göster ve edin.** Üye, değişken veya yerel öğe gibi bir kod öğesinin tanımlandığı modülü hızla gösterebilir ve değiştirebilirsiniz.

    Bir açılır pencerede bir tanım açmak için, öğeyi vurgulayın ve ardından **Alt**+**F12** tuşlarını seçin veya öğe için kısayol menüsünü açın ve ardından **Peek Definition'ı**seçin. Ayrı bir kod penceresinde bir tanım açmak için, öğe için kısayol menüsünü açın ve ardından **Tanıma Git'i**seçin.

- **Örnek uygulamaları kullanın.** [Microsoft Developer Network'ten](https://code.msdn.microsoft.com/)örnek uygulamaları indirip yükleyerek uygulama geliştirmeyi hızlandırabilirsiniz. Ayrıca, belirli bir teknolojiyi veya programlama kavramını, o alan için bir Örnek Paketi indirip keşfederek de öğrenebilirsiniz.

## <a name="navigate-within-your-code"></a>Kodunuz içinde gezinme

Kodunuzda belirli konumları daha hızlı bulmak ve taşımak için çeşitli teknikler kullanabilirsiniz.

- **Kod yer imi satırları**. Bir dosyadaki belirli kod satırlarına hızla gitmek için yer imlerini kullanabilirsiniz.

    Yer imi ayarlamak için, menü çubuğunda**Yer İşaretlerini** > **Ayarla Yer İşareti İşaretini** **Edin'i** > seçin. **Yer İşaretleri** penceresinde bir çözüm için yer imlerinin tümlerini görüntüleyebilirsiniz. Daha fazla bilgi için [bkz.](../ide/setting-bookmarks-in-code.md)

- **Dosyadaki sembol tanımlarını arayın.** Sembol tanımlarını ve dosya adlarını bulmak için bir çözüm içinde arama yapabilirsiniz, ancak arama sonuçları ad boşluklarını veya yerel değişkenleri içermez.

   Bu özelliğe erişmek için menü çubuğunda**Gezin'i** **edin'i** > seçin.

- **Kodunuzun genel yapısına göz atın.** **Çözüm Gezgini'nde,** projelerinizde sınıflarda ve bunların türlerini ve üyelerinde arama yapabilir ve göz atabilirsiniz. Ayrıca sembolleri arayabilir, yöntemin Çağrı Hiyerarşisi'ni görüntüleyebilir, simge referansları bulabilir ve diğer görevleri gerçekleştirebilirsiniz. **Çözüm Gezgini'nde**bir kod öğesi seçerseniz, ilişkili dosya **Önizleme** sekmesinde açılır ve imleç dosyadaki öğeye taşınır. Daha fazla bilgi için bkz. [kodun yapısını görüntüleyin.](../ide/viewing-the-structure-of-code.md)

## <a name="find-items-faster"></a>Öğeleri daha hızlı bulma

Geçerli göreviniz için yalnızca alakalı bilgileri göstermek için araç pencerelerinin içeriğini filtrelemenin yanı sıra komutlar, dosyalar ve seçenekler için IDE'de arama yapabilirsiniz.

- **Araç pencerelerinin içeriğini filtreleyin.** **Araç Kutusu,** **Özellikler** penceresi ve **Çözüm Gezgini**gibi birçok araç penceresinin içeriğinde arama yapabilir, ancak yalnızca adları belirttiğiniz karakterleri içeren öğeleri görüntüleyebilirsiniz.

- **Yalnızca gidermek istediğiniz hataları görüntüleyin.** **Hata Listesi** araç çubuğundaki **Filtre** düğmesini seçerseniz, **Hata Listesi** penceresinde görünen hata sayısını azaltabilirsiniz. Yalnızca düzenleyicide açık olan dosyalardaki hataları, yalnızca geçerli dosyadaki hataları veya geçerli projedeki hataları görüntüleyebilirsiniz. Belirli hataları bulmak için **Hata Listesi** penceresinde de arama yapabilirsiniz.

- **İletişim kutularını, menü komutlarını, seçenekleri ve daha fazlasını bulun.** Arama kutusuna, bulmaya çalıştığınız öğeler için anahtar kelimeler veya ifadeler girin. Örneğin, **yeni proje**girerseniz aşağıdaki seçenekler görüntülenir:

   ::: moniker range="vs-2017"

   !['Yeni proje' için Hızlı Lansman Sonuçları](../ide/media/productivity_quicklaunch.png)

   **Hızlı Başlatma,** yeni bir proje oluşturmak, projeye yeni bir öğe eklemek ve diğerleri arasında **Seçenekler** iletişim kutusundaki **Projeler ve Çözümler** sayfasına bağlantılar görüntüler. Arama sonuçları proje dosyalarını ve araç pencerelerini de içerebilir.

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   !['Yeni proje' için arama sonuçları](../ide/media/vs-2019/productivity-quick-launch-new-project.png)

   ::: moniker-end

   Doğrudan arama kutusuna atlamak için **Ctrl**+**Q** tuşuna basın.

## <a name="debug-code"></a>Hata ayıklama kodu

Hata ayıklama çok zaman tüketebilir, ancak aşağıdaki ipuçları işlemi hızlandırmanıza yardımcı olabilir.

- **Aynı sayfayı, uygulamayı veya siteyi farklı tarayıcılarda test edin.** Kodunuzu hata ayıklama olarak, [sayfa denetçisi (Visual Studio)](https://msdn.microsoft.com/Library/65880969-1ad2-47be-85b9-bb12c81bf209)da dahil olmak üzere yüklü web tarayıcıları arasında kolayca geçiş yapabilirsiniz, iletişim kutusu **ile Gözat'ı** açmak zorunda kalmadan. Hata ayıklama veya sayfaları görüntülediğiniz sırada hangi tarayıcıyı kullandığınızı hızlı bir şekilde doğrulamak **için, Hata Ayıklama** Düğmesini Başlat'ın yanındaki **Standart** araç çubuğunda bulunan **Hata Ayıklama Hedef** listesini kullanabilirsiniz.

    ![Web tarayıcısı hata ayıklama seçeneklerini seçin](../ide/media/webbrowserdropdowntoolbar.png)

- **Geçici kesme noktaları ayarlayın.** Geçerli kod satırında geçici bir kesme noktası oluşturabilir ve hata ayıklayıcıyı aynı anda başlatabilirsiniz. Bu kod satırına vurduğunuzda, hata ayıklayıcı kesme moduna girer. Daha fazla bilgi için [hata ayıklayıcıyla kodda gezine'ye](../debugger/navigating-through-code-with-the-debugger.md)bakın.

    Bu özelliği kullanmak için **Ctrl**+**F10** tuşlarını seçin veya kırmak istediğiniz kod satırı için kısayol menüsünü açın ve ardından **İmlec'e Koş'u**seçin.

- **Hata ayıklama sırasında yürütme noktasını taşıyın.** Geçerli yürütme noktasını kodun farklı bir bölümüne taşıyabilir ve ardından bu noktadan hata ayıklamayı yeniden başlatabilirsiniz. Bu teknik, bu bölüme ulaşmak için gereken tüm adımları yeniden oluşturmak zorunda kalmadan kod bir bölümünü hata ayıklamak istiyorsanız yararlıdır. Daha fazla bilgi için [hata ayıklayıcıyla kodda gezine'ye](../debugger/navigating-through-code-with-the-debugger.md)bakın.

     Yürütme noktasını taşımak için, sarı ok başını aynı kaynak dosyasında bir sonraki ifadeyi ayarlamak istediğiniz bir konuma sürükleyin ve hata ayıklama devam etmek için **F5** tuşunu seçin.

- **Değişkenler için değer bilgilerini yakalayın.** Kodunuzdaki bir değişkene bir DataTip ekleyebilir ve hata ayıklama tamamlandıktan sonra değişkeniçin bilinen son değere erişebilmeniz için onu sabitleyebilirsiniz. Daha fazla bilgi için bkz. [Veri İpuçları'ndaki veri değerlerini görüntüleyin.](../debugger/view-data-values-in-data-tips-in-the-code-editor.md)

     Veri İpucu eklemek için hata ayıklamanın kesme modunda olması gerekir. İmleci değişkenin üzerine yerleştirin ve ardından görünen DataTip'teki pin düğmesini seçin. Hata ayıklama durdurulduğunda, değişkeni içeren kod satırının yanındaki kaynak dosyada mavi bir pin simgesi görüntülenir. Mavi iğneyi işaret ederseniz, en son hata ayıklama oturumundaki değişkenin değeri görüntülenir.

- **Hemen pencereyi temizleyin.** [Hemen penceresinin](../ide/reference/immediate-window.md) içeriğini tasarım zamanında girerek `>cls` veya`>Edit.ClearAll`

     Ek komutlar hakkında daha fazla bilgi için [Visual Studio komut diğer adlarına](../ide/reference/visual-studio-command-aliases.md)bakın.

## <a name="access-visual-studio-tools"></a>Visual Studio araçlarına erişin

Başlat menüsüne veya görev çubuğuna sabitlerseniz, Geliştirici Komut Istem'ine veya başka bir Visual Studio aracına hızla erişebilirsiniz.

::: moniker range="vs-2017"

1. Windows Gezgini'nde *%ProgramData%\Microsoft\Windows\Başlat Menüsü\Programlar\Visual Studio 2017\Visual Studio Tools'a*göz atın.

::: moniker-end

::: moniker range=">=vs-2019"

1. Windows Gezgini'nde *%ProgramData%\Microsoft\Windows\Başlat Menüsü\Programlar\Visual Studio 2019\Visual Studio Tools'a*göz atın.

::: moniker-end

2. **Geliştirici Komut Ustem**için bağlam menüsünü sağ tıklatın veya açın ve ardından **Başlat'a** Sabitle'yi veya **görev çubuğuna Sabitle'yi**seçin.

## <a name="manage-files-toolbars-and-windows"></a>Dosyaları, araç çubuklarını ve pencereleri yönetme

Herhangi bir anda, birden çok kod dosyasında çalışıyor ve bir uygulama geliştirirken çeşitli araç pencereleri arasında hareket ediyor olabilirsiniz. Aşağıdaki ipuçlarını kullanarak düzenli tutabilirsiniz:

- **Sık kullandığınız dosyaları düzenleyicide görünür tutun.** Dosyaları, düzenleyicide kaç dosya nın açık olduğuna bakılmaksızın görünür kalması için sekmenin sol tarafına iyi sabitleyebilirsiniz.

   Bir dosyayı sabitlemek için, dosyanın sekmesini seçin ve ardından **Geçiş Pin Durumu** düğmesini seçin.

- **Belgeleri ve pencereleri diğer monitörlere taşıyın.** Uygulama geliştirirken birden fazla monitör kullanıyorsanız, düzenleyicide açık olan dosyaları başka bir monitöre taşıyarak uygulamanızın bazı kısımları üzerinde daha kolay çalışabilirsiniz. Hata ayıklama pencereleri gibi araç pencerelerini de "sallar" oluşturmak için başka bir monitör ve sekme dock belge ve araç pencerelerine taşıyabilirsiniz. Daha fazla bilgi için [Visual Studio'daki pencere düzenlerini özelleştir'e](../ide/customizing-window-layouts-in-visual-studio.md)bakın.

   Ayrıca, **Solution Explorer'ın** başka bir örneğini oluşturup başka bir monitöre taşıyarak dosyaları daha kolay yönetebilirsiniz. **Çözüm Gezgini'nin**başka bir örneğini oluşturmak **için, Solution Explorer'da**bir kısayol menüsü açın ve ardından **Yeni Çözüm Gezgini Görünümü'nü**seçin.

- **Visual Studio'da görünen yazı tiplerini özelleştirin.** IDE'deki metin için kullanılan yazı tipi yüzünü, boyutunu ve rengini değiştirebilirsiniz. Örneğin, düzenleyicideki belirli kod öğelerinin rengini ve araç pencerelerinde veya IDE boyunca yazı tipi yüzünü özelleştirebilirsiniz. Daha fazla bilgi için [bkz: Yazı tiplerini ve renkleri ve](../ide/how-to-change-fonts-and-colors-in-visual-studio.md) [nasıl değiştirilir: Editördeki yazı tiplerini ve renklerini değiştirin.](../ide/reference/how-to-change-fonts-and-colors-in-the-editor.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio ipuçları ve püf noktaları blog yazısı](https://devblogs.microsoft.com/visualstudio/visual-studio-tips-and-tricks/)
- [Sık kullanılan komutlar için varsayılan klavye kısayolları](../ide/default-keyboard-shortcuts-for-frequently-used-commands-in-visual-studio.md)
- [Menüleri ve araç çubuklarını özelleştirme](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md)
- [Walkthrough: Basit bir uygulama oluşturma](../get-started/csharp/tutorial-wpf.md)
- [Erişilebilirlik ipuçları ve püf noktaları](../ide/reference/accessibility-tips-and-tricks.md)
