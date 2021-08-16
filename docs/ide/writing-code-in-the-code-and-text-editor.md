---
title: Kod Düzenleyicisi özellikleri
description: kodunuzu ve metninizi yazmanızı ve yönetmenizi kolaylaştırmak için Visual Studio 'deki kod düzenleyicisinin sağladığı özellikler hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 02/23/2018
ms.topic: conceptual
helpviewer_keywords:
- code, editing [Visual Studio]
- code editor [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 428c86247686987c6b32c1b6dc109c338f590cd50593c41144e880add7c73b03
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121288990"
---
# <a name="features-of-the-code-editor"></a>Kod düzenleyicisinin özellikleri

Visual Studio düzenleyicisi, kodunuzu ve metninizi yazmanızı ve yönetmenizi kolaylaştıran birçok özellik sağlar. Anahat kullanarak farklı kod bloklarını genişletebilir ve daraltabilirsiniz. IntelliSense, **nesne tarayıcısı** ve çağrı hiyerarşisini kullanarak kod hakkında daha fazla bilgi edinebilirsiniz. **Git** gibi özellikleri kullanarak kodu bulabilir, **tanıma gidebilirsiniz** ve **tüm başvuruları bulabilirsiniz**. Kod parçacıkları içeren kod blokları ekleyebilirsiniz ve **kullanımdan oluştur** gibi özellikleri kullanarak kod oluşturabilirsiniz. daha önce Visual Studio düzenleyicisini kullanmadıysanız, bkz. [kod düzenleyicisini kullanmayı öğrenin](../get-started/tutorial-editor.md).

> [!NOTE]
> bu konu Windows Visual Studio için geçerlidir. Mac için Visual Studio için bkz. [kaynak düzenleyicisi (Mac için Visual Studio)](/visualstudio/mac/source-editor).

Kodunuzu çeşitli yollarla görüntüleyebilirsiniz. Varsayılan olarak **Çözüm Gezgini** , kodunuzu dosyalara göre düzenlenmiş olarak gösterir. Kodunuzu sınıflara göre düzenlenmiş olarak görüntülemek için pencerenin alt kısmındaki **sınıf görünümü** sekmesine tıklayabilirsiniz.

Tek veya birden çok dosyada metin arayabilir ve değiştirebilirsiniz. Daha fazla bilgi için bkz. [metni bulma ve değiştirme](../ide/finding-and-replacing-text.md). Metni bulmak ve değiştirmek için normal ifadeleri kullanabilirsiniz. Daha fazla bilgi için bkz. [Visual Studio normal Ifadeleri kullanma](../ide/using-regular-expressions-in-visual-studio.md).

farklı Visual Studio diller farklı özellik kümeleri sunar ve bazı durumlarda özellikler farklı dillerde farklı davranır. bu farklılıkların birçoğu özelliklerin açıklamalarında belirtilmiştir, ancak daha fazla bilgi için belirli Visual Studio dillerdeki bölümleri görebilirsiniz.

## <a name="editor-features"></a>Düzenleyici özellikleri

|Özellik|Açıklama|
|-|-|
|Sözdizimi renklendirme|Kod ve biçimlendirme dosyalarının bazı sözdizimi öğeleri, bunları ayırt etmek için farklı renklendirilir. örneğin, ( `using` C# ve Visual Basic gibi) anahtar kelimeleri `Imports` bir renktedir, ancak türler ( `Console` ve gibi `Uri` ) başka bir renktir. Diğer sözdizimi öğeleri de, dize sabit değerleri ve açıklamalar gibi renklendirilmiştir. C++, diğer belirteçlerin yanı sıra türler, numaralandırmalar ve makroları birbirinden ayırt etmek için renk kullanır.<br /><br /> Her tür için varsayılan rengi görebilir ve **Araçlar** menüsünden açabileceğiniz [yazı tipleri ve renkler, ortam, Seçenekler iletişim kutusunda](../ide/reference/fonts-and-colors-environment-options-dialog-box.md)herhangi bir belirli bir söz dizimi öğesi için rengi değiştirebilirsiniz.|
|Hata ve uyarı Işaretleri|Kod eklerken ve çözümünüzü oluştururken, kodunuzda görüntülenen (a) farklı renkli dalgalı alt çizgiler (dalgalı çizgiler olarak bilinir) veya (b) açık bulbs görebilirsiniz. Red dalgalı çizgiler, sözdizimi hatalarını ifade eder, mavi derleyici hatalarını, yeşil bir uyarı gösterir ve mor diğer hata türlerini gösterir. [Hızlı eylemler](../ide/quick-actions.md) sorunlara yönelik düzeltmeler önerir ve düzeltmenin uygulanmasını kolaylaştırır.<br /><br /> Her bir hata için varsayılan rengi ve **araç**  >  **seçenekleri**  >  **ortam**  >  **yazı tipleri ve renkler** iletişim kutusunda bir uyarı dalgalı çizgi ' yi görürsünüz. **Sözdizimi hatası**, **derleyici hatası**, **Uyarı** ve **diğer hata** olup olmadığına bakın.|
|Ayraç eşleştirme|Ekleme noktası, bir kod dosyasındaki açık bir küme ayracı üzerine yerleştirildiğinde, hem hem de kapanış küme ayracı vurgulanır. Bu özellik, yanlış yerleştirilmiş veya eksik küme ayraçları hakkında anında geri bildirim sağlar. **Otomatik sınırlayıcı vurgulama** ayarı (**Araçlar**  >  **Seçenekler**  >  **metin Düzenleyicisi**) ile, parantez ile eşleştirmeyi etkinleştirebilir veya devre dışı bırakabilirsiniz. **Yazı tipi ve renkler** ayarında vurgu rengini değiştirebilirsiniz (**Araçlar**  >  **Seçenekler**  >  **ortamı**). **Küme ayracı Ile eşleşen (vurgu)** veya **ayraç eşleştirme (dikdörtgen)** arayın.|
|Yapı görselleştiricisi|Noktalı çizgiler, kod dosyalarında eşleşen küme ayraçlarını, açma ve kapatma küme ayracı çiftlerini daha kolay görmenizi sağlar. Bu, kod tabanınızdaki kodu daha hızlı bir şekilde bulmanıza yardımcı olabilir. Bu satırları **Araçlar**  Seçenekler metin Düzenleyicisi Genel sayfasındaki görüntü bölümünde **yapıyı göster yönergeleriyle** açabilir veya kapatabilirsiniz  >    >    >   .|
|Satır numaraları|Satır numaraları, kod penceresinin sol kenar boşluğunda görüntülenebilir. Varsayılan olarak gösterilmezler. Bu seçeneği, **metin düzenleyici tüm diller** ayarlarında (**Araçlar**  >  **Seçenekler**  >  **metin düzenleyici**  >  **tüm diller**) açabilirsiniz. Bu dillerin ayarlarını değiştirerek, bireysel programlama dilleri için satır numaralarını görüntüleyebilirsiniz (**Araçlar**  >  **Seçenekler**  >  **metin Düzenleyicisi**  >  **\<language>** ). Yazdırılacak satır numaraları için **Yazdır** iletişim kutusunda **satır numaralarını dahil et** ' i seçmeniz gerekir.|
|Değişiklik İzleme|Sol kenar boşluğunun rengi, bir dosyada yaptığınız değişiklikleri izlemenize olanak sağlar. Dosya açıldığı ancak kaydedilmediği için yaptığınız değişiklikler sol kenar boşluğunda (seçim kenar boşluğu olarak bilinir) sarı bir çubukla gösterilir. Değişiklikleri kaydettikten sonra (ancak dosyayı kapatmadan önce), çubuk yeşile döner. Dosyayı kaydettikten sonra bir değişikliği geri alırsanız, çubuk turuncu 'ı kapatır. Bu özelliği devre dışı bırakmak ve açmak için **metin Düzenleyicisi** ayarları 'ndaki (**Araçlar**   >  **Seçenekler**  >  **metin Düzenleyicisi**) değişiklikleri izle seçeneğini değiştirin.|
|Kod ve metin seçme|Standart sürekli akış modunda veya kutu modunda metin seçebilirsiniz, burada satır kümesi yerine metnin dikdörtgen bir bölümünü seçersiniz. Kutu modunda seçim yapmak için, fareyi seçimin üzerine sürüklerken **alt** tuşuna basın (veya **alt** + **SHIFT** tuşuna basın + **\<arrow key>** ). Seçim, seçimdeki ilk karakter ve son karakter tarafından tanımlanan dikdörtgenin içindeki tüm karakterleri içerir. Seçilen alana yazılan veya yapıştırılan her şey, her satırda aynı noktaya eklenir.|
|Zoom|Herhangi bir kod penceresinde, **CTRL** tuşunu basılı tutarak ve kaydırma tekerleğini fareyle (ya da **CTRL** + **+ Shift** tuşlarına basarak) yakınlaştırıp uzaklaştırabilirsiniz + **.** arttırmak ve **CTRL** + **tuşlarını** +  azaltmak için). Ayrıca, belirli bir yakınlaştırma yüzdesi ayarlamak için kod penceresinin sol alt köşesindeki **Yakınlaştır** kutusunu da kullanabilirsiniz. Yakınlaştırma özelliği araç pencereleri içinde çalışmaz.|
|Sanal alan|varsayılan olarak, bir satırın sonundaki **sağ ok** tuşu imleci bir sonraki satırın başlangıcına taşıdıkça, Visual Studio düzenleyicilerde bulunan satırlar son karakterden sonra sona erdir. Bazı diğer düzenleyicilerde, bir satır son karakterden sonra bitmez ve imlecinizi satıra istediğiniz yere yerleştirebilirsiniz. **Araç**  >  **seçenekleri**  >  **metin düzenleyici**  >  **tüm diller** ayarlarında düzenleyicide sanal alanı etkinleştirebilirsiniz. **Sanal alanı** veya **sözcük kaydırmayı** etkinleştirebileceğinizi, ancak ikisini de kullanabileceğinizi unutmayın.|
|Yazdırma|Dosya yazdırırken satır numaralarını dahil etmek veya daraltılmış kod bölgelerini gizlemek için **Yazdır** iletişim kutusundaki seçenekleri kullanabilirsiniz. **Sayfa yapısı** iletişim kutusunda, **sayfa üstbilgisi**' ni seçerek dosyanın tam yolunu ve adını yazdırmayı da tercih edebilirsiniz.<br /><br /> **Araç**  >  **seçenekleri**  >  **ortam**  >  **yazı tipleri ve renkler** iletişim kutusunda renkli yazdırma seçeneklerini ayarlayabilirsiniz. Renkli yazdırmayı özelleştirmek için **ayarları göster** listesinden **Yazıcı** ' yı seçin. Bir dosyayı düzenleyen bir dosyayı yazdırmak için farklı renkler belirtebilirsiniz.|
|Küresel geri alma ve yineleme|**Düzenleme** menüsündeki **son genel eylemi geri al** ve **son genel eylemi yinele** komutları, birden çok dosyayı etkileyen genel eylemleri geri alır veya yineler. Genel eylemler bir sınıf veya ad alanını yeniden adlandırma, bir çözüm genelinde bul ve değiştir işlemi gerçekleştirme, bir veritabanını yeniden düzenleme ya da birden çok dosyayı değiştiren başka bir işlem yapma içerir. bir eylemin uygulandığı çözümü kapatsanız bile, geçerli Visual Studio oturumundaki eylemlere genel geri alma ve yineleme komutlarını uygulayabilirsiniz.|

## <a name="advanced-editing-features"></a>Gelişmiş Özellikleri Düzenle

  >  Araç çubuğundaki **Gelişmiş** Özellikleri Düzenle menüsünde birçok gelişmiş özellik bulabilirsiniz. Tüm kod dosyası türlerinde bu özelliklerin hepsi kullanılamaz.

|Özellik|Açıklama|
|-|-|
|Belgeyi Biçimlendir|Kod satırlarının uygun girintisini ayarlar ve küme ayraçlarını belgedeki satırlara ayırmak için taşımayın.|
|Biçim Seçimi|Kod satırlarının doğru girintilenmesini ayarlar ve küme ayraçlarını seçimdeki satırlara ayırmak için taşımayın.|
|Seçili satırları sekmeye Dönüştür|Baştaki boşlukları uygun yerlerde sekmeler olarak değiştirir.|
|Seçili satırları sekmeye Dönüştür|Baştaki sekmeleri boşluklara dönüştürür. Dosyanızdaki tüm boşlukları sekmelere (veya tüm sekmeleri boşluklara) dönüştürmek istiyorsanız, `Edit.ConvertSpacesToTabs` ve `Edit.ConvertTabsToSpaces` komutlarını kullanabilirsiniz. bu komutlar Visual Studio menülerde görünmez, ancak bunları **hızlı erişim** penceresinden veya komut penceresinden çağırabilirsiniz.|
|Büyük harf yap|Seçimdeki tüm karakterleri büyük harfe değiştirir veya seçim yoksa ekleme noktasındaki karakteri büyük harfe değiştirir. Kısayol: **CTRL** + **SHIFT** + **U**.|
|Küçük Harf Yapma|Seçimdeki tüm karakterleri küçük harf olarak değiştirir veya seçim yoksa ekleme noktasındaki karakteri küçük harf olarak değiştirir. Kısayol: **Ctrl** + **U**.|
|Seçili Satırları Yukarı Taşı|Seçilen satırı bir satır yukarı taşır. Kısayol: **Alt** + **Up Arrow**.|
|Seçili Satırları Aşağı Taşı|Seçili satırı bir satır aşağı taşır. Kısayol: **Alt** + **Aşağı Ok.**|
|Yatay Boşluk Silme|Geçerli satırın sonundaki sekmeleri veya boşlukları siler. Kısayol: **Ctrl** + **K**, **Ctrl**+**\\**|
|Boşluğu Görüntüle|Boşlukları yükseltilmiş nokta olarak, sekmeleri ise oklar olarak görüntüler. Bir dosyanın sonu dikdörtgen bir glyph olarak görüntülenir. Araç **Seçenekleri** Metin Düzenleyici Tüm Diller Sözcük Kaydırma Sözcük Kaydırma Göster sözcük kaydırma için görünür  >    >    >    >    >  **glyph'ler** seçilirse, söz dizim de görüntülenir.|
|Sözcük Kaydırma|Bir belgede yer alan tüm satırların kod penceresinde görünür olmasına neden olur. Metin Düzenleyici Tüm Diller ayarlarında ( Araçlar Seçenekler Metin Düzenleyici Tüm **Diller** **)** sözcük  >    >  **kaydırmayı**  >  **kapatabilirsiniz ve açabilirsiniz.**|
|Açıklama Seçimi|Seçime veya geçerli satıra açıklama karakterleri ekler. Kısayol: **Ctrl** + **K**, **Ctrl** + **C**|
|Uncomment Selection|Seçimden veya geçerli satırdan açıklama karakterlerini kaldırır. Kısayol: **Ctrl** + **K**, **Ctrl** + **U**|
|Satır Girintisini Artırma|Seçili satırlara veya geçerli satıra bir sekme (veya eşdeğer boşluklar) ekler.|
|Satır Girintisini Azalt|Seçili satırlardan veya geçerli satırdan bir sekmeyi (veya eşdeğer boşlukları) kaldırır.|
|Etiket'i seçin|Etiketleri içeren bir belgede (örneğin, XML veya HTML), etiketi seçer.|
|İçeriği Etiketle'yi seçin|Etiketleri içeren bir belgede (örneğin, XML veya HTML), içeriği seçer.|

## <a name="navigate-and-find-code"></a>Kodda gezinme ve kod bulma

Geri ve ileri doğru önceki ekleme noktalarına gezinme, bir tür veya üyenin tanımını görüntüleme ve gezinti çubuğunu kullanarak belirli bir yönteme atlama da dahil olmak üzere kod düzenleyicisinde birkaç farklı şekilde gezinebilirsiniz. Daha fazla bilgi için [bkz. Kodda gezinme.](navigating-code.md)

## <a name="find-references-in-your-code-base"></a>Kod tabanınıza başvuru bulma

Kod tabanınız genelinde belirli kod öğelerine nerede başvurul  olduğunu bulmak için Tüm Başvuruları Bul komutunu kullanabilir veya **Shift** + **F12 tuşuna basabilirsiniz.** Ayrıca, bir türe veya üyeye tıklarken, başvuru vurgulama **özelliği** otomatik olarak o türe veya üyeye yapılan tüm başvuruları vurgular. Daha fazla bilgi için [bkz. Kodundaki başvuruları bulma.](finding-references.md)

## <a name="customize-the-editor"></a>Düzenleyiciyi özelleştirme

Visual Studio ayarlarınızı başka bir geliştiriciyle paylaşabilir, ayarlarınızın standartla uyumlu hale getirebilirsiniz veya Araçlar menüsündeki Visual Studio İçeri ve Dışarı Aktarma Sihirbazı komutunu kullanarak **Ayarlar** varsayılan ayarlarına **dönebilirsiniz.** İçeri ve **Dışarı Aktarma Ayarlar Sihirbazı'nda,** seçilen genel ayarları veya dili ve projeye özgü ayarları değiştirebilirsiniz.

Yeni kısayol tuşları tanımlamak veya mevcut kısayol anahtarlarını yeniden tanımlamak için Araçlar Seçenekler Ortam  >  **Klavyesi'ne**  >    >  **gidin.** Kısayol tuşları hakkında daha fazla bilgi için bkz. [Varsayılan klavye kısayolları.](../ide/default-keyboard-shortcuts-in-visual-studio.md)

JavaScript'e özgü düzenleyici seçenekleri için bkz. [JavaScript düzenleyicisi seçenekleri.](../ide/reference/options-text-editor-javascript-formatting.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Kaynak düzenleyicisi (Mac için Visual Studio)](/visualstudio/mac/source-editor)
- [Visual Studio IDE](../get-started/visual-studio-ide.md)
- [Kullanmaya başlayın C++ ile Visual Studio](/cpp/get-started/tutorial-console-cpp)
- [Kullanmaya başlayın C# ve ASP.NET ile Visual Studio](../get-started/csharp/tutorial-aspnet-core.md)
- [Kullanmaya başlayın Python ile Visual Studio](../ide/quickstart-python.md)
