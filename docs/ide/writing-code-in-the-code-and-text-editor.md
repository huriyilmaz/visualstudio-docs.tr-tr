---
title: Kod düzenleyicisi özellikleri
ms.date: 02/23/2018
ms.topic: conceptual
helpviewer_keywords:
- code, editing [Visual Studio]
- code editor [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: de209e0a940fe7f7c64644cea37de3762df0d643
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75588557"
---
# <a name="features-of-the-code-editor"></a>Kod düzenleyicisinin özellikleri

Visual Studio editörü, kodunuzu ve metninizi yazmanızı ve yönetmeninizi kolaylaştıran birçok özellik sağlar. Anahat'ı kullanarak farklı kod bloklarını genişletebilir ve daraltabilirsiniz. IntelliSense, **Object Browser**ve Çağrı Hiyerarşisi'ni kullanarak kod hakkında daha fazla bilgi edinebilirsiniz. **Go To**, Go To To **To**, Ve Tüm **Başvuruları Bul**gibi özellikleri kullanarak kodu bulabilirsiniz. Kod parçacıklarıyla kod blokları ekleyebilir ve **Kullanımdan Oluştur**gibi özellikleri kullanarak kod oluşturabilirsiniz. Visual Studio düzenleyicisini daha önce hiç kullanmadıysanız, [bkz.](../get-started/tutorial-editor.md)

> [!NOTE]
> Bu konu Windows'daki Visual Studio için geçerlidir. Mac için Visual Studio için [Kaynak editöre (Mac için Visual Studio)](/visualstudio/mac/source-editor)bakın.

Kodunuzu çeşitli şekillerde görüntüleyebilirsiniz. Varsayılan olarak, **Solution Explorer** kodunuzu dosyalar tarafından düzenlenir. Sınıflara göre düzenlenen kodunuzu görüntülemek için pencerenin altındaki **Sınıf Görünümü** sekmesine tıklayabilirsiniz.

Tek veya birden çok dosyada metin arayabilir ve değiştirebilirsiniz. Daha fazla bilgi için [bkz.](../ide/finding-and-replacing-text.md) Metni bulmak ve değiştirmek için normal ifadeler kullanabilirsiniz. Daha fazla bilgi için [bkz.](../ide/using-regular-expressions-in-visual-studio.md)

Farklı Visual Studio dilleri farklı özellikler sunar ve bazı durumlarda özellikler farklı dillerde farklı şekilde davranmaktadır. Bu farklılıkların çoğu özelliklerin açıklamalarında belirtilir, ancak daha fazla bilgi için belirli Visual Studio dillerinin bölümlerini görebilirsiniz.

## <a name="editor-features"></a>Editör özellikleri

|||
|-|-|
|Sözdizimi Boyama|Kod ve biçimlendirme dosyalarının bazı sözdizimi öğeleri ayırt etmek için farklı renktedir. Örneğin, anahtar kelimeler `using` (C# `Imports` ve Visual Basic gibi) bir renktir, ancak türleri (gibi `Console` ve) `Uri`başka bir renktir. Dize literals ve açıklamalar gibi diğer sözdizimi öğeleri de renklendirilmiştir. C++, diğer belirteçler arasında türleri, sayısallaştırmalar ve makrolar arasında ayrım yapmak için renk kullanır.<br /><br /> Her tür için varsayılan rengi görebilir ve **Araçlar** menüsünden açabileceğiniz Yazı [Tipleri ve Renkler, Çevre, Seçenekler iletişim kutusunda](../ide/reference/fonts-and-colors-environment-options-dialog-box.md)belirli bir sözdizimi öğesinin rengini değiştirebilirsiniz.|
|Hata ve Uyarı İşaretleri|Kod ekleyip çözümünüzü oluştururken, (a) farklı renkli dalgalı alt çizgilerini (dalgalı olarak bilinir) veya (b) kodunuzda görünen ampuller görebilirsiniz. Kırmızı dalgalandırma sözdizimi hatalarını, mavi derleyici hatalarını gösterir, yeşil uyarıları gösterir ve mor diğer hata türlerini gösterir. [Hızlı Eylemler,](../ide/quick-actions.md) sorunlar için düzeltmeler önerir ve düzeltmeyi uygulamayı kolaylaştırır.<br /><br /> **Araçlar** > **Seçenekleri** > **Ortamı** > **Yazı Tipleri ve Renkler** iletişim kutusunda her hata ve uyarı dalgalı için varsayılan renk görebilirsiniz. **Sözdizimi Hatası,** **Derleyici Hatası,** **Uyarı**ve **Diğer Hata**arayın.|
|Ayraç Eşleştirme|Ekleme noktası bir kod dosyasındaki açık bir ayraç üzerine yerleştirildiğinde, hem bu işaret hem de kapanış ayracı vurgulanır. Bu özellik, yanlış yerleştirilmiş veya eksik ayraçlar hakkında anında geri bildirim sağlar. **Otomatik Delimiter Vurgulama** ayarı **(Tools** > **Options** > **Text Editor)** ile ayraç eşleştirmesini açıp kapatabilirsiniz. **Yazı Tipleri ve Renkler** ayarında vurgu rengini değiştirebilirsiniz (**Araçlar** > **Seçenekleri** > **Ortamı).** Ayr **Ayr uyumlu (Vurgu)** veya **Ayrayr Eşleştirme (Dikdörtgen)** arayın.|
|Yapı Görselleştiricisi|Noktalı çizgiler kod dosyalarındaki eşleşen ayraçları birbirine bağlayarak ayraç çiftlerini açma ve kapatmayı kolaylaştırır. Bu, kod tabanınızdaki kodu daha hızlı bulmanıza yardımcı olabilir.  >  **Araçlar** > **Seçenekleri****Metin Editörü** > **Genel** sayfasının **Görüntü** bölümündeki **Yapıyı Göster yönergeleriyle** bu satırları açabilir veya kapatabilirsiniz.|
|Çizgi Numaraları|Satır numaraları kod penceresinin sol kenar boşluğunda görüntülenebilir. Bunlar varsayılan olarak görüntülenmez. Bu seçeneği **Metin Düzenleyicisi Tüm Diller** ayarlarında açabilirsiniz (**Araçlar** > **Seçenekleri** > **Metin Düzenleyicisi** > **Tüm Diller**). Bu dillerin ayarlarını değiştirerek tek tek programlama dilleri için satır numaralarını görüntüleyebilirsiniz **(Araçlar** > **Seçenekleri** > **Metin Düzenleyicidili** > **\<>). ** Satır numaralarının yazdırılması için **Yazdır** iletişim kutusuna **satır numaralarını ekleme'yi** seçmeniz gerekir.|
|Değişiklik İzleme|Sol kenar boşluğunun rengi, bir dosyada yaptığınız değişiklikleri izlemenizi sağlar. Dosya açıldığından beri yaptığınız ancak kaydedilmemiş değişiklikler sol kenar boşluğundaki sarı çubukla (seçim kenar boşluğu olarak bilinir) gösterilir. Değişiklikleri kaydettikten sonra (ancak dosyayı kapatmadan önce), çubuk yeşile döner. Dosyayı kaydettikten sonra bir değişikliği geri alırsanız, çubuk turuncuya döner. Bu özelliği kapatıp açmak için **Metin Düzenleyicisi** ayarlarındaki **Değişiklikleri İzleme** seçeneğini değiştirin (**Araçlar** > **Seçenekleri** > **Metin Düzenleyicisi**).|
|Kod ve Metin Seçme|Metni standart sürekli akış modunda veya satır kümesi yerine metnin dikdörtgen bir bölümünü seçtiğiniz kutu modunda seçebilirsiniz. Kutu modunda seçim yapmak için fareyi seçimin üzerine sürüklerken **Alt** tuşuna basın (veya **Alt**+**Shift**+**\<ok tuşuna>) **tuşuna basın. Seçim, ilk karakter ve seçimdeki son karakter tarafından tanımlanan dikdörtgen içindeki tüm karakterleri içerir. Seçili alana yazılan veya yapıştırılan her şey, her satıra aynı noktaya eklenir.|
|Zoom|**Ctrl** tuşuna basıp basılı tutarak ve kaydırma tekerleğini farenin üzerinde hareket ettirerek (veya **Ctrl**+**Shift.**+**.** artırmak ve **Ctrl**+**Shift**+**,** azaltmak için). Belirli bir yakınlaştırma yüzdesi ayarlamak için kod penceresinin sol alt köşesindeki **Yakınlaştırma** kutusunu da kullanabilirsiniz. Yakınlaştırma özelliği araç pencerelerinde çalışmaz.|
|Sanal Alan|Varsayılan olarak, Visual Studio düzenleyicisindeki satırlar son karakterden sonra sona erer, böylece bir satırın sonundaki **Sağ Ok** tuşu imleci bir sonraki satırın başına taşır. Diğer bazı editörlerde bir satır son karakterden sonra bitmez ve imlecinizi satırın herhangi bir yerine yerleştirebilirsiniz. **Araçlar** > **Seçenekleri** > Metin**Düzenleyicisi** **Text Editor** > Tüm Diller ayarlarında düzenleyicide sanal alanı etkinleştirebilirsiniz. **Sanal Alan** veya **Word Wrap'ı**etkinleştirebileceğinizi, ancak her ikisini birden etkinleştirmeyeceğinizi unutmayın.|
|Yazdırma|Dosya yazdırırken satır numaralarını eklemek veya yazdırılan kod bölgelerini gizlemek için **Yazdır** iletişim kutusundaki seçenekleri kullanabilirsiniz. Sayfa **Kurulumu** iletişim kutusunda, **Sayfa üstbilgisini**seçerek dosyanın tam yolunu ve adını yazdırmayı da seçebilirsiniz.<br /><br /> **Araçlar** > **Seçenekleri** > **Ortamı** > **Yazı Tipleri ve Renkler** iletişim kutusunda renk yazdırma seçeneklerini ayarlayabilirsiniz. Renkli yazdırmayı özelleştirmek için liste **yi göster ayarlarında** **Yazıcı'yı** seçin. Bir dosyayı yazdırmak için dosyayı düzenlemeden farklı renkler belirtebilirsiniz.|
|Küresel Geri Ala ve Redo|**Son Genel Eylemi Geri Al** ve Son Genel Eylemi Yeniden **Yap** komutları, birden çok dosyayı etkileyen genel eylemleri **geri** al veya yeniden yap menüsünde. Genel eylemler, bir sınıfı veya ad alanını yeniden adlandırmayı, çözüm de bul-değiştir işlemini gerçekleştirmeyi, veritabanını yeniden düzenlemeyi veya birden çok dosyayı değiştiren başka bir eylemi içerir. Bir eylemin uygulandığı çözümü kapattıktan sonra bile, genel geri ave ve yeniden yapma komutlarını geçerli Visual Studio oturumundaki eylemlere uygulayabilirsiniz.|

## <a name="advanced-editing-features"></a>Gelişmiş düzenleme özellikleri

Araç çubuğunda Gelişmiş **Gelişmiş'i** > **Edit** menüsünde bir dizi gelişmiş özellik bulabilirsiniz. Bu özelliklerin tümü tüm kod dosyaları için kullanılamaz.

|||
|-|-|
|Belgeyi Biçimlendir|Kod satırlarının uygun girintisini ayarlar ve kıvırcık ayraçları belgedeki satırları ayırmak için taşır.|
|Biçim Seçimi|Kod satırlarının uygun girintisini ayarlar ve kıvırcık ayraçları seçimdeki satırları ayırmak için hareket ettirir.|
|Tabify Seçilen Satırlar|Satır aralığını uygun yerlerde sekmelere değiştirir.|
|Untabify Seçili Satırlar|Satır aralığıseklerini boşluklara değiştirir. Dosyanızdaki tüm boşlukları sekmelere (veya tüm sekmeleri boşluklara) dönüştürmek istiyorsanız, `Edit.ConvertSpacesToTabs` `Edit.ConvertTabsToSpaces` bu boşlukları ve komutları kullanabilirsiniz. Bu komutlar Visual Studio menülerinde görünmez, ancak bunları **Hızlı Erişim** penceresinden veya komut penceresinden arayabilirsiniz.|
|Büyük Harf Yap|Seçimdeki tüm karakterleri büyük harfe değiştirir veya seçim yoksa ekleme noktasındaki karakteri büyük harfe göre değiştirir. Kısayol: **Ctrl**+**Shift**+**U**.|
|Küçük Harf yap|Seçimdeki tüm karakterleri küçük harfle değiştirir veya seçim yoksa ekleme noktasındaki karakteri küçük harfle değiştirir. Kısayol: **Ctrl**+**U**.|
|Seçili Satırları Yukarı Taşıma|Seçili satırı bir satıryukarı taşır. Kısayol: **Alt**+**Yukarı Ok**.|
|Seçili Satırları Aşağı Taşıma|Seçili satırı bir satıraşağı taşır. Kısayol: **Alt**+**Aşağı Ok**.|
|Yatay Beyaz Alanı Silme|Geçerli satırın sonundaki sekmeleri veya boşlukları siler. Kısayol: **Ctrl**+**K**, **Ctrl**+**\\**|
|Beyaz Alanı Görüntüle|Boşlukları yükseltilmiş nokta olarak görüntüler ve sekmeleri ok olarak görüntüler. Dosyanın sonu dikdörtgen bir glifler olarak görüntülenir. **Araçlar** > **Seçenekleri** > Metin**Düzenleyicitüm** > **Dilleri** > **Word Wrap** > Word**wrap için görünür glifleri gösterir** seçilirse, bu gph da görüntülenir.|
|Sözcük Kaydırma|Belgedeki tüm satırların kod penceresinde görünür olmasını neden olur. **Metin Düzenleyicisi Tüm Diller** ayarlarında **(Araçlar** > **Seçenekleri** > **Metin Düzenleyicisi** > **Tüm Diller)** sözcük kaydırmave açma'yı kapatabilirsiniz.|
|Yorum Seçimi|Seçime veya geçerli satıra açıklama karakterleri ekler. Kısayol: **Ctrl**+**K**, **Ctrl**+**C**|
|Yorumsuz Seçim|Açıklama karakterlerini seçimden veya geçerli satırdan kaldırır. Kısayol: **Ctrl**+**K**, **Ctrl**+**U**|
|Hat Girintiyi Artır|Seçili satırlara veya geçerli satıra bir sekme (veya eşdeğer boşluklar) ekler.|
|Satır Girintiyi Azaltma|Seçili satırlardan veya geçerli satırlardan bir sekmeyi (veya eşdeğer boşlukları) kaldırır.|
|Etiket'i seçin|Etiketler (örneğin, XML veya HTML) içeren bir belgede etiketi seçer.|
|Etiket İçeriği ni seçin|Etiketler (örneğin, XML veya HTML) içeren bir belgede, içeriği seçer.|

## <a name="navigate-and-find-code"></a>Gezinme ve kodu bulma

Kod düzenleyicisinde, önceki ekleme noktalarına ileri ve geri gezinme, bir tür veya üyenin tanımını görüntüleme ve gezinti çubuğunu kullanarak belirli bir yönteme atlama gibi çeşitli şekillerde hareket edebilirsiniz. Daha fazla bilgi için [bkz.](navigating-code.md)

## <a name="find-references-in-your-code-base"></a>Kod tabanınızda referansları bulma

Kod tabanınız boyunca belirli kod öğelerinin başvurulduğu yeri bulmak için **Tüm Referansları Bul** komutunu kullanabilir veya **F12'ye**+**F12**basabilirsiniz. Ayrıca, bir türü veya üyeyi tıklattığınızda, **başvuru vurgulama** özelliği otomatik olarak bu türe veya üyeye yapılan tüm başvuruları vurgular. Daha fazla bilgi için [bkz.](finding-references.md)

## <a name="customize-the-editor"></a>Düzenleyiciyi özelleştirme

**Araçlar** menüsündeki **İçe Ve Dışa** Aktar Ayarları Sihirbazı komutunu kullanarak Visual Studio ayarlarınızı başka bir geliştiriciyle paylaşabilir, ayarlarınızın bir standarda uygun olmasını sağlayabilir veya Visual Studio varsayılan ayarlarına dönebilirsiniz. **Ayarve Dışa Aktar**Sihirbazı'nda, seçili genel ayarları veya dil ve projeye özel ayarları değiştirebilirsiniz.

Yeni kısayol tuşları tanımlamak veya varolan kısayol tuşlarını yeniden tanımlamak için **Araçlar** > **Seçenekleri** > **Ortamı** > **Klavyesi'ne**gidin. Kısayol tuşları hakkında daha fazla bilgi için [Varsayılan klavye kısayolları'na](../ide/default-keyboard-shortcuts-in-visual-studio.md)bakın.

JavaScript'e özgü düzenleyici seçenekleri için [JavaScript düzenleyici seçeneklerine](../ide/reference/options-text-editor-javascript-formatting.md)bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Kaynak editör (Visual Studio For Mac)](/visualstudio/mac/source-editor)
- [Görsel Stüdyo IDE](../get-started/visual-studio-ide.md)
- [Visual Studio'da C++ ile başlayın](/cpp/get-started/tutorial-console-cpp)
- [Visual Studio'da C# ve ASP.NET ile başlayın](../get-started/csharp/tutorial-aspnet-core.md)
- [Visual Studio'da Python ile başlayın](../ide/quickstart-python.md)
