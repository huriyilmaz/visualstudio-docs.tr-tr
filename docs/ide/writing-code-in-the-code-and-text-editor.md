---
title: Kod düzenleyicisi özellikleri
description: Kod ve metin yazmanızı ve yönetmenizi kolaylaştırmak Visual Studio kod düzenleyicisinin sağladığı özellikler hakkında bilgi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 01/31/2022
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
ms.openlocfilehash: 979253347b6947121ae9de42b81e38375faa768d
ms.sourcegitcommit: 3766c051f9a8b35106b16f751db7fecde0b92254
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/02/2022
ms.locfileid: "137951487"
---
# <a name="features-of-the-code-editor"></a>Kod düzenleyicisinin özellikleri

Visual Studio düzenleyicisi, kodunuzu ve metninizi yazmanızı ve yönetmenizi kolaylaştıran birçok özellik sağlar. Altı çizili kullanarak farklı kod bloklarını genişletebilirsiniz ve daraltabilirsiniz. IntelliSense, Object Browser ve Çağrı Hiyerarşisi kullanarak kod hakkında **daha** fazla bilgi edinebilirsiniz. Git, Tanıma Git ve Tüm **Başvuruları Bul** gibi özellikleri **kullanarak kod bulabilirsiniz**.  Kod parçacıklarıyla kod blokları ekleyebilirsiniz ve Kullanımdan Oluştur gibi özellikleri kullanarak **kod da üretebilirsiniz**. Daha önce Visual Studio kullanmadıysanız bkz. [Kod düzenleyicisini kullanmayı öğrenin](../get-started/tutorial-editor.md).

> [!NOTE]
> Bu konu, Visual Studio için Windows. Daha Mac için Visual Studio için bkz[. Kaynak düzenleyicisi (Mac için Visual Studio)](/visualstudio/mac/source-editor).

Kodunuzu birkaç farklı şekilde görüntüleyebilirsiniz. Varsayılan olarak **, Çözüm Gezgini** göre düzenlenmiş kodunuzu gösterir. Kodunuzu sınıflara göre **Sınıf Görünümü** görüntülemek için pencerenin en altındaki Sınıf Görünümü sekmesine tıkleyebilirsiniz.

Tek veya birden çok dosyada metin arayabilir ve değiştirebilirsiniz. Daha fazla bilgi için bkz [. Metin bulma ve değiştirme](../ide/finding-and-replacing-text.md). Normal ifadeleri kullanarak metin bulabilir ve değiştirebilirsiniz. Daha fazla bilgi için bkz[. Normal ifadeleri Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

Farklı Visual Studio farklı özellik kümeleri sunar ve bazı durumlarda özellikler farklı dillerde farklı davranır. Bu farklılıkların çoğu özelliklerin açıklamalarında belirtilmiştir, ancak daha fazla bilgi için belirli Visual Studio bölümlerine bakebilirsiniz.

## <a name="editor-features"></a>Düzenleyici özellikleri

|Özellik|Açıklama|
|-|-|
|Söz Dizimi Renklendirmesi|Kod ve işaretleme dosyalarının bazı söz dizimi öğeleri, ayırt etmek için farklı renklendirilmiştir. Örneğin, anahtar sözcükler (`using`C# `Imports` ve Visual Basic gibi) bir renktir, ancak türler (ve `Console` `Uri`gibi) başka bir renktir. Dize değişmez öğeleri ve açıklamalar gibi diğer söz dizimi öğeleri de renklendirmeye sahiptir. C++ türleri, numaralarını ve makroları diğer belirteçler arasında ayırt etmek için renk kullanır.<br /><br /> Her tür için varsayılan rengi görebilir ve Araçlar menüsünden açabilirsiniz Yazı Tipleri ve Renkler [, Ortam,](../ide/reference/fonts-and-colors-environment-options-dialog-box.md) Seçenekler iletişim kutusunda herhangi bir söz dizimi öğesinin rengini **değiştirebilirsiniz** .|
|Hata ve Uyarı İşaretleri|Kod eklerken ve çözümlerinizi eklerken, (a) farklı renkli dalgalı alt çizgileri (dalgalı çizgiler olarak bilinir) veya (b) ampullerin kodunda görüntü olduğunu görebilir. Kırmızı geçişler söz dizimi hatalarını, mavi derleyici hatalarını, yeşil uyarıları ve mor da diğer hata türlerini gösterir. [Hızlı Eylemler](../ide/quick-actions.md) , sorunlar için düzeltmeler önerir ve düzeltmeyi uygulamayı kolaylaştırır.<br /><br /> AraçlarSetirmelerEnvironmentFonts  >  >  ve Renkler iletişim kutusunda her hata ve uyarı iki durumlu **düğmesinin** >  **varsayılan rengini** görüntüebilirsiniz. Söz **Dizimi Hatası**, **Derleyici Hatası**, Uyarı **ve** Diğer **Hata'ya bakın**.|
|Küme Ayracı Eşleştirme|Ekleme noktası bir kod dosyasındaki açık küme ayracı üzerine yerleştirilse, hem ekleme noktası hem de kapanış ayracı vurgulanır. Bu özellik yanlış yer alan veya eksik ayraçlar hakkında anında geri bildirim sağlar. Otomatik Sınırlayıcı Vurgulama ayarıyla **(** > AraçlarSeçmelerMetin Düzenleyicisi) ayraç **eşleştirmeyi açabilirsiniz** >  **veya kapatabilirsiniz**. Yazı Tipleri ve Renkler ayarında **vurgu rengini değiştirebilirsiniz** (**AraçlarOptionsEnvironment** >  > ). Küme **Ayracı Eşleştirme (Vurgula)** veya Küme **Ayracı Eşleştirme (Dikdörtgen)'i seçin**.|
|Yapı Görselleştirici|Noktalı çizgiler, kod dosyalarındaki eşleşen küme ayraçlarını bağarak açma ve kapatma küme ayracı çiftlerini daha kolay bir şekilde görmelerini sağlar. Bu, kod tabanınıza daha hızlı kod bulumanıza yardımcı olabilir. AraçlarSekimlerMetin  >  >  DüzenleyicisiGenel  sayfasının Görüntüleme bölümündeki Yapı yönergelerini göster ile bu **satırları aç** >  **veya kapatabilirsiniz**.|
|Satır Numaraları|Satır numaraları, kod penceresinin sol kenar boşluğunda görüntülenebilir. Bunlar varsayılan olarak görüntülenmez. Bu seçeneği Metin Düzenleyici Tüm Diller **ayarlarında (****AraçlarSeçmelerMetin** >  >  **DüzenleyiciTüm** >  **Diller) açabilirsiniz**. Bu dillerin ayarlarını değiştirerek (AraçlarSeçmelerMetin Düzenleyicisi **) tek** >  tek programlama dilleri için **satır numaralarını** >  **görüntüebilirsiniz** > **\<language>**. Satır numaralarının yazdırılacak olması için Yazdır iletişim **kutusunda Satır numaralarını ekle'yi** seçmeniz gerekir.|
|Değişiklik İzleme|Sol kenar boşluğun rengi, bir dosyada yaptığınız değişiklikleri izlemenizi sağlar. Dosya açıldığından ancak kaydedilemediği için yaptığınız değişiklikler, sol kenar boşluğunda sarı bir çubukla (seçim kenar boşluğu olarak bilinir) görünür. Değişiklikleri (ancak dosyayı kapatmadan önce) kaydedildikten sonra çubuk yeşile döner. Dosyayı kaydeddikten sonra bir değişikliği geri alarsanız çubuk turuncuya döner. Bu özelliği kapatmak ve açmak için Metin Düzenleyici **ayarlarında** **(** > AraçlarSeçmelerMetin **Düzenleyicisi**) Değişiklikleri **izle** >  **seçeneğini değiştirin**.|
|Kod ve Metin Seçme|Metinleri standart sürekli akış modunda veya kutu modunda seçebilirsiniz. Burada satır kümesi yerine dikdörtgen bir metin bölümü seçebilirsiniz. Kutu modunda seçim yapmak için, fareyi seçimin üzerine **sürüklerken Alt** tuşuna basın (veya **AltShift'e**+ **basın**+**\<arrow key>**). Seçim, ilk karakter ve seçimdeki son karakter tarafından tanımlanan dikdörtgen içindeki tüm karakterleri içerir. Seçilen alana yazılmış veya yapıştırılmış her şey her satırda aynı noktaya eklenir.|
|Zoom|Ctrl tuşuna basarak ve basılı tutarak ve farenin üzerinde kaydırma tekerleğini (**veya CtrlShift**) hareket ettirerek herhangi bir kod penceresini yakınlaştırabilir veya **uzaklaştırabilirsiniz**++**.** ve azaltmak için **CtrlShift**++ **tuşlarına** basın). Belirli bir yakınlaştırma yüzdesi **ayarlamak** için kod penceresinin sol alt köşesindeki Yakınlaştırma kutusunu da kullanabilirsiniz. Yakınlaştırma özelliği araç pencerelerde çalışmıyor.|
|Sanal Alan|Varsayılan olarak, Visual Studio düzenleyicilerde satırlar son karakterden sonra sona erer; böylece bir satırın  sonundaki Sağ Ok tuşu imleci sonraki satırın başına taşır. Diğer bazı düzenleyicilerde bir satır son karakterden sonra sona erer ve imlecinizi satırın herhangi bir yerine yerleştirebilirsiniz. AraçlarSenizmetin DüzenleyicisiTüm **Diller** >  ayarlarında **düzenleyicide** >  >  **sanal alanı etkinleştirebilirsiniz**. Sanal Alanı veya Sözcük **Kaydırmayı etkinleştiresiniz** , ancak **ikisini** birden etkinleştiresiniz.|
|Yazdırma|Yazdır iletişim kutusundaki seçenekleri kullanarak **satır numaralarını** içerebilir veya bir dosyayı yazdırıyorsanız daraltılmış kod bölgelerini gizleyebilirsiniz. Sayfa **Kurulumu iletişim** kutusunda, Sayfa üst bilgisi'yi seçerek dosyanın tam yolunu ve adını **yazdırmayı da seçebilirsiniz**.<br /><br /> AraçlarOptionsEnvironmentFonts >  >  ve Renkler iletişim **kutusunda** >  renk **yazdırma seçeneklerini** ayarlayabilirsiniz. Renk **yazdırmayı** özelleştirmek **için Ayarları göster listesinde** Yazıcı'ya tıklayın. Bir dosyayı yazdırmak için, dosyayı düzenlemekten farklı renkler belirtebilirsiniz.|
|Genel Geri Alma ve TekrarLa|Düzenle **menüsündeki Son Genel Eylemi** Geri Al ve **Son Genel** Eylemi Yeniden Gerçekleştir  komutları, birden çok dosya etkileyen genel eylemleri geri alın veya tekrar gerçekleştirin. Genel eylemler bir sınıfı veya ad alanını yeniden ad alanını yeniden adlandırarak, çözümde bul ve değiştir işlemi gerçekleştirmeyi, veritabanını yeniden düzenlemeyi veya birden çok dosyada değişiklik yapan diğer eylemleri içerir. Bir eylemin uygulandığı çözümü kapatmış olsa bile genel geri alma ve Visual Studio eylemlerini geçerli oturumda eylemlere uygulayabilirsiniz.|

## <a name="advanced-editing-features"></a>Gelişmiş düzenleme özellikleri

Araç çubuğundaki  > **EditAdvanced menüsünde bir dizi gelişmiş** özellik bulabilirsiniz. Bu özelliklerin hepsi tüm kod dosyası türleri için kullanılamaz.

|Özellik|Açıklama|
|-|-|
|Belgeyi Biçimlendir|Kod satırlarının düzgün girintisini ayarlar ve küme ayraçlarını belgede ayrı satırlara taşır.|
|Biçim Seçimi|Kod satırlarının düzgün girintisini ayarlar ve küme ayraçlarını seçimde ayrı satırlara taşır.|
|Seçili Satırları Sekmeye Ekle|Uygun olduğunda sekmelerde baştaki boşlukları değiştirir.|
|Seçili Satırların Untabify|Baştaki sekmeleri boşluk olarak değiştirir. Dosyanız içinde yer alan tüm alanları sekmelere (veya tüm sekmeleri boşluklara) dönüştürmek için ve komutlarını kullanabilirsiniz `Edit.ConvertSpacesToTabs` `Edit.ConvertTabsToSpaces` . Bu komutlar, Visual Studio menülerde görünmez, ancak Bunları Hızlı Erişim penceresinden **veya komut** penceresinden çağırabilirsiniz.|
|Büyük Harf Yapma|Seçimdeki tüm karakterleri büyük harf olarak değiştirir veya seçim yoksa ekleme noktasındaki karakteri büyük harf olarak değiştirir. Kısayol: **CtrlShiftU**++.|
|Küçük Harf Yapma|Seçimdeki tüm karakterleri küçük harf olarak değiştirir veya seçim yoksa ekleme noktasındaki karakteri küçük harf olarak değiştirir. Kısayol: **CtrlU**+.|
|Seçili Satırları Yukarı Taşı|Seçilen satırı bir satır yukarı taşır. Kısayol: **AltUp**+ **Oku**.|
|Seçili Satırları Aşağı Taşı|Seçili satırı bir satır aşağı taşır. Kısayol: **AltDown**+ **Oku**.|
|Yatay Boşluk Silme|Geçerli satırın sonundaki sekmeleri veya boşlukları siler. Kısayol: **CtrlK**+, **Ctrl**+**\\**|
|Boşluğu Görüntüle|Boşlukları yükseltilmiş nokta olarak, sekmeleri ise oklar olarak görüntüler. Bir dosyanın sonu dikdörtgen bir glyph olarak görüntülenir.  > **ToolsOptionsText** >  **EditorTüm** >  **DillerWord** >  **WrapShow** >  sözcük kaydırma için görünür **glyph'ler** seçilirse, söz dizim de görüntülenir.|
|Sözcük Kaydırma|Belgelerdeki tüm satırların kod penceresinde görünür olmasına neden olur. Metin Düzenleyici Tüm Diller ayarlarında (**AraçlarSeçmelerMetin** >  >  DüzenleyiciTüm Diller) sözcük **kaydırmayı kapatabilirsiniz** > **.**|
|Açıklama Seçimi|Seçime veya geçerli satıra açıklama karakterleri ekler. Kısayol: **CtrlK**+, **CtrlC**+|
|Uncomment Selection|Seçimden veya geçerli satırdan açıklama karakterlerini kaldırır. Kısayol: **CtrlK**+, **CtrlU**+|
|Satır Girintisini Artırma|Seçili satırlara veya geçerli satıra bir sekme (veya eşdeğer boşluklar) ekler.|
|Satır Girintisini Azalt|Seçili satırlardan veya geçerli satırdan bir sekmeyi (veya eşdeğer boşlukları) kaldırır.|
|Etiket'i seçin|Etiketleri içeren bir belgede (örneğin, XML veya HTML), etiketi seçer.|
|İçeriği Etiketle'yi seçin|Etiketleri içeren bir belgede (örneğin, XML veya HTML), içeriği seçer.|

## <a name="navigate-and-find-code"></a>Kodda gezinme ve kod bulma

Geri ve ileri doğru önceki ekleme noktalarına gezinme, bir tür veya üyenin tanımını görüntüleme ve gezinti çubuğunu kullanarak belirli bir yönteme atlama da dahil olmak üzere kod düzenleyicisinde birkaç farklı şekilde gezinebilirsiniz. Daha fazla bilgi için bkz [. Kodda gezinme](navigating-code.md).

## <a name="find-references-in-your-code-base"></a>Kod tabanınıza başvuru bulma

Kod tabanınız genelinde belirli kod öğelerine nerede başvurul olduğunu bulmak için Tüm Başvuruları Bul komutunu  kullanabilir veya **ShiftF12 tuşuna**+ basabilirsiniz. Ayrıca, bir türe veya üyeye tıklarken, başvuru **vurgulama özelliği otomatik** olarak o türe veya üyeye yapılan tüm başvuruları vurgular. Daha fazla bilgi için bkz [. Kodundaki başvuruları bulma](finding-references.md).

## <a name="generate-fix-or-refactor-code"></a>Kod oluşturma, düzeltme veya yeniden düzenleme

Kodu oluşturma, düzeltme Visual Studio yeniden düzenlemeye yardımcı olmak için birçok farklı yol vardır.

- Anahtar bloğu [veya enum](code-snippets.md) bildirimi gibi bir şablon [eklemek için kod](/dotnet/csharp/language-reference/keywords/switch) [parçacıklarını kullanabilirsiniz](/dotnet/csharp/language-reference/keywords/enum) .

- Hızlı [Eylemler'i sınıflar](quick-actions.md) ve özellikler gibi kod oluşturmak veya yerel bir değişken tanıtmak için kullanabilirsiniz. Ayrıca Hızlı Eylemler'i kullanarak kodu [geliştirebilirsiniz. Örneğin](common-quick-actions.md), gereksiz tür değiştirmeleri ve kullanılmayan değişkenleri kaldırmak veya değişkenlere erişmeden önce null denetimler eklemek için.

- Bir değişkeni [yeniden adlandırmak](refactoring-in-visual-studio.md) , yöntem parametrelerini yeniden sıralamak veya bir türü dosya adıyla eşitlemek için kodu yeniden düzenlerini kullanabilirsiniz.

## <a name="customize-the-editor"></a>Düzenleyiciyi özelleştirme

Visual Studio ayarlarınızı başka bir geliştiriciyle paylaşabilir, ayarlarınızın standartla uyumlu hale getirebilirsiniz veya Araçlar menüsündeki Ayarlar İçeri ve Dışarı Aktarma Sihirbazı komutunu kullanarak varsayılan Visual Studio ayarlarına **geri dönebilirsiniz**. İçeri ve **Dışarı Aktarma Ayarlar Sihirbazı'nda**, seçilen genel ayarları veya dili ve projeye özgü ayarları değiştirebilirsiniz.

Yeni kısayol tuşları tanımlamak veya mevcut kısayol anahtarlarını yeniden tanımlamak için **AraçlarOptionsEnvironmentKeyboard'a** >  >  >  **gidin**. Kısayol tuşları hakkında daha fazla bilgi için bkz. [Varsayılan klavye kısayolları](../ide/default-keyboard-shortcuts-in-visual-studio.md).

JavaScript'e özgü düzenleyici seçenekleri için bkz. [JavaScript düzenleyicisi seçenekleri](../ide/reference/options-text-editor-javascript-formatting.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Kaynak düzenleyicisi (Mac için Visual Studio)](/visualstudio/mac/source-editor)
- [Visual Studio IDE](../get-started/visual-studio-ide.md)
- [Kullanmaya başlayın C++ ile Visual Studio](/cpp/get-started/tutorial-console-cpp)
- [Kullanmaya başlayın C# ve ASP.NET ile Visual Studio](../get-started/csharp/tutorial-aspnet-core.md)
- [Kullanmaya başlayın Python ile Visual Studio](../ide/quickstart-python.md)
