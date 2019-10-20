---
title: Kod ve metin düzenleyicisinde kod yazma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.texteditor
dev_langs:
- JScript
- VB
- CSharp
helpviewer_keywords:
- code editor, word wrap
- outlining
- code, editing
- squiggles
- code editor, outlining
- code editor, error and warning markers
- word wrap
- code editor, syntax coloring
- code editor, go to definition
- diff
- code editor [Visual Studio]
- code editor, diff
- error and warning markers
- code editor, navigation bar
- code editor, customizing
- comment selection
- code editor, tabify
- brace matching
- code editor, line numbers
- printing
- code editor, brace matching
- code editor, squiggles
- code editor, features
- line numbers
- go to definition
- syntax coloring
- code editor, navigate to
- code editor, comparing files
- code editor, zoom
- code editor
- code files
- go to line
- tabify
- zoom
- navigate to
- line break characters
- code editor, virtual space
- code editor, change tracking
- code editor, comment selection
- code editor, printing
- virtual space
- code editor, line break characters
- code editor, go to line
- code
ms.assetid: cb53ab9a-5b76-4759-b9e8-7bf32298ecbe
caps.latest.revision: 46
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8793dd08a5ed4aaf83c1ddd52948db4c8b22034b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662632"
---
# <a name="writing-code-in-the-code-and-text-editor"></a>Kod ve Metin Düzenleyici'de Kod Yazma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
Visual Studio Düzenleyicisi, kodunuzu yazmanızı ve yönetmenizi kolaylaştıran birçok özellik sağlar. Anahat kullanarak farklı kod bloklarını genişletebilir ve daraltabilirsiniz. IntelliSense, **nesne tarayıcısı**ve çağrı hiyerarşisini kullanarak, kullanmakta olduğunuz kod hakkında daha fazla bilgi edinebilirsiniz. ' A **gidin**, **Tanıma Git**ve **tüm başvuruları bul**gibi özellikleri kullanarak kodunuzun içinde gezinebilirsiniz. Kod parçacıkları içeren kod blokları ekleyebilirsiniz ve **kullanımdan oluştur**gibi özellikleri kullanarak kod oluşturabilirsiniz. Daha önce Visual Studio 2015 düzenleyicisini kullanmadıysanız, hızlı bir genel bakış için [kodunuzu düzenleme](https://www.visualstudio.com/features/ide-vs) bölümüne bakın.

 Kodunuzu çeşitli yollarla görüntüleyebilirsiniz. Çözümünüzün bir sınıf görünümünü görmek için **sınıf görünümü** penceresini açabilir veya sınıf dosyalarınızın altındaki **Çözüm Gezgini** düğümleri genişletebilirsiniz.

 Tek veya birden çok dosya için metin arayabilir ve değiştirebilirsiniz. Daha fazla bilgi için bkz. [metni bulma ve değiştirme](../ide/finding-and-replacing-text.md). Normal ifadeler kullanırsanız, bul ve Değiştir ' in .NET normal ifadelerini kullandığına unutmayın. Daha fazla bilgi için bkz. [Visual Studio 'Da normal Ifadeler kullanma](../ide/using-regular-expressions-in-visual-studio.md).

 Farklı Visual Studio dilleri farklı özellik kümeleri sunar ve bazı durumlarda özellikler farklı dillerde farklı davranır. Bu farklılıkların birçoğu özelliklerin açıklamalarında belirtilmiştir, ancak daha fazla bilgi için belirli Visual Studio dillerinde bölümleri görebilirsiniz.

> [!IMPORTANT]
> Visual Studio sürümü ve kullandığınız ayarlar IDE 'deki özellikleri etkileyebilir. Bu konu başlığı altında açıklananlardan farklı olabilirler.

## <a name="editor-features"></a>Düzenleyici özellikleri

|||
|-|-|
|Sözdizimi renklendirme|Kod ve biçimlendirme dosyalarının bazı sözdizimi öğeleri, bunları ayırt etmek için farklı renklendirilir. Örneğin, anahtar sözcükler (Visual Basic `using` C# ve `Imports`) bir renktedir, ancak türler (`Console` ve `Uri` gibi) başka bir renktir. Diğer sözdizimi öğeleri de, dize sabit değerleri ve açıklamalar gibi renklendirilmiştir. C++diğer belirteçlerde türler, numaralandırmalar ve makrolar arasında ayrım yapmak için renk kullanır.<br /><br /> Her tür için varsayılan rengi görebilir ve **Araçlar** menüsünden açabileceğiniz [yazı tipleri ve renkler, ortam, Seçenekler iletişim kutusunda](../ide/reference/fonts-and-colors-environment-options-dialog-box.md)herhangi bir belirli bir söz dizimi öğesi için rengi değiştirebilirsiniz.|
|Hata ve uyarı Işaretleri|Kod eklerken ve çözümünüzü oluştururken, kodunuzda görüntülenen (a) farklı renkli dalgalı alt çizgiler (dalgalı çizgiler olarak bilinir) veya (b) açık bulbs görebilirsiniz. Red dalgalı çizgiler, sözdizimi hatalarını ifade eder, mavi derleyici hatalarını, yeşil bir uyarı gösterir ve mor diğer hata türlerini gösterir. [Hafif bulbs](../ide/perform-quick-actions-with-light-bulbs.md) , sorunlara yönelik düzeltmeler önerir ve düzeltmenin uygulanmasını kolaylaştırır.<br /><br /> **Araçlar/Seçenekler/ortam/yazı tipleri ve renkler** iletişim kutusunda her bir hata ve uyarı dalgalı çizgi için varsayılan rengi görebilirsiniz. **Sözdizimi hatası**, **derleyici hatası**, **Uyarı**ve **diğer hata**olup olmadığına bakın.|
|Ayraç eşleştirme|Ekleme noktası, bir kod dosyasındaki açık bir küme ayracı üzerine yerleştirildiğinde, hem hem de kapanış küme ayracı vurgulanır. Bu özellik, yanlış yerleştirilmiş veya eksik küme ayraçları hakkında anında geri bildirim sağlar. **Otomatik sınırlayıcı vurgulama** ayarı (**Araçlar/Seçenekler/metin düzenleyici**) ile küme ayracı ile eşleştirmeyi etkinleştirebilir veya devre dışı bırakabilirsiniz. **Yazı tipi ve renkler** ayarında vurgu rengini değiştirebilirsiniz (**Araçlar/Seçenekler/ortam**). **Küme ayracı Ile eşleşen (vurgu)** veya **ayraç eşleştirme (dikdörtgen)** arayın.|
|Satır numaraları|Satır numaraları, kod penceresinin sol kenar boşluğunda görüntülenebilir. Varsayılan olarak gösterilmezler. Bu seçeneği, **metin düzenleyici tüm diller** ayarlarında (**Araçlar/Seçenekler/metin düzenleyici/tüm diller**) açabilirsiniz. Bu dillerin ayarlarını değiştirerek (**Araçlar/Seçenekler/metin Düzenleyicisi/\<language >** ), bağımsız programlama dillerinin satır numaralarını görüntüleyebilirsiniz. Yazdırılacak satır numaraları için **Yazdır** iletişim kutusunda satır numaralarını dahil et ' i seçmeniz gerekir.|
|Değişiklik İzleme|Sol kenar boşluğunun rengi, bir dosyada yaptığınız değişiklikleri izlemenize olanak sağlar. Dosya açıldığı ancak kaydedilmediği için yaptığınız değişiklikler sol kenar boşluğunda (seçim kenar boşluğu olarak bilinir) sarı bir çubukla gösterilir. Değişiklikleri kaydettikten sonra (ancak dosyayı kapatmadan önce), çubuk yeşile döner. Dosyayı kaydettikten sonra bir değişikliği geri alırsanız, çubuk turuncu 'ı kapatır. Bu özelliği devre dışı bırakmak ve açmak için **metin Düzenleyicisi** ayarları 'Ndaki **Değişiklikleri İzle** seçeneğini değiştirin (**Araçlar/Seçenekler/metin düzenleyici**).|
|Kod ve metin seçme|Standart sürekli akış modunda veya kutu modunda metin seçebilirsiniz, burada satır kümesi yerine metnin dikdörtgen bir bölümünü seçersiniz. Kutu modunda seçim yapmak için, fareyi seçimin üzerine sürüklerken ALT tuşuna basın (veya ALT + SHIFT + \<arrow Key >). Seçim, seçimdeki ilk karakter ve son karakter tarafından tanımlanan dikdörtgenin içindeki tüm karakterleri içerir. Seçilen alana yazılan veya yapıştırılan her şey, her satırda aynı noktaya eklenir.|
|Yakınlaştır|CTRL tuşunu basılı tutarak ve kaydırma tekerleğini fareyle taşıyarak (ya da CTRL + SHIFT + tuşlarına basarak) herhangi bir kod penceresinde yakınlaştırıp uzaklaştırabilirsiniz. arttırmak ve CTRL + SHIFT +, azaltmak için). Ayrıca, belirli bir yakınlaştırma yüzdesi ayarlamak için kod penceresinin sol alt köşesindeki Yakınlaştır kutusunu da kullanabilirsiniz. Yakınlaştırma özelliği araç pencereleri içinde çalışmaz.|
|Sanal alan|Varsayılan olarak, Visual Studio düzenleyicilerinde bulunan satırlar son karakterden sonra sona erdir, böylece satırın sonundaki sağ ok tuşu imleci bir sonraki satırın başlangıcına taşıdıkça. Bazı diğer düzenleyicilerde, bir satır son karakterden sonra bitmez ve imlecinizi satıra istediğiniz yere yerleştirebilirsiniz. **Araçlar/Seçenekler/metin düzenleyici/tüm diller** ayarlarındaki düzenleyicide sanal alanı etkinleştirebilirsiniz. **Sanal alanı** veya **sözcük kaydırmayı**etkinleştirebileceğinizi, ancak ikisini de kullanabileceğinizi unutmayın.|
|Yazdırma|Dosya yazdırırken satır numaralarını dahil etmek veya daraltılmış kod bölgelerini gizlemek için **Yazdır** iletişim kutusundaki seçenekleri kullanabilirsiniz. **Sayfa yapısı** iletişim kutusunda, **sayfa üstbilgisi**' ni seçerek dosyanın tam yolunu ve adını yazdırmayı da tercih edebilirsiniz.<br /><br /> **Araçlar/Seçenekler/ortam/yazı tipleri ve renkler** iletişim kutusunda renkli yazdırma seçeneklerini belirleyebilirsiniz. Renkli yazdırmayı özelleştirmek için **ayarları göster** listesinden **Yazıcı** ' yı seçin. Bir dosyayı düzenleyen bir dosyayı yazdırmak için farklı renkler belirtebilirsiniz.|
|Küresel geri alma ve yineleme|**Düzenleme** menüsündeki **son genel eylemi geri al** ve **son genel eylemi yinele** komutları, birden çok dosyayı etkileyen genel eylemleri geri alır veya yineler. Genel eylemler bir sınıf veya ad alanını yeniden adlandırma, bir çözüm genelinde bul ve değiştir işlemi gerçekleştirme, bir veritabanını yeniden düzenleme ya da birden çok dosyayı değiştiren başka bir işlem yapma içerir. Bir eylemin uygulandığı çözümü kapattıktan sonra bile, geçerli Visual Studio oturumunda eylemlere genel geri alma ve yineleme komutlarını uygulayabilirsiniz.|

## <a name="advanced-editing-features"></a>Gelişmiş Özellikleri Düzenle
 **Düzenleme/Gelişmiş** alt menüsünde birçok gelişmiş özellik bulabilirsiniz. Bu özelliklerin hepsi tüm kod dosyası türleri için kullanılamaz.

|||
|-|-|
|Belgeyi Biçimlendir|Kod satırlarının uygun girintisini ayarlar ve küme ayraçlarını belgedeki satırlara ayırmak için taşımayın.|
|Biçim Seçimi|Kod satırlarının doğru girintilenmesini ayarlar ve küme ayraçlarını seçimdeki satırlara ayırmak için taşımayın.|
|Seçili satırları sekmeye Dönüştür|Baştaki boşlukları uygun yerlerde sekmeler olarak değiştirir.|
|Seçili satırları sekmeye Dönüştür|Baştaki sekmeleri boşluklara dönüştürür. Dosyanızdaki tüm boşlukları sekmelere (veya tüm sekmeleri boşluklara) dönüştürmek istiyorsanız, `Edit.ConvertSpacesToTabs` ve `Edit.ConvertTabsToSpaces` komutlarını kullanabilirsiniz. Bu komutlar Visual Studio menülerinde görünmez, ancak bunları hızlı erişim penceresinden veya komut penceresinden çağırabilirsiniz.|
|Büyük harf yap|Seçimdeki tüm karakterleri büyük harfe değiştirir veya seçim yoksa ekleme noktasındaki karakteri büyük harfe değiştirir.|
|Küçük harf yap|Seçimdeki tüm karakterleri küçük harfe çevirir veya seçim yoksa ekleme noktasındaki karakteri küçük harfe dönüştürür.|
|Belgeyi doğrula|JScript kod dosyalarını doğrular.|
|Yatay boşluğu Sil|Geçerli satırın sonundaki sekmeleri veya boşlukları siler.|
|Boşluğu görüntüle|Boşlukları, kabarık noktalar olarak ve ok olarak sekme olarak görüntüler. Bir dosyanın sonu dikdörtgen bir karakter olarak görüntülenir. **Araçlar/Seçenekler/metin düzenleyici/tüm diller/kelime kaydır/sözcük kaydırması için görünür glifleri göster** seçiliyse, bu glif de görüntülenir.|
|Sözcük Kaydırma|Belgedeki tüm satırların kod penceresinde görünür olmasını sağlar. Sözcük kaydırmayı, tüm diller ayarlarında (**Araçlar/Seçenekler/metin düzenleyici/tüm diller**) metin düzenleyicisinde devre dışı bırakabilirsiniz.|
|Seçimi açıklama kaldır|Seçime veya geçerli satıra Açıklama karakterleri ekler.|
|Açıklama seçimi|Seçim veya geçerli satırdan açıklama karakterlerini kaldırır.|
|Satır girintisini artır|Seçili satırlara veya geçerli satıra bir sekme (veya eşdeğer boşluk) ekler.|
|Satır girintisini azalt|Seçili satırlardan veya geçerli satırdan bir sekmeyi (veya eşdeğer alanları) kaldırır.|
|Etiket Seç|Etiketler (örneğin, XML veya HTML) içeren bir belgede etiketi seçer.|
|Etiket Içeriğini seçin|Etiketler (örneğin, XML veya HTML) içeren bir belgede, içeriği seçer.|

## <a name="navigate-in-the-code-window"></a>Kod penceresinde gezinme
 Bir belgede birçok farklı şekilde hareket edebilirsiniz. Standart işlemlere ek olarak, ekleme noktasını önceki konumlara taşımak veya ' de daha güncel konumlara geri dönmek için **geri git** (veya CTRL + eksi) ve araç çubuğundaki **İleri** (CTRL + SHIFT + eksi) düğmelerini kullanabilirsiniz. etkin belge. Bu düğmeler, ekleme noktasının son 20 konumunu korur.

 ![İleri ve geri gezinti düğmeleri](../ide/media/vs2015-nav-buttons.png "VS2015_Nav_buttons")

 Kodunuzun bir kuşbakışı görünümünü almak için bir kod penceresinde gelişmiş kaydırma çubuğunu da kullanabilirsiniz. Harita modunda, imleci yukarı ve aşağı kaydırma çubuğunun üzerinde hareket ettirdiğinizde kodun önizlemelerini görebilirsiniz. daha fazla bilgi Için, bkz. [nasıl yapılır: kaydırma çubuğunu özelleştirerek kodunuzu izleme](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md).

 Aşağıdaki komutlar koda özgü gezinti yöntemleridir:

|||
|-|-|
|@No__t_0line sayıya git >|(**Düzenle/git** veya CTRL + G): etkin belgedeki belirli bir satır numarasına gider.|
|Şuraya gidin|(**Düzenle/git** veya CTRL +,): etkin çözümde bir sembol veya dosya bulur. Bir sorgudan uygun bir eşleşen sonuçlar kümesi seçmenize yardımcı olur. Simgenin anahtar sözcüklere bölmek için ortası küçük harf ve alt çizgi karakterlerini kullanarak bir sembolde bulunan anahtar sözcükleri arayabilirsiniz.|
|Tüm Başvuruları Bul|(bağlam menüsü): çözümdeki seçili öğenin tüm başvurularını bulur.|
|Tanıma Git|(bağlam menüsü veya F12): seçili öğenin tanımını bulur.|
|Açıklama Özeti|(bağlam menüsü veya alt + F12): seçili öğenin tanımını bulur ve bir açılan pencerede görüntüler. Daha fazla bilgi için bkz. [nasıl yapılır: Açıklama tanımı kullanarak kodu görüntüleme ve düzenleme (alt + F12)](../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md).|
|Next yöntemi, Previous yöntemi|(**Düzenle/sonraki yöntem, önceki yöntem**) Visual Basic kod dosyalarında, ekleme noktasını farklı yöntemlere taşımak için bu komutları kullanın.|
|Başvuru vurgulama|Kaynak kodunda bir simgeye tıkladığınızda, söz konusu simgenin tüm örnekleri belgede vurgulanır. Vurgulanan semboller, bildirim ve başvuru içerebilir ve **tüm başvuruları** içeren diğer birçok sembol döndürülür. Bunlar sınıfların, nesnelerin, değişkenlerin, yöntemlerin ve özelliklerin adlarını içerir. Visual Basic kodda, birçok denetim yapısı için anahtar sözcükler de vurgulanır. İleri veya önceki vurgulanan simgeye gitmek için CTRL + SHIFT + aşağı ok veya CTRL + SHIFT + yukarı ok tuşlarına basın. **Araçlar/Seçenekler/ortam/yazı tipleri ve renkler/vurgulanan başvuru** içindeki vurgulama rengini değiştirebilirsiniz.|
|Kodla ilgili bilgileri bulma|Kod düzenleyicisinde CodeLens kullandığınızda, değişiklikler ve bu değişiklikleri kimin yaptığını, başvuruları, hataları, iş öğelerini, kod incelemelerini ve birim test durumunu oluşturan belirli kod hakkındaki bilgileri bulabilirsiniz. CodeLens, Team Foundation Server Visual Studio Enterprise kullandığınızda bir başlık görünümü gibi çalışır. Bkz. [kod değişikliklerini ve diğer geçmişi bulma](../ide/find-code-changes-and-other-history-with-codelens.md).|

 Ayrıca, bir kod dosyasında gezinmek için, kod penceresinin üstünde görüntülenen iki açılan kutu olan **Gezinti çubuğunu**da kullanabilirsiniz. Bu çubuk, doğrudan belirli bir türe veya bir tür içindeki üyelerden birine gitmenizi sağlar. Gezinti çubuğu Visual Basic, C#ve C++ kod dosyaları ile görünür.

 Gezinti çubuğunu gizlemek için, metin düzenleyici tüm diller ayarlarında (**Araçlar/Seçenekler/metin düzenleyici/tüm diller**) **Gezinti çubuğu** seçeneğini değiştirin veya tek dillerin ayarlarını değiştirebilirsiniz. Açılan kutularda aşağıdaki gibi gezinebilirsiniz:

- Odağı kod penceresinden gezinti çubuğuna kaydırmak için CTRL + F2 tuş birleşimine basın.

- Gezinti çubuğundan kod penceresine odaklanmak için ESC tuşuna basın.

- Odağı gezinti çubuğundaki öğeden öğeye kaydırmak için TAB tuşuna basın.

- Odağa sahip olan ve IDE 'ye döndürülen gezinti çubuğu öğesini seçmek için ENTER tuşuna basın

- Bir sınıfa veya türe gitmek için sol taraftaki açılan menüde adına tıklayın.

- Bir sınıftaki yordama doğrudan gitmek için sağ açılan listede bir yordama tıklayın.

  Kısmi bir sınıfta, geçerli kod dosyası dışında tanımlanan Üyeler gri olabilir.

## <a name="find-code-using-navigate-to"></a>Git kullanarak kod bulma
Visual Studio 'nun "git" komutu, kod dosyalarında belirtilen öğeleri hızlı bir şekilde bulmanıza yardımcı olmak için kodunuzun odaklanmış bir aramasını yapar, dosya yolları ve kod sembolleri. Dosyalarda bul veya bul gibi diğer metin aramalarından farklı olarak, arama Için dosya, form ve kod modülleri gibi gerçek kodun yaşadığı alanlara yönelik aramayı sınırlar ' a gidin. Örneğin, tüm çözümdeki dosyalarda bul veya bul ' u kullanarak bir ASP.NET Web uygulamasında bir dize arıyorsanız, kod açıklamalarında dize örnekleri de dahil olmak üzere birkaç isabetle karşılaşabilirsiniz. Bununla birlikte, ' a git ' i kullanarak yalnızca tek bir işlev alabilir ve kod açıklamalarında dize örneklerini yok sayın.

### <a name="navigate-code-using-navigate-to"></a>Git kullanarak koda gitme

1. Visual Studio 'da bir çözüm veya klasör açın.
1. Ana menüde **Düzenle** **' yi seçin, git '** i seçin veya **CTRL +,** tuşlarına basın.

    Kod Düzenleyicisinin üst köşesinde küçük bir metin kutusu görünür.
1. Metin kutusuna bulmak istediğiniz kod öğesinin adını girin.

    ![Pencereye git](../ide/media/vside-navigatetowindow.png "Pencereye git")

    Siz yazarken, sonuçlar metin kutusunun altındaki bir açılan listede görüntülenir.
1. Bir öğeye gitmek için listeden seçin.

### <a name="filter-your-search"></a>Aramanızı filtreleyin

Aramanızı yalnızca kod sembolleriyle sınırlamak için, "\@" karakteriyle sorguya gitmeniz gerekir. Örneğin, `@application` arıyorsanız, örneğin, yalnızca içinde "uygulama" sözcüğünü içeren sınıflar gibi görüntüler ' e gidin.

Kodunuzda ortası büyük harfleri kullanırsanız, yalnızca kod öğesi adının büyük harflerini girerek kod öğelerini daha hızlı bulabilirsiniz. Örneğin, kodunuzun `ViewSwitcher` adlı bir bileşeni varsa, gidilecek pencereye yalnızca büyük harfleri (`"VS"`) girerek bulabilirsiniz.

![Pencereye gitme-büyük harfler ile arama](../ide/media/vside-capitalsearch.png "Pencereye gitme-büyük harfler ile arama")

Kodunuzun uzun adlara sahip olması durumunda bu özellik özellikle faydalıdır.

## <a name="customize-the-editor"></a>Düzenleyiciyi özelleştirme
 **Ayarları içeri ve dışarı**aktarma: ayarları başka bir geliştiriciyle paylaşabilir, ayarlarınızı bir standart ile uyumlu yapabilir veya **Araçlar** menüsündeki **Içeri ve dışarı aktarma ayarları Sihirbazı** 'nı kullanarak Visual Studio varsayılan ayarlarına dönebilirsiniz. Genel ayarları veya dili ve projeye özgü ayarları değiştirebilirsiniz.

 **Klavye eşleme**: Araçlar/Seçenekler/ortam/klavye ayarları ' nda yeni kısayol tuşlarını tanımlayabilir veya var olanları yeniden tanımlayabilirsiniz. Kısayol tuşları hakkında daha fazla bilgi için bkz. [varsayılan klavye kısayolları](../ide/default-keyboard-shortcuts-in-visual-studio.md).

 Dile özgü düzenleyici seçenekleri hakkında bilgi için aşağıdakilere bakın:

- [Visual Basic ayarları](https://msdn.microsoft.com/library/2712b3b1-18f2-430c-ae91-28468bbf5f32)

- [C# için Visual Studio Geliştirme Ortamını Kullanma](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md)

- [Seçenekler, Metin Düzenleyici, JavaScript, Biçimlendirme](../ide/reference/options-text-editor-javascript-formatting.md)

## <a name="in-this-section"></a>Bu bölümde

- [Metin Bulma ve Değiştirme](../ide/finding-and-replacing-text.md)

- [Kodlamalar ve Satır Sonları](../ide/encodings-and-line-breaks.md)

- [Anahat Oluşturma](../ide/outlining.md)

- [Yeniden Düzenle](../ide/refactoring-in-visual-studio.md)

- [Üretkenlik İpuçları](../ide/productivity-tips-for-visual-studio.md)

- [IntelliSense Kullanma](../ide/using-intellisense.md)

- [Düzenleyiciyi Özelleştirme](../ide/customizing-the-editor.md)

- [Nasıl Yapılır: Kaydırma Çubuğunu Özelleştirerek Kodunuzu İzleme](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md)

- [Nasıl yapılır: Özet Tanımı'nı Kullanarak Kodu Görüntüleme ve Düzenleme (Alt+F12)](../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)

- [Ampullerle hızlı eylemler gerçekleştirme](../ide/perform-quick-actions-with-light-bulbs.md)

- [Kod Parçacıkları](../ide/code-snippets.md)

- [Araç Kutusunu Kullanma](../ide/using-the-toolbox.md)

- [Kod Yapısını Görüntüleme](../ide/viewing-the-structure-of-code.md)

- [Kodda Yer İşaretleri Ayarlama](../ide/setting-bookmarks-in-code.md)

- [Görev Listesini Kullanma](../ide/using-the-task-list.md)

- [Kod değişikliklerini ve diğer geçmişi bulma](../ide/find-code-changes-and-other-history-with-codelens.md)

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio IDE](../ide/visual-studio-ide.md)
