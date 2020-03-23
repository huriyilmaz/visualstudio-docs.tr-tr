---
title: Metni bulma ve değiştirme ve çok yönlü seçim
ms.date: 08/14/2018
ms.topic: conceptual
f1_keywords:
- vs.find
- vs.findreplacecontrol
- vs.findreplace.findsymbol
- vs.findreplace.symbol
- findresultswindow
- vs.findreplace.quickreplace
- vs.findsymbol
- vs.findresults1
- vs,findsymbolwindow
- vs.findreplace.quickfind
- vs.lookin
- vs.replace
helpviewer_keywords:
- text searches
- Replace in Files dialog box
- Find in Files dialog box
- text searches, finding and replacing text
- text, finding and replacing
- find and replace
- find text
- replace text
- multi-caret selection
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ffc31a0d0e2b6878b5dd5173a35ce4f538e135be
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590351"
---
# <a name="find-and-replace-text"></a>Metin bulma ve değiştirme

Visual Studio düzenleyicisinde Metni Bul ve [Değiştir](#find-and-replace-control) **(Ctrl**+**F** veya **Ctrl**+**H)** veya [Dosyalarda Bul/Değiştir](#find-in-files-and-replace-in-files) **(Ctrl**+**Shift**+**F** veya **Ctrl**+**Shift**+**H)** kullanarak metni bulabilir ve değiştirebilirsiniz. Ayrıca, *[çok noktalı seçimi](#multi-caret-selection)* kullanarak yalnızca *bazı* desen örneklerini bulabilir ve değiştirebilirsiniz.

> [!TIP]
> Değişkenler ve yöntemler gibi kod sembollerini yeniden adarıyorsanız, bunları bul-değiştir'i kullanmaktan daha iyi *[bir şekilde yeniden düzenlemeniz](../ide/reference/rename.md)* daha iyidir. Refactoring akıllıdır ve kapsamı anlar, oysa bul-değiştir ve bul tüm örnekleri körü körüne değiştirir.

Bul ve değiştir işlevleri düzenleyicide, **Sonuçları Bul** pencereleri gibi diğer metin tabanlı pencerelerde, XAML tasarımcısı ve Windows Forms tasarımcısı gibi tasarımcı pencerelerinde ve araç pencerelerinde kullanılabilir.

Aramaları geçerli belgeye, geçerli çözüme veya özel bir klasör kümesine kapsamda sürebilirsiniz. Ayrıca, çok dosyalı aramalar için bir dosya adı uzantıları kümesi de belirtebilirsiniz. .NET [normal ifadeleri](../ide/using-regular-expressions-in-visual-studio.md)kullanarak arama sözdizimini özelleştirin.

> [!TIP]
> [Bul/Komut](../ide/find-command-box.md) kutusu araç çubuğu denetimi olarak kullanılabilir, ancak varsayılan olarak görünmez. **Bul/Komut** kutusunu görüntülemek için **Standart** araç çubuğunda **Ekle veya Kaldır Düğmeleri'ni** seçin ve ardından **Bul'u**seçin.

## <a name="find-and-replace-control"></a>Denetimi Bul ve Değiştir

- Geçerli dosyada bir dize *bulmak* için kısayol olarak **Ctrl**+**F** tuşuna basın.
- Geçerli dosyadaki bir dizeyi *bulmak ve değiştirmek* için kısayol olarak **Ctrl**+**H** tuşuna basın.

**Bul ve Değiştir** denetimi kod düzenleyicipenceresinin sağ üst köşesinde görünür. Geçerli belgedeki verilen arama dizesinin her oluşumunu hemen vurgular. **Sonrakini Bul** düğmesini veya arama denetimindeki **Öncekileri Bul** düğmesini seçerek bir oluşumdan diğerine gidebilirsiniz.

![Visual Studio'da Bul ve Değiştir](media/find-and-replace-box.png)

**Metin** kutusunubul'un yanındaki düğmeyi seçerek değiştirme seçeneklerine erişebilirsiniz. Aynı anda bir değişiklik yapmak için, Metin Kutusunu **Değiştir'in** yanındaki **İleri'yi Değiştir** düğmesini seçin. Tüm eşleşmeleri değiştirmek için **Tümünü Değiştir** düğmesini seçin.

Eşleşmeler için vurgu rengini değiştirmek için **Araçlar** menüsünü seçin, **Seçenekler'i**seçin ve ardından **Çevre'yi**seçin ve Yazı Tipleri **ve Renkler'i**seçin. Liste **için Göster ayarlarında** Metin **Düzenleyici'yi**seçin ve ardından **Öğeleri Görüntüle** listesinde **Vurgula (Uzantı)** seçin.

### <a name="search-tool-windows"></a>Araç pencerelerini ara

**Ctrl+F**tuşuna basarak **Bul** > **ve Değiştir'i** seçerek, **Çıktı** pencereleri ve **Sonuçları Bul** pencereleri gibi kod veya metin pencerelerinde **Bul** denetimini kullanabilirsiniz.

Bazı araç pencerelerinde **Bul** denetiminin bir sürümü de mevcuttur. Örneğin, arama kutusuna metin girerek **Araç Kutusu** penceresindeki denetimler listesini filtreleyebilirsiniz. İçeriklerini aramanıza olanak tanıyan diğer araç pencereleri çözüm **gezgini,** **Özellikler** penceresi ve **Takım Gezgini'ni**içerir.

## <a name="find-in-files-and-replace-in-files"></a>Dosyalarda Bul ve Dosyalarda Değiştir

- Birden çok dosyada bir dize *bulmak* için kısayol olarak **Ctrl**+**Shift**+**F** tuşuna basın.
- Birden çok dosyadaki bir dizeyi *bulmak ve değiştirmek* için kısayol olarak **Ctrl**+**Shift**+**H** tuşuna basın.

**Dosyalarda Bul/Değiştir** **denetimi** gibi çalışır, ancak aramanız için bir kapsam tanımlayabilirsiniz. Yalnızca düzenleyicideki geçerli açık dosyayı aramakla birlikte, tüm açık belgeleri, tüm çözümü, geçerli projeyi ve seçili klasör kümelerini de arayabilirsiniz. Dosya adı uzantısına göre de arama yapabilirsiniz. **Dosyalarda Bul/Değiştir** iletişim kutusuna erişmek **için, Edit** menüsünde **Bul ve Değiştir'i** seçin (veya **Ctrl**+**Shift**+**F**tuşuna basın).

![Visual Studio'da Dosyaları Bul](media/find-in-files-box.png)

### <a name="find-results"></a>Sonuçları Bul

**Tümünü Bul'u**seçtiğinizde, **Sonuçları Bul** penceresi açılır ve aramanızın eşleşmelerini listeler. Listede bir sonuç seçilmesi ilişkili dosyayı görüntüler ve eşleşmeyi vurgular. Dosya düzenleme için zaten açık değilse, sekenin sağ tarafındaki bir önizleme sekmesinde açılır. **Sonuçları** Bul listesinde arama yapmak için **Bul** denetimini kullanabilirsiniz.

### <a name="create-custom-search-folder-sets"></a>Özel arama klasörü kümeleri oluşturma

**Arama Klasörleri Seç** düğmesini **(...** gibi görünüyor) **kutusunun** yanındaki arama kapsamını belirleyebilirsiniz. Arama **Klasörleri Seç** iletişim kutusunda, aranacak bir klasör kümesi belirleyebilir ve daha sonra yeniden kullanabilmek için belirtimi kaydedebilirsiniz.

> [!TIP]
> Uzak bir makinenin sürücüsünün yerel makinenize eşlenemesini yaptımysa, uzak makinede aramak için klasörler belirtebilirsiniz.

### <a name="create-custom-component-sets"></a>Özel bileşen kümeleri oluşturma

**Kutudaki Bak'ın** yanındaki Özel Bileşen **Setini Edit** düğmesini seçerek bileşen kümelerini arama kapsamınız olarak tanımlayabilirsiniz. Yüklü .NET veya COM bileşenlerini, çözümünüze dahil olan Visual Studio projelerini veya herhangi bir derleme veya tür kitaplığını (*.dll*, *.tlb*, *.olb*, *.exe*, veya *.ocx)* belirtebilirsiniz. Başvuruları aramak için **başvurulardaki Bak** kutusunu seçin.

## <a name="multi-caret-selection"></a>Çok bakımlı seçim

> [!NOTE]
> Bu bölüm Windows'daki Visual Studio için geçerlidir. Mac için Visual Studio için [Blok seçimine](/visualstudio/mac/block-selection)bakın.

**Visual Studio 2017 sürümü 15.8 tanıtıldı**

Aynı ediyi aynı anda iki veya daha fazla yerde yapmak için *çok noktalı seçimi* kullanın. Örneğin, aynı metni ekleyebilir veya aynı anda birden çok konumda varolan metni değiştirebilirsiniz.

Aşağıdaki ekran görüntüsünde, `-0000` üç konumda seçilir; kullanıcı **Sil**tuşuna baslarsa, üç seçim de silinir:

![Visual Studio'daki bir XML dosyasında çok noktalı seçim](media/multi-caret-selection.png)

Birden çok basamak seçmek için, her zamanki gibi ilk metin seçimini tıklatın veya yapın ve ardından her ek konumda metni tıklatırken veya seçerken **Alt** tuşuna basın. Ayrıca, eşleşen metni ek seçimler olarak otomatik olarak ekleyebilir veya her satırda aynı şekilde düzenlemek için bir metin kutusu seçebilirsiniz.

> [!TIP]
> Fare için değiştirici tuşu olarak **Alt'ı** seçtiyseniz, **Araçlar** > Da Tanıma Git**seçeneğini**tıklattıysanız, çok bakımlı seçim devre dışı bırakılır.

### <a name="commands"></a>Komutlar

Çok yönlü seçim davranışları için aşağıdaki tuşları ve eylemleri kullanın:

|Kısayol|Eylem|
|-|-|
|**Ctrl**+**Alt** + tıklayın|İkincil bir caret ekleme|
|**Ctrl**+**Alt** + çift tıklatma|İkincil sözcük seçimi ekleme|
|**Ctrl**+**Alt** + tıklayın + sürükle|İkincil seçim ekleme|
|**Shift**+**Alt**+**.**|Bir sonraki eşleşen metni seçim olarak ekleme|
|**Ctrl**+**Shift**+**Alt**+**,**|Tüm eşleşen metni seçim olarak ekleme|
|**Shift**+**Alt**+**,**|Seçilen son oluşumu kaldırma|
|**Ctrl**+**Shift**+**Alt**+**.**|Sonraki eşleşen oluşumu atla|
|**Alt** + tıklayın|Kutu seçimi ekleme|
|**Esc** veya tıklayın|Tüm seçimleri temizle|

Komutlardan bazıları **Birden Çok Bakım**altında **Edit** menüsünde de mevcuttur:

![Visual Studio'da birden fazla carets fly-out menü](media/edit-menu-multiple-carets.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da düzenli ifadeler kullanma](../ide/using-regular-expressions-in-visual-studio.md)
- [Visual Studio'da refactor kodu](../ide/refactoring-in-visual-studio.md)
- [Blok seçimi (Mac için Visual Studio)](/visualstudio/mac/block-selection)
