---
title: Kod Düzenleyicisi özellikleri
ms.date: 02/23/2018
ms.topic: conceptual
helpviewer_keywords:
- code, editing [Visual Studio]
- code editor [Visual Studio]
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 86cab4db7c732aeb33d9adf61bfdcb2c4563da57
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72647040"
---
# <a name="features-of-the-code-editor"></a>Kod düzenleyicisinin özellikleri

Visual Studio Düzenleyicisi, kodunuzu ve metninizi yazmanızı ve yönetmenizi kolaylaştıran birçok özellik sağlar. Anahat kullanarak farklı kod bloklarını genişletebilir ve daraltabilirsiniz. IntelliSense, **nesne tarayıcısı**ve çağrı hiyerarşisini kullanarak kod hakkında daha fazla bilgi edinebilirsiniz. **Git**gibi özellikleri kullanarak kodu bulabilir, **tanıma gidebilirsiniz**ve **tüm başvuruları bulabilirsiniz**. Kod parçacıkları içeren kod blokları ekleyebilirsiniz ve **kullanımdan oluştur**gibi özellikleri kullanarak kod oluşturabilirsiniz. Daha önce Visual Studio düzenleyicisini kullanmadıysanız bkz. [kod düzenleyicisini kullanmayı öğrenin](../get-started/tutorial-editor.md).

> [!NOTE]
> Bu konu, Windows üzerinde Visual Studio için geçerlidir. Mac için Visual Studio için bkz. [kaynak Düzenleyicisi (Mac için Visual Studio)](/visualstudio/mac/source-editor).

Kodunuzu çeşitli yollarla görüntüleyebilirsiniz. Varsayılan olarak **Çözüm Gezgini** , kodunuzu dosyalara göre düzenlenmiş olarak gösterir. Kodunuzu sınıflara göre düzenlenmiş olarak görüntülemek için pencerenin alt kısmındaki **sınıf görünümü** sekmesine tıklayabilirsiniz.

Tek veya birden çok dosyada metin arayabilir ve değiştirebilirsiniz. Daha fazla bilgi için bkz. [metni bulma ve değiştirme](../ide/finding-and-replacing-text.md). Metni bulmak ve değiştirmek için normal ifadeleri kullanabilirsiniz. Daha fazla bilgi için bkz. [Visual Studio 'da normal Ifadeler kullanma](../ide/using-regular-expressions-in-visual-studio.md).

Farklı Visual Studio dilleri farklı özellik kümeleri sunar ve bazı durumlarda özellikler farklı dillerde farklı davranır. Bu farklılıkların birçoğu özelliklerin açıklamalarında belirtilmiştir, ancak daha fazla bilgi için belirli Visual Studio dillerinde bölümleri görebilirsiniz.

## <a name="editor-features"></a>Düzenleyici özellikleri

|||
|-|-|
|Sözdizimi renklendirme|Kod ve biçimlendirme dosyalarının bazı sözdizimi öğeleri, bunları ayırt etmek için farklı renklendirilir. Örneğin, anahtar sözcükler (Visual Basic `using` C# ve `Imports`) bir renktedir, ancak türler (`Console` ve `Uri` gibi) başka bir renktir. Diğer sözdizimi öğeleri de, dize sabit değerleri ve açıklamalar gibi renklendirilmiştir. C++diğer belirteçlerde türler, numaralandırmalar ve makrolar arasında ayrım yapmak için renk kullanır.<br /><br /> Her tür için varsayılan rengi görebilir ve **Araçlar** menüsünden açabileceğiniz [yazı tipleri ve renkler, ortam, Seçenekler iletişim kutusunda](../ide/reference/fonts-and-colors-environment-options-dialog-box.md)herhangi bir belirli bir söz dizimi öğesi için rengi değiştirebilirsiniz.|
|Hata ve uyarı Işaretleri|Kod eklerken ve çözümünüzü oluştururken, kodunuzda görüntülenen (a) farklı renkli dalgalı alt çizgiler (dalgalı çizgiler olarak bilinir) veya (b) açık bulbs görebilirsiniz. Red dalgalı çizgiler, sözdizimi hatalarını ifade eder, mavi derleyici hatalarını, yeşil bir uyarı gösterir ve mor diğer hata türlerini gösterir. [Hızlı eylemler](../ide/quick-actions.md) sorunlara yönelik düzeltmeler önerir ve düzeltmenin uygulanmasını kolaylaştırır.<br /><br /> **Araçlar** > **Seçenekler** > **ortam** > **yazı tipi ve renkler** iletişim kutusunda her bir hata ve uyarı dalgalı çizgi için varsayılan rengi görebilirsiniz. **Sözdizimi hatası**, **derleyici hatası**, **Uyarı**ve **diğer hata**olup olmadığına bakın.|
|Ayraç eşleştirme|Ekleme noktası, bir kod dosyasındaki açık bir küme ayracı üzerine yerleştirildiğinde, hem hem de kapanış küme ayracı vurgulanır. Bu özellik, yanlış yerleştirilmiş veya eksik küme ayraçları hakkında anında geri bildirim sağlar. **Otomatik sınırlayıcı vurgulama** ayarı (**Araçlar** > **seçenekleri** > **metin Düzenleyicisi**) ile, çift ayraç eşleştirmeyi etkinleştirebilir veya devre dışı bırakabilirsiniz. **Yazı tipi ve renkler** ayarında vurgu rengini değiştirebilirsiniz (**Araçlar** > **Seçenekler** > **ortamı**). **Küme ayracı Ile eşleşen (vurgu)** veya **ayraç eşleştirme (dikdörtgen)** arayın.|
|Yapı görselleştiricisi|Noktalı çizgiler, kod dosyalarında eşleşen küme ayraçlarını, açma ve kapatma küme ayracı çiftlerini daha kolay görmenizi sağlar. Bu, kod tabanınızdaki kodu daha hızlı bir şekilde bulmanıza yardımcı olabilir. Bu satırları, **araçlar** > **seçenekleri** > **metin Düzenleyicisi** > **genel** sayfasındaki **görüntü** bölümünde bulunan **yapısı göster yönergeleriyle** birlikte etkinleştirebilir veya devre dışı bırakabilirsiniz.|
|Satır numaraları|Satır numaraları, kod penceresinin sol kenar boşluğunda görüntülenebilir. Varsayılan olarak gösterilmezler. Bu seçeneği, **metin düzenleyici tüm diller** ayarlarında (**Araçlar** > **seçenekleri** > **metin Düzenleyicisi** > **tüm diller**) açabilirsiniz. Bu dillerin ayarlarını değiştirerek bağımsız programlama dillerinin satır numaralarını görüntüleyebilirsiniz (**araçlar** > **seçenekleri** > **metin Düzenleyicisi** >  **\<dil >** ). Yazdırılacak satır numaraları için **Yazdır** iletişim kutusunda **satır numaralarını dahil et** ' i seçmeniz gerekir.|
|Değişiklik İzleme|Sol kenar boşluğunun rengi, bir dosyada yaptığınız değişiklikleri izlemenize olanak sağlar. Dosya açıldığı ancak kaydedilmediği için yaptığınız değişiklikler sol kenar boşluğunda (seçim kenar boşluğu olarak bilinir) sarı bir çubukla gösterilir. Değişiklikleri kaydettikten sonra (ancak dosyayı kapatmadan önce), çubuk yeşile döner. Dosyayı kaydettikten sonra bir değişikliği geri alırsanız, çubuk turuncu 'ı kapatır. Bu özelliği devre dışı bırakmak ve açmak için **metin Düzenleyicisi** ayarlarındaki **Değişiklikleri İzle** seçeneğini değiştirin (**araçlar** > **Seçenekler** > **metin Düzenleyicisi**).|
|Kod ve metin seçme|Standart sürekli akış modunda veya kutu modunda metin seçebilirsiniz, burada satır kümesi yerine metnin dikdörtgen bir bölümünü seçersiniz. Kutu modunda seçim yapmak için, fareyi seçimin üzerine sürüklerken **alt** tuşuna basın (veya **alt**+**SHIFT**+ **\<OK tuşuna basın >** ). Seçim, seçimdeki ilk karakter ve son karakter tarafından tanımlanan dikdörtgenin içindeki tüm karakterleri içerir. Seçilen alana yazılan veya yapıştırılan her şey, her satırda aynı noktaya eklenir.|
|Yakınlaştır|**CTRL** tuşunu basılı tutarak ve kaydırma tekerleğini fareyle taşıyarak (ya da **CTRL**+**SHIFT**+ ' i seçerek herhangi bir kod penceresinde yakınlaştırıp uzaklaştırabilirsiniz **.** artırmak ve **Ctrl** +**SHIFT** **+ azaltmak için.** Ayrıca, belirli bir yakınlaştırma yüzdesi ayarlamak için kod penceresinin sol alt köşesindeki **Yakınlaştır** kutusunu da kullanabilirsiniz. Yakınlaştırma özelliği araç pencereleri içinde çalışmaz.|
|Sanal alan|Varsayılan olarak, Visual Studio düzenleyicilerinde bulunan satırlar son karakterden sonra sona erdir, böylece satırın sonundaki **sağ ok** tuşu imleci bir sonraki satırın başlangıcına taşıdıkça. Bazı diğer düzenleyicilerde, bir satır son karakterden sonra bitmez ve imlecinizi satıra istediğiniz yere yerleştirebilirsiniz. **Araçlar** > **seçenekleri** > **metin Düzenleyicisi** > **tüm diller** ayarları ' nda düzenleyicide sanal alanı etkinleştirebilirsiniz. **Sanal alanı** veya **sözcük kaydırmayı**etkinleştirebileceğinizi, ancak ikisini de kullanabileceğinizi unutmayın.|
|Yazdırma|Dosya yazdırırken satır numaralarını dahil etmek veya daraltılmış kod bölgelerini gizlemek için **Yazdır** iletişim kutusundaki seçenekleri kullanabilirsiniz. **Sayfa yapısı** iletişim kutusunda, **sayfa üstbilgisi**' ni seçerek dosyanın tam yolunu ve adını yazdırmayı da tercih edebilirsiniz.<br /><br /> **Araçlar** > **seçenekleri** > **ortam** > **yazı tipi ve renkler** iletişim kutusunda renkli yazdırma seçeneklerini ayarlayabilirsiniz. Renkli yazdırmayı özelleştirmek için **ayarları göster** listesinden **Yazıcı** ' yı seçin. Bir dosyayı düzenleyen bir dosyayı yazdırmak için farklı renkler belirtebilirsiniz.|
|Küresel geri alma ve yineleme|**Düzenleme** menüsündeki **son genel eylemi geri al** ve **son genel eylemi yinele** komutları, birden çok dosyayı etkileyen genel eylemleri geri alır veya yineler. Genel eylemler bir sınıf veya ad alanını yeniden adlandırma, bir çözüm genelinde bul ve değiştir işlemi gerçekleştirme, bir veritabanını yeniden düzenleme ya da birden çok dosyayı değiştiren başka bir işlem yapma içerir. Bir eylemin uygulandığı çözümü kapattıktan sonra bile, geçerli Visual Studio oturumunda eylemlere genel geri alma ve yineleme komutlarını uygulayabilirsiniz.|

## <a name="advanced-editing-features"></a>Gelişmiş Özellikleri Düzenle

Araç **çubuğundaki  > ** **Gelişmiş** Özellikler menüsünden Gelişmiş özellikler bulabilirsiniz. Tüm kod dosyası türlerinde bu özelliklerin hepsi kullanılamaz.

|||
|-|-|
|Belgeyi Biçimlendir|Kod satırlarının uygun girintisini ayarlar ve küme ayraçlarını belgedeki satırlara ayırmak için taşımayın.|
|Biçim Seçimi|Kod satırlarının doğru girintilenmesini ayarlar ve küme ayraçlarını seçimdeki satırlara ayırmak için taşımayın.|
|Seçili satırları sekmeye Dönüştür|Baştaki boşlukları uygun yerlerde sekmeler olarak değiştirir.|
|Seçili satırları sekmeye Dönüştür|Baştaki sekmeleri boşluklara dönüştürür. Dosyanızdaki tüm boşlukları sekmelere (veya tüm sekmeleri boşluklara) dönüştürmek istiyorsanız, `Edit.ConvertSpacesToTabs` ve `Edit.ConvertTabsToSpaces` komutlarını kullanabilirsiniz. Bu komutlar Visual Studio menülerinde görünmez, ancak bunları **hızlı erişim** penceresinden veya komut penceresinden çağırabilirsiniz.|
|Büyük harf yap|Seçimdeki tüm karakterleri büyük harfe değiştirir veya seçim yoksa ekleme noktasındaki karakteri büyük harfe değiştirir. Kısayol: **Ctrl**+**SHIFT**+**U**.|
|Küçük harf yap|Seçimdeki tüm karakterleri küçük harfe çevirir veya seçim yoksa ekleme noktasındaki karakteri küçük harfe dönüştürür. Kısayol: **Ctrl**+**U**.|
|Seçili satırları yukarı taşı|Seçili satırı bir satır yukarı kaydırır. Kısayol: **Alt**+**yukarı ok**.|
|Seçili satırları aşağı taşı|Seçili satırı bir satır aşağı kaydırır. Kısayol: **Alt**+**aşağı ok**.|
|Yatay boşluğu Sil|Geçerli satırın sonundaki sekmeleri veya boşlukları siler. Kısayol: **ctrl**+**K**, **CTRL**+ **\\**|
|Boşluğu görüntüle|Boşlukları, kabarık noktalar olarak ve ok olarak sekme olarak görüntüler. Bir dosyanın sonu dikdörtgen bir karakter olarak görüntülenir. **Araçlar** > **Seçenekler** > **metin Düzenleyicisi** > **tüm diller** > **sözcük kaydırmayı** >  sözcük kaydırması**için görünür glifleri göster** seçilidir, bu glif de görüntülenir.|
|Sözcük Kaydırma|Belgedeki tüm satırların kod penceresinde görünür olmasını sağlar. Word kaydırmayı, **metin düzenleyici tüm diller** ayarlarında (**Araçlar** > **seçenekleri** > **metin Düzenleyicisi** > **tüm diller**) açabilir.|
|Açıklama seçimi|Seçime veya geçerli satıra Açıklama karakterleri ekler. Kısayol: **ctrl**+**K**, **CTRL**+**C**|
|Seçimi açıklama kaldır|Seçim veya geçerli satırdan açıklama karakterlerini kaldırır. Kısayol: **ctrl**+**K**, **CTRL**+**U**|
|Satır girintisini artır|Seçili satırlara veya geçerli satıra bir sekme (veya eşdeğer boşluk) ekler.|
|Satır girintisini azalt|Seçili satırlardan veya geçerli satırdan bir sekmeyi (veya eşdeğer alanları) kaldırır.|
|Etiket Seç|Etiketler (örneğin, XML veya HTML) içeren bir belgede etiketi seçer.|
|Etiket Içeriğini seçin|Etiketler (örneğin, XML veya HTML) içeren bir belgede, içeriği seçer.|

## <a name="navigate-and-find-code"></a>Gezinme ve kod bulma

Geriye doğru gitme ve önceki ekleme noktalarına iletme, bir tür veya üyenin tanımını görüntüleme ve gezinti çubuğunu kullanarak belirli bir yönteme atlama dahil olmak üzere birkaç farklı yolla kod düzenleyicide gezinebilirsiniz. Daha fazla bilgi için bkz. [gezinme kodu](navigating-code.md).

## <a name="find-references-in-your-code-base"></a>Kod tabanınız için başvuruları bulma

Belirli kod öğelerine kod tabanınızın tamamında başvurulduğunu bulmak için, **tüm başvuruları bul** komutunu kullanabilir veya **SHIFT**+**F12**tuşlarına basabilirsiniz. Ayrıca, bir tür veya üyeye tıkladığınızda, **başvuru vurgulama** özelliği bu tür veya üyeye yapılan tüm başvuruları otomatik olarak vurgular. Daha fazla bilgi için bkz. [kodunuzda başvuruları bulma](finding-references.md).

## <a name="customize-the-editor"></a>Düzenleyiciyi özelleştirme

Visual Studio ayarlarınızı başka bir geliştiriciyle paylaşabilir, ayarlarınızı bir standart ile uyumlu yapabilir veya **Araçlar** menüsünde **ayarları Içeri ve dışarı aktarma Sihirbazı** komutunu kullanarak Visual Studio varsayılan ayarlarına dönebilirsiniz. **Ayarları içeri ve dışarı aktarma sihirbazında**, seçili genel ayarları veya dili ve projeye özgü ayarları değiştirebilirsiniz.

Yeni kısayol tuşlarını tanımlamak veya mevcut kısayol tuşlarını yeniden tanımlamak için **araçlar**  > **seçenekler**  > **ortam**  > **klavye**' ye gidin. Kısayol tuşları hakkında daha fazla bilgi için bkz. [varsayılan klavye kısayolları](../ide/default-keyboard-shortcuts-in-visual-studio.md).

JavaScript 'e özgü düzenleyici seçenekleri için bkz. [JavaScript Düzenleyicisi seçenekleri](../ide/reference/options-text-editor-javascript-formatting.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Kaynak Düzenleyicisi (Mac için Visual Studio)](/visualstudio/mac/source-editor)
- [Visual Studio IDE](../get-started/visual-studio-ide.md)
- [Visual Studio C++ 'da kullanmaya başlayın](/cpp/get-started/tutorial-console-cpp)
- [Visual Studio 'da C# ve ASP.NET kullanmaya başlayın](../get-started/csharp/tutorial-aspnet-core.md)
- [Visual Studio 'da Python ile çalışmaya başlama](../ide/quickstart-python.md)
