---
title: Metin bul ve Değiştir ve çok şapka seçimi
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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590351"
---
# <a name="find-and-replace-text"></a>Metin bulma ve değiştirme

Visual Studio Düzenleyicisi 'ndeki metni [Bul ve Değiştir](#find-and-replace-control) (**CTRL**+**F** veya **CTRL**+**H**) kullanarak bulabilir ve değiştirebilir veya [dosyalarda Bul/Değiştir](#find-in-files-and-replace-in-files) (**CTRL**+**SHIFT**+**F** ya da **CTRL**+**SHIFT**+**H**). Ayrıca, *[Çoklu şapka seçimini](#multi-caret-selection)* kullanarak bir düzenin yalnızca *bazı* örneklerini bulabilir ve değiştirebilirsiniz.

> [!TIP]
> Değişkenler ve yöntemler gibi kod sembollerini yeniden adlandırıyorsanız, bul ve Değiştir ' i kullanmaya kıyasla yeniden *[düzenleme](../ide/reference/rename.md)* daha iyidir. Yeniden düzenleme akıllı ve anlamıştır, ancak bul ve Değiştir, tüm örneklerin yerini alır.

Bul ve Değiştir işlevleri, düzenleyicide, XAML Tasarımcısı ve Windows Forms tasarımcı gibi tasarımcı pencereleri ve araç pencereleri gibi çeşitli metin tabanlı **pencereler için düzenleyicide** bulunur.

Aramaları geçerli belge, geçerli çözüm veya özel bir klasör kümesiyle kapsamını belirleyebilirsiniz. Ayrıca, çok dosya aramaları için bir dosya adı uzantıları kümesi de belirtebilirsiniz. .NET [normal ifadelerini](../ide/using-regular-expressions-in-visual-studio.md)kullanarak arama sözdizimini özelleştirin.

> [!TIP]
> [Bul/komut](../ide/find-command-box.md) kutusu, bir araç çubuğu denetimi olarak kullanılabilir, ancak varsayılan olarak görünmez. **Bul/komut** kutusunu göstermek için **standart** araç çubuğunda **Düğme Ekle veya Kaldır** ' ı seçin ve ardından **bul**' u seçin.

## <a name="find-and-replace-control"></a>Bul ve Değiştir denetimi

- Geçerli dosyada bir dize *bulmak* için kısayol olarak **CTRL**+**F** tuşlarına basın.
- Geçerli dosyadaki bir dizeyi *bulmak ve değiştirmek* için kısayol olarak **CTRL**+**H** tuşuna basın.

**Bul ve Değiştir** denetimi, kod Düzenleyicisi penceresinin sağ üst köşesinde görüntülenir. Geçerli belgede verilen arama dizesinin her oluşumunu anında vurgular. Arama denetimindeki **Sonrakini Bul** düğmesini veya **Öncekini Bul** düğmesini seçerek bir örnekten diğerine gidebilirsiniz.

![Visual Studio 'da bul ve Değiştir](media/find-and-replace-box.png)

**Bul** metin kutusunun yanındaki düğmeyi seçerek değiştirme seçeneklerine erişebilirsiniz. Tek seferde bir değiştirme yapmak için, **Değiştir** metin kutusunun yanındaki **Sonrakini Değiştir** düğmesini seçin. Tüm eşleşmeleri değiştirmek için **Tümünü Değiştir** düğmesini seçin.

Eşleşmelerin vurgu rengini değiştirmek için, **Araçlar** menüsünü seçin, **Seçenekler**' i seçin ve ardından **ortam**' ı seçin ve **yazı tipleri ve renkler**' i seçin. **Ayarları göster** listesinde, **metin düzenleyici**' yi seçin ve ardından **öğeleri görüntüle** listesinde, **vurgu bul (uzantı)** öğesini seçin.

### <a name="search-tool-windows"></a>Arama aracı pencereleri

**Düzenle** > **Bul ve Değiştir** ' i seçerek veya **CTRL + F**tuşlarına basarak kodda veya metin penceresinde bulunan **bul** denetimini kullanabilirsiniz.

**Bul** denetiminin bir sürümü de bazı araç pencereleri için de kullanılabilir. Örneğin, arama kutusuna metin girerek **araç kutusu** penceresindeki denetim listesini filtreleyebilirsiniz. İçeriklerini aramanıza izin veren diğer araç pencereleri **Çözüm Gezgini**, **özellikler** penceresi ve **Takım Gezgini**içerir.

## <a name="find-in-files-and-replace-in-files"></a>Dosyalarda bulma ve dosyalardaki değiştirme

- Birden çok dosyada bir dize *bulmak* için kısayol olarak **Ctrl**+**SHIFT**+**F** tuşlarına basın.
- Birden çok dosyada bir dizeyi *bulmak ve değiştirmek* için kısayol olarak **Ctrl**+**SHIFT**+**H** tuşlarına basın.

**Dosyalarınızda Bul/Değiştir** , **Bul ve Değiştir** denetimi gibi çalışarak, aramanız için bir kapsam tanımlayabilmeniz gerekir. Yalnızca düzenleyicideki geçerli açık dosyada arama yapabilir, ancak tüm açık belgeler, tüm çözüm, geçerli proje ve seçili klasör kümelerini de arayabilirsiniz. Dosya adı uzantısına göre de arama yapabilirsiniz. **Dosyalarda Bul/Değiştir** iletişim kutusuna erişmek Için, **Düzenle** menüsünde **Bul ve Değiştir** ' i seçin (veya **CTRL**+**SHIFT**+**F**' e basın).

![Visual Studio 'da dosyalarda bul](media/find-in-files-box.png)

### <a name="find-results"></a>Sonuçları bul

**Tümünü Bul**' u seçtiğinizde, bir **sonuçları bul** penceresi açılır ve aramanızın eşleşmeleri listelenir. Listede bir sonuç seçildiğinde ilişkili dosya görüntülenir ve eşleşme vurgulanır. Dosya zaten düzenlenmek üzere açık değilse, sekme alanının sağ tarafındaki bir önizleme sekmesinde açılır. **Bul denetimini,** **sonuçları bul** listesinde aramak için kullanabilirsiniz.

### <a name="create-custom-search-folder-sets"></a>Özel arama klasörü kümeleri oluşturma

Arama **yeri** kutusunun yanındaki arama **klasörlerini Seç** düğmesini ( **.** ..) seçerek bir arama kapsamı tanımlayabilirsiniz. **Arama klasörlerini Seç** iletişim kutusunda, aranacak bir klasör kümesi belirtebilir ve daha sonra yeniden kullanabilmeniz için belirtimi kaydedebilirsiniz.

> [!TIP]
> Uzak makinenin sürücüsünü yerel makinenize eşleştirdiyseniz, uzak makinede arama yapmak için klasörler belirtebilirsiniz.

### <a name="create-custom-component-sets"></a>Özel bileşen kümeleri oluşturma

Arama **yeri** kutusunun yanındaki **özel bileşen kümesini Düzenle** düğmesini seçerek, bileşen kümelerini arama kapsamınız olarak tanımlayabilirsiniz. Yüklü .NET veya COM bileşenlerini, çözümünüze dahil olan Visual Studio projelerini veya herhangi bir derlemeyi ya da tür kitaplığını ( *. dll*, *. tlb*, *. olb*, *. exe*veya *. ocx*) belirtebilirsiniz. Başvuruları aramak için **başvurularda ara** kutusunu seçin.

## <a name="multi-caret-selection"></a>Çoklu giriş işareti seçimi

> [!NOTE]
> Bu bölüm Windows üzerinde Visual Studio için geçerlidir. Mac için Visual Studio için bkz. [blok seçimi](/visualstudio/mac/block-selection).

**Visual Studio 2017 sürüm 15,8 ' de tanıtılan**

Aynı düzenlemeyi aynı anda iki veya daha fazla yerde yapmak için *Çoklu giriş işareti seçimini* kullanın. Örneğin, aynı metni ekleyebilir veya aynı anda birden fazla konumda varolan metni değiştirebilirsiniz.

Aşağıdaki ekran görüntüsünde, üç konumda `-0000` seçilidir; Kullanıcı **Sil**' i basarsa, üç seçim de silinir:

![Visual Studio 'da bir XML dosyasında çoklu giriş işareti seçimi](media/multi-caret-selection.png)

Birden çok Evcil hayvan seçmek için her zamanki gibi ilk metin seçimini tıklatın veya seçin, sonra da her bir ek konumda metin ' i tıklattığınızda veya seçerken **alt** tuşuna basın. Ayrıca, eşleşen metni ek seçimler olarak otomatik olarak ekleyebilir veya her satırda aynı şekilde düzenlenecek metin kutusunu seçebilirsiniz.

> [!TIP]
> Fare tıklaması için değiştirici tuşu olarak **alt** ' i seçtiyseniz **Araçlar** > **Seçenekler**' de tanıma git ' e tıklayın, çoklu şapka seçimi devre dışıdır.

### <a name="commands"></a>Komutlar

Çoklu giriş işareti seçim davranışları için aşağıdaki anahtarları ve eylemleri kullanın:

|Kısayol|Eylem|
|-|-|
|**Ctrl**+**alt** + tıklama|İkincil giriş işareti ekleme|
|**Ctrl**+**alt** + çift tıklama|İkincil sözcük seçimi ekleme|
|**Ctrl**+**alt** + + sürükle 'e tıklayın|İkincil bir seçim ekleyin|
|**Shıft**+**alt**+ **.**|Sonraki eşleşen metni seçim olarak ekle|
|**Ctrl**+**shıft**+**alt**+ **,**|Tüm eşleşen metni seçimler olarak ekle|
|**Shıft**+**alt**+ **,**|Son seçili oluşumu kaldır|
|**Ctrl**+**shıft**+**alt**+ **.**|Sonraki eşleşen oluşumu atla|
|**Alt** + tıklama|Kutu seçimi Ekle|
|**ESC** veya tıklama|Tüm Seçimleri Temizle|

Bazı komutlardan biri de **düzenleme** menüsünde, **birden çok sepetin**altında bulunur:

![Visual Studio 'da çoklu Evcil hayvan uçarak çıkış menüsü](media/edit-menu-multiple-carets.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 'da normal ifadeler kullanma](../ide/using-regular-expressions-in-visual-studio.md)
- [Visual Studio 'da kodu yeniden düzenleme](../ide/refactoring-in-visual-studio.md)
- [Seçimi engelle (Mac için Visual Studio)](/visualstudio/mac/block-selection)
