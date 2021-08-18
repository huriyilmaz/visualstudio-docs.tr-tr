---
title: Kod düzenleyicisi özellikleri
description: Kod ve metin yazmanızı ve yönetmenizi kolaylaştırmak Visual Studio kod düzenleyicisinin sağladığı özellikler hakkında bilgi öğrenin.
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
ms.openlocfilehash: 2e947606f13b986503e5af5cfc54c9e4ee758b79
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122040586"
---
# <a name="features-of-the-code-editor"></a>Kod düzenleyicisinin özellikleri

Bu Visual Studio düzenleyici, kodunuzu ve metninizi yazmanızı ve yönetmenizi kolaylaştıran birçok özellik sağlar. Altı çizili kullanarak farklı kod bloklarını genişletebilirsiniz ve daraltabilirsiniz. IntelliSense, **Object Browser** ve Çağrı Hiyerarşisi kullanarak kod hakkında daha fazla bilgi edinebilirsiniz. Git, Tanıma Git ve Tüm **Başvuruları** Bul **gibi** özellikleri kullanarak kod **bulabilirsiniz.** Kod parçacıklarıyla kod blokları ekleyebilirsiniz ve Kullanımdan Oluştur gibi özellikleri kullanarak **kod üretebilirsiniz.** Daha önce herhangi bir Visual Studio önce kullanmadıysanız [bkz. Kod düzenleyicisini kullanmayı öğrenin.](../get-started/tutorial-editor.md)

> [!NOTE]
> Bu konu, Visual Studio için Windows. Daha Mac için Visual Studio için [bkz. Kaynak düzenleyicisi (Mac için Visual Studio)](/visualstudio/mac/source-editor).

Kodunuzu birkaç farklı şekilde görüntüleyebilirsiniz. Varsayılan **olarak, Çözüm Gezgini** göre düzenlenmiş kodunuzu gösterir. Kodunuzu sınıflara göre **Sınıf Görünümü** görüntülemek için pencerenin en altındaki Sınıf Görünümü sekmesine tıkleyebilirsiniz.

Tek veya birden çok dosyada metin arayabilir ve değiştirebilirsiniz. Daha fazla bilgi için [bkz. Metin bulma ve değiştirme.](../ide/finding-and-replacing-text.md) Metin bulmak ve değiştirmek için normal ifadeleri kullanabilirsiniz. Daha fazla bilgi için [bkz. Normal ifadeleri Visual Studio.](../ide/using-regular-expressions-in-visual-studio.md)

Farklı Visual Studio farklı özellik kümeleri sunar ve bazı durumlarda özellikler farklı dillerde farklı davranır. Bu farklılıkların çoğu özelliklerin açıklamalarında belirtilmiştir, ancak daha fazla bilgi için belirli Visual Studio bölümlerine bakebilirsiniz.

## <a name="editor-features"></a>Düzenleyici özellikleri

|Özellik|Açıklama|
|-|-|
|Söz Dizimi Renklendirmesi|Kod ve işaretleme dosyalarının bazı söz dizimi öğeleri, ayırt etmek için farklı renklendirilmiştir. Örneğin, anahtar sözcükler (C# ve Visual Basic gibi) bir renktir, ancak `using` `Imports` türler (ve `Console` `Uri` gibi) başka bir renktir. Dize değişmez öğeleri ve açıklamalar gibi diğer söz dizimi öğeleri de renklendirmeye sahiptir. C++ türleri, numaralarını ve makroları diğer belirteçler arasında ayırt etmek için renk kullanır.<br /><br /> Her tür için varsayılan rengi görebilir ve Araçlar menüsünden açabilirsiniz Yazı Tipleri ve [Renkler, Ortam,](../ide/reference/fonts-and-colors-environment-options-dialog-box.md)Seçenekler iletişim kutusunda herhangi bir söz dizimi öğesinin rengini **değiştirebilirsiniz.**|
|Hata ve Uyarı İşaretleri|Kod eklerken ve çözümlerinizi eklerken, (a) farklı renkli dalgalı alt çizgileri (dalgalı çizgiler olarak bilinir) veya (b) ampullerin kodunda görüntü olduğunu görebilir. Kırmızı geçişler söz dizimi hatalarını, mavi derleyici hatalarını, yeşil uyarıları ve mor da diğer hata türlerini gösterir. [Hızlı Eylemler,](../ide/quick-actions.md) sorunlar için düzeltmeler önerir ve düzeltmeyi uygulamayı kolaylaştırır.<br /><br /> Araçlar Seçenekler Ortam Yazı Tipleri ve Renkler iletişim kutusunda her hata ve uyarı iki durumlu  >    >  **düğmesinin**  >  **varsayılan rengini** görüntüebilirsiniz. Söz **Dizimi Hatası,** **Derleyici Hatası,** Uyarı **ve** Diğer **Hata'ya bakın.**|
|Küme Ayracı Eşleştirme|Ekleme noktası bir kod dosyasındaki açık küme ayracı üzerine yerleştirilse, hem ekleme noktası hem de kapanış ayracı vurgulanır. Bu özellik yanlış yer alan veya eksik ayraçlar hakkında anında geri bildirim sağlar. Otomatik Sınırlayıcı Vurgulama ayarı ( Araçlar Seçenekler Metin Düzenleyicisi ) ile **küme** ayracı  >  **eşleştirmeyi**  >  **açabilirsiniz veya kapatabilirsiniz.** Yazı Tipleri ve Renkler ayarında vurgulama **rengini değiştirebilirsiniz** (**Araçlar**  >  **Seçenekler**  >  **Ortamı).** Küme **Ayracı Eşleştirme (Vurgula)** veya Küme **Ayracı Eşleştirme (Dikdörtgen) 'i seçin.**|
|Yapı Görselleştirici|Noktalı çizgiler, kod dosyalarındaki eşleşen küme ayraçlarını bağarak açma ve kapatma küme ayracı çiftlerinin daha kolay bir şekilde açılmasını sağlar. Bu, kod tabanınıza daha hızlı kod bulumanıza yardımcı olabilir. Araçlar Seçenekler Metin Düzenleyici Genel sayfasının Görüntü bölümündeki  **Yapı** yönergelerini göster seçeneğiyle bu satırları   >    >  **açabilirsiniz veya**  >  **kapatabilirsiniz.**|
|Satır Numaraları|Satır numaraları, kod penceresinin sol kenar boşluğunda görüntülenebilir. Bunlar varsayılan olarak görüntülenmez. Bu seçeneği Metin Düzenleyici Tüm Diller ayarlarında ( **Araçlar Seçenekler Metin** Düzenleyici Tüm Diller  >    >    >  **) açabilirsiniz.** Bu dillerin ayarlarını değiştirerek tek tek programlama dilleri için satır numaralarını görüntüebilirsiniz (**Araçlar**  >  **Seçenekler Metin**  >  **Düzenleyici**  >  **\<language>** ). Satır numaralarının yazdırılacak olması için Yazdır iletişim **kutusunda Satır numaralarını ekle'yi** seçmeniz gerekir. |
|Değişiklik İzleme|Sol kenar boşluğun rengi, bir dosyada yaptığınız değişiklikleri izlemenizi sağlar. Dosya açıldığından ancak kaydedilemediği için yaptığınız değişiklikler, sol kenar boşluğunda sarı bir çubukla (seçim kenar boşluğu olarak bilinir) görünür. Değişiklikleri (ancak dosyayı kapatmadan önce) kaydedildikten sonra çubuk yeşile döner. Dosyayı kaydeddikten sonra bir değişikliği geri alarsanız çubuk turuncuya döner. Bu özelliği kapatmak ve açmak için Metin Düzenleyici **ayarları (** Araçlar Seçenekleri Metin Düzenleyicisi ) sayfasındaki **Değişiklikleri** **izle**  >    >  **seçeneğini değiştirin.**|
|Kod ve Metin Seçme|Metinleri standart sürekli akış modunda veya kutu modunda seçebilirsiniz. Burada satır kümesi yerine dikdörtgen bir metin bölümü seçebilirsiniz. Kutu modunda seçim yapmak için, fareyi seçimin üzerine **sürüklerken Alt** tuşuna basın (veya Alt Shift  + **tuşlarına** + **\<arrow key>** basın). Seçim, ilk karakter ve seçimdeki son karakter tarafından tanımlanan dikdörtgen içindeki tüm karakterleri içerir. Seçilen alana yazılmış veya yapıştırılmış her şey her satırda aynı noktaya eklenir.|
|Zoom|Ctrl tuşuna basarak ve basılı tutarak ve farenin üzerinde kaydırma tekerleğini hareket ettirerek **(veya Ctrl** Shift ile) herhangi bir kod penceresini yakınlaştırabilir veya  + **uzaklaştırabilirsiniz.** +  ve **Ctrl Shift** + **tuşlarına** + **basarak** azaltmak için). Belirli bir yakınlaştırma yüzdesi **ayarlamak** için kod penceresinin sol alt köşesindeki Yakınlaştırma kutusunu da kullanabilirsiniz. Yakınlaştırma özelliği araç pencerelerde çalışmıyor.|
|Sanal Alan|Varsayılan olarak, Visual Studio düzenleyicilerde satırlar son karakterden sonra  sona erer; böylece bir satırın sonundaki Sağ Ok tuşu imleci sonraki satırın başına taşır. Diğer bazı düzenleyicilerde bir satır son karakterden sonra sona erer ve imlecinizi satırın herhangi bir yerine yerleştirebilirsiniz. Araçlar Seçenekler Metin Düzenleyici Tüm Diller ayarlarında  >    >  **düzenleyicide**  >  **sanal alanı etkinleştirebilirsiniz.** Sanal Alanı veya Sözcük **Kaydırmayı etkinleştiresiniz,** ancak ikisini birden etkinleştirmeysiniz. |
|Yazdırma|Yazdır iletişim kutusundaki seçenekleri kullanarak **satır numaralarını** içerebilir veya bir dosyayı yazdırıyorsanız daraltılmış kod bölgelerini gizleyebilirsiniz. Sayfa **Kurulumu iletişim** kutusunda, Sayfa üst bilgisi seçeneğini kullanarak dosyanın tam yolunu ve adını yazdırmayı **da seçebilirsiniz.**<br /><br /> Araç Seçenekleri Ortam Yazı Tipleri ve Renkler  >  **iletişim kutusunda**  >  **renk** yazdırma  >  **seçeneklerini** ayarlayabilirsiniz. Renk **yazdırmayı** özelleştirmek **için Ayarları göster listesinde** Yazıcı'ya tıklayın. Bir dosyayı yazdırmak için, bir dosyayı düzenlemekten farklı renkler belirtebilirsiniz.|
|Genel Geri Alma ve TekrarLa|Düzenle **menüsündeki Son Genel Eylemi** Geri Al  ve **Son Genel** Eylemi Yeniden Gerçekleştir komutları, birden çok dosya etkileyen genel eylemleri geri alın veya tekrar gerçekleştirin. Genel eylemler bir sınıfı veya ad alanını yeniden ad alanını yeniden adlandırarak, çözümde bul ve değiştir işlemi gerçekleştirmeyi, veritabanını yeniden düzenlemeyi veya birden çok dosyada değişiklik yapan diğer eylemleri içerir. Genel geri alma ve yenidendo komutlarını geçerli Visual Studio eylemin uygulandığı çözümü kapatmış bile olsa eylemlere uygulayabilirsiniz.|

## <a name="advanced-editing-features"></a>Gelişmiş düzenleme özellikleri

Araç çubuğundaki Gelişmiş Düzenle menüsünde **bir dizi**  >  **gelişmiş** özellik bulabilirsiniz. Bu özelliklerin hepsi tüm kod dosyası türleri için kullanılamaz.

|Özellik|Açıklama|
|-|-|
|Belgeyi Biçimlendir|Kod satırlarının düzgün girintisini ayarlar ve küme ayraçlarını belgede ayrı satırlara taşır.|
|Biçim Seçimi|Kod satırlarının düzgün girintisini ayarlar ve küme ayraçlarını seçimde ayrı satırlara taşır.|
|Seçili Satırları Sekmeye Ekle|Uygun olduğunda sekmelerde baştaki boşlukları değiştirir.|
|Seçili Satırların Untabify|Baştaki sekmeleri boşluk olarak değiştirir. Dosyanız içinde yer alan tüm alanları sekmelere (veya tüm sekmeleri boşluklara) dönüştürmek için ve komutlarını `Edit.ConvertSpacesToTabs` `Edit.ConvertTabsToSpaces` kullanabilirsiniz. Bu komutlar menülerde Visual Studio, ancak Bunları Hızlı Erişim penceresinden veya komut **penceresinden** çağırabilirsiniz.|
|Büyük Harf Yapma|Seçimdeki tüm karakterleri büyük harf olarak değiştirir veya seçim yoksa ekleme noktasındaki karakteri büyük harf olarak değiştirir. Kısayol: **Ctrl** + **Shift** + **U**.|
|Küçük harf yap|Seçimdeki tüm karakterleri küçük harfe çevirir veya seçim yoksa ekleme noktasındaki karakteri küçük harfe dönüştürür. Kısayol: **CTRL** + **U**.|
|Seçili satırları yukarı taşı|Seçili satırı bir satır yukarı kaydırır. Kısayol: **alt** + **yukarı ok**.|
|Seçili satırları aşağı taşı|Seçili satırı bir satır aşağı kaydırır. Kısayol: **alt** + **aşağı ok**.|
|Yatay boşluğu Sil|Geçerli satırın sonundaki sekmeleri veya boşlukları siler. Kısayol: **CTRL** + **K**, **CTRL**+**\\**|
|Boşluğu görüntüle|Boşlukları, kabarık noktalar olarak ve ok olarak sekme olarak görüntüler. Bir dosyanın sonu dikdörtgen bir karakter olarak görüntülenir. **Araç**  >  **seçenekleri**  >  **metin düzenleyici**  >  **tüm diller**  >  **sözcük kaydırması** sözcük kaydırması  >  **için görünür glifleri göster** seçili ise, bu glif de görüntülenir.|
|Sözcük Kaydırma|Belgedeki tüm satırların kod penceresinde görünür olmasını sağlar. Word kaydırmayı, **metin düzenleyici tüm diller** ayarlarında (**Araçlar**  >  **Seçenekler**  >  **metin düzenleyici**  >  **tüm diller**) açabilir ve açık bir şekilde açabilirsiniz.|
|Açıklama seçimi|Seçime veya geçerli satıra Açıklama karakterleri ekler. Kısayol: **CTRL** + **K**, **CTRL** + **C**|
|Seçimi açıklama kaldır|Seçim veya geçerli satırdan açıklama karakterlerini kaldırır. Kısayol: **CTRL** + **K**, **CTRL** + **U**|
|Satır girintisini artır|Seçili satırlara veya geçerli satıra bir sekme (veya eşdeğer boşluk) ekler.|
|Satır girintisini azalt|Seçili satırlardan veya geçerli satırdan bir sekmeyi (veya eşdeğer alanları) kaldırır.|
|Etiket Seç|Etiketler (örneğin, XML veya HTML) içeren bir belgede etiketi seçer.|
|Etiket Içeriğini seçin|Etiketler (örneğin, XML veya HTML) içeren bir belgede, içeriği seçer.|

## <a name="navigate-and-find-code"></a>Gezinme ve kod bulma

Geriye doğru gitme ve önceki ekleme noktalarına iletme, bir tür veya üyenin tanımını görüntüleme ve gezinti çubuğunu kullanarak belirli bir yönteme atlama dahil olmak üzere birkaç farklı yolla kod düzenleyicide gezinebilirsiniz. Daha fazla bilgi için bkz. [gezinme kodu](navigating-code.md).

## <a name="find-references-in-your-code-base"></a>Kod tabanınız için başvuruları bulma

Kodlarınızın tamamında belirli kod öğelerine başvurulduğunu bulmak için, **tüm başvuruları bul** komutunu kullanabilir veya **SHIFT** + **F12** tuşlarına basabilirsiniz. Ayrıca, bir tür veya üyeye tıkladığınızda, **başvuru vurgulama** özelliği bu tür veya üyeye yapılan tüm başvuruları otomatik olarak vurgular. Daha fazla bilgi için bkz. [kodunuzda başvuruları bulma](finding-references.md).

## <a name="customize-the-editor"></a>Düzenleyiciyi özelleştirme

Visual Studio ayarlarınızı başka bir geliştiriciyle paylaşabilir, ayarlarınızı bir standart ile uyumlu yapabilir veya **araçlar** menüsünde **Ayarlar içeri ve dışarı aktarma sihirbazı** komutunu kullanarak Visual Studio varsayılan ayarlara geri dönebilirsiniz. **Ayarlar içeri ve dışarı aktarma sihirbazı**' nda, seçili genel ayarları veya dili ve projeye özgü ayarları değiştirebilirsiniz.

Yeni kısayol tuşlarını tanımlamak veya mevcut kısayol tuşlarını yeniden tanımlamak için **Araçlar**  >  **Seçenekler**  >  **ortam**  >  **klavyesi**' ne gidin. Kısayol tuşları hakkında daha fazla bilgi için bkz. [varsayılan klavye kısayolları](../ide/default-keyboard-shortcuts-in-visual-studio.md).

JavaScript 'e özgü düzenleyici seçenekleri için bkz. [JavaScript Düzenleyicisi seçenekleri](../ide/reference/options-text-editor-javascript-formatting.md).

## <a name="see-also"></a>Ayrıca bkz.

- [kaynak düzenleyicisi (Mac için Visual Studio)](/visualstudio/mac/source-editor)
- [Visual Studio IDE](../get-started/visual-studio-ide.md)
- [Visual Studio C++ ile çalışmaya başlama](/cpp/get-started/tutorial-console-cpp)
- [ASP.NET C# ve Visual Studio ile çalışmaya başlama](../get-started/csharp/tutorial-aspnet-core.md)
- [Visual Studio 'de Python ile çalışmaya başlama](../ide/quickstart-python.md)
