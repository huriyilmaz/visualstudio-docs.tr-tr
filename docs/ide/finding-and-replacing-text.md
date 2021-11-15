---
title: Metin bul ve Değiştir ve çok şapka seçimi
description: Bul ve Değiştir özelliği ve bir düzenin örneklerini bulmak ve değiştirmek için nasıl kullanılacağı hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/15/2021
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
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 5abfbcc906cd64e63bce545bb71167439dc69d9f
ms.sourcegitcommit: 215680b355cf613bfa125cf6b864c8bb5f2c71a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/15/2021
ms.locfileid: "132453221"
---
# <a name="find-and-replace-text"></a>Metin bulma ve değiştirme

[bul ve değiştir](#find-and-replace-control) (**ctrl** + **F** veya **ctrl** + **H**) veya [dosyalarda bul/değiştir '](#find-in-files-and-replace-in-files) i kullanarak Visual Studio düzenleyicisinde metin bulabilir ve değiştirebilirsiniz (**ctrl** + **shıft** +  veya **ctrl** + **shıft** + **H**). Ayrıca, *[Çoklu şapka seçimini](#multi-caret-selection)* kullanarak bir düzenin yalnızca *bazı* örneklerini bulabilir ve değiştirebilirsiniz.

> [!TIP]
> Değişkenler ve yöntemler gibi kod sembollerini yeniden adlandırıyorsanız, bul ve Değiştir ' i kullanmaya kıyasla yeniden *[düzenleme](../ide/reference/rename.md)* daha iyidir. Yeniden düzenleme akıllı ve anlamıştır, ancak bul ve Değiştir, tüm örneklerin yerini alır.

bul ve değiştir işlevleri, düzenleyicide, XAML tasarımcısı ve Windows Forms tasarımcı gibi tasarımcı pencereleri ve araç pencereleri gibi çeşitli metin tabanlı **pencereler için düzenleyicide** bulunur.

Aramaları geçerli belge, geçerli çözüm veya özel bir klasör kümesiyle kapsamını belirleyebilirsiniz. Ayrıca, çok dosya aramaları için bir dosya adı uzantıları kümesi de belirtebilirsiniz. .NET [normal ifadelerini](../ide/using-regular-expressions-in-visual-studio.md)kullanarak arama sözdizimini özelleştirin.

> [!TIP]
> [Bul/komut](../ide/find-command-box.md) kutusu, bir araç çubuğu denetimi olarak kullanılabilir, ancak varsayılan olarak görünmez. **Bul/komut** kutusunu göstermek için **standart** araç çubuğunda **Düğme Ekle veya Kaldır** ' ı seçin ve ardından **bul**' u seçin.

## <a name="find-and-replace-control"></a>Bul ve Değiştir denetimi

-  + Geçerli dosyada bir dize *bulmak* için kısayol olarak Ctrl **F** tuşlarına basın.
-  + Geçerli dosyadaki bir dizeyi *bulmak ve değiştirmek* için kısayol olarak Ctrl **H** tuşuna basın.

**Bul ve Değiştir** denetimi, kod Düzenleyicisi penceresinin sağ üst köşesinde görüntülenir. Geçerli belgede verilen arama dizesinin her oluşumunu anında vurgular. Arama denetimindeki **Sonrakini Bul** düğmesini veya **Öncekini Bul** düğmesini seçerek bir örnekten diğerine gidebilirsiniz.

![Visual Studio bul ve Değiştir](media/find-and-replace-box.png)

**Bul** metin kutusunun yanındaki düğmeyi seçerek değiştirme seçeneklerine erişebilirsiniz. Tek seferde bir değiştirme yapmak için, **Değiştir** metin kutusunun yanındaki **Sonrakini Değiştir** düğmesini seçin. Tüm eşleşmeleri değiştirmek için **Tümünü Değiştir** düğmesini seçin.

Eşleşmelerin vurgu rengini değiştirmek için, **Araçlar** menüsünü seçin, **Seçenekler**' i seçin ve ardından **ortam**' ı seçin ve **yazı tipleri ve renkler**' i seçin. **Ayarları göster** listesinde, **metin düzenleyici**' yi seçin ve ardından **öğeleri görüntüle** listesinde, **vurgu bul (uzantı)** öğesini seçin.

### <a name="search-tool-windows"></a>Arama aracı pencereleri

Bul ve Değiştir Windows ve **sonuçları bul** **pencereleri gibi bir** kod veya metin penceresinde **bul** denetimini, bul **Düzenle**  >  **'** yi seçerek veya **CTRL + F** tuşlarına basarak kullanabilirsiniz.

**Bul** denetiminin bir sürümü de bazı araç pencereleri için de kullanılabilir. Örneğin, arama kutusuna metin girerek **araç kutusu** penceresindeki denetim listesini filtreleyebilirsiniz. İçeriklerini aramanıza izin veren diğer araç pencereleri **Çözüm Gezgini**, **özellikler** penceresi ve **Takım Gezgini** içerir.

## <a name="find-in-files-and-replace-in-files"></a>Dosyalarda bulma ve dosyalardaki değiştirme

-  +  + Birden çok dosyada dize *bulmak* için CTRL SHIFT **F** kısayolunu kısayol olarak basın.
-  +  + Birden çok dosyada bir dizeyi *bulmak ve değiştirmek* için kısayol olarak CTRL SHIFT **H** tuşuna basın.

**Dosyalarınızda Bul/Değiştir** , **Bul ve Değiştir** denetimi gibi çalışarak, aramanız için bir kapsam tanımlayabilmeniz gerekir. Yalnızca düzenleyicideki geçerli açık dosyada arama yapabilir, ancak tüm açık belgeler, tüm çözüm, geçerli proje ve seçili klasör kümelerini de arayabilirsiniz. Dosya adı uzantısına göre de arama yapabilirsiniz. **Dosyalarda Bul/Değiştir** iletişim kutusuna erişmek için, **Düzenle** menüsünde **Bul ve Değiştir** ' i seçin (veya **CTRL** + **SHIFT** + **F** tuşlarına basın).

![Visual Studio dosyalarında bulma](media/find-in-files-box.png)

### <a name="find-results"></a>Sonuçları bul

**Tümünü Bul**' u seçtiğinizde, bir **sonuçları bul** penceresi açılır ve aramanızın eşleşmeleri listelenir. Listede bir sonuç seçildiğinde ilişkili dosya görüntülenir ve eşleşme vurgulanır. Dosya zaten düzenlenmek üzere açık değilse, sekme alanının sağ tarafındaki bir önizleme sekmesinde açılır. **Bul denetimini,** **sonuçları bul** listesinde aramak için kullanabilirsiniz.

### <a name="create-custom-search-folder-sets"></a>Özel arama klasörü kümeleri oluşturma

Arama **yeri** kutusunun yanındaki arama **klasörlerini Seç** düğmesini ( **.**..) seçerek bir arama kapsamı tanımlayabilirsiniz. **Arama klasörlerini Seç** iletişim kutusunda, aranacak bir klasör kümesi belirtebilir ve daha sonra yeniden kullanabilmeniz için belirtimi kaydedebilirsiniz.

> [!TIP]
> Uzak makinenin sürücüsünü yerel makinenize eşleştirdiyseniz, uzak makinede arama yapmak için klasörler belirtebilirsiniz.

### <a name="create-custom-component-sets"></a>Özel bileşen kümeleri oluşturma

Arama **yeri** kutusunun yanındaki **özel bileşen kümesini Düzenle** düğmesini seçerek, bileşen kümelerini arama kapsamınız olarak tanımlayabilirsiniz. yüklü .net veya COM bileşenlerini, çözümünüze dahil olan projeleri Visual Studio veya herhangi bir derlemeyi ya da tür kitaplığını (*.dll*, *. tlb*, *. olb*, *.exe* veya *. ocx*) belirtebilirsiniz. Başvuruları aramak için **başvurularda ara** kutusunu seçin.

## <a name="multi-caret-selection"></a>Çoklu giriş işareti seçimi

> [!NOTE]
> bu bölüm Windows Visual Studio için geçerlidir. Mac için Visual Studio için bkz. [blok seçimi](/visualstudio/mac/block-selection).

::: moniker range="vs-2017"

**Visual Studio 2017 sürüm 15,8 ' de kullanıma sunuldu**

::: moniker-end

Aynı düzenlemeyi aynı anda iki veya daha fazla yerde yapmak için *Çoklu giriş işareti seçimini* kullanın. Örneğin, aynı metni ekleyebilir veya aynı anda birden fazla konumda varolan metni değiştirebilirsiniz.

::: moniker range="vs-2022"

Visual Studio 2022 ' de, çoklu giriş işareti kopyalama ve yapıştırma deneyimini geliştirdik. Daha önce, birden çok satırı birden çok çizgiye yapıştırmak, her bir şapka durumunda tüm panonun yinelenmesiyle sonuçlandı. Şimdi, birden fazla satırı aynı sepetlere yapıştırmak her satırı ilgili bir giriş işaretine ekleyecektir.

Çoklu giriş işaretini kullanmak için, **alt** + **SHIFT** + **fare tıklaması** veya **alt** + **SHIFT** tuşuna basın + **.** ardından  +  + seçimleri genişletmek için CTRL SHIFT **ok tuşunu** kullanın. Sonra,  + metni birden çok seçimlerde kopyalamak için CTRL **C** tuşuna basın.  +  + Her satır için istediğiniz yere yapıştırmak üzere birden çok Evcil hayvan oluşturmak için alt Shift **fare tıklamasını** kullanın. Son olarak, **CTRL** + **V** tuşlarına basarak her satırı kendi giriş işaretine yapıştırın.

:::image type="content" source="media/vs-2022/multi-caret-copy-paste.gif" alt-text="Visual Studio içindeki çoklu giriş işareti seçim eyleminin animasyonu.":::

:::image-end:::

Ayrıca, **alt** + **Shift** + **yukarı ok tuşunu** (veya **aşağı ok tuşunu**) veya **alt** + **SHIFT tuşuna basarak** +  birden çok Evcil hayvan seçebilirsiniz. Daha önce bu hareketler bir kutu seçimi oluşturdu. Şimdi, bir kutu seçimi birden çok kutucuya dönüştürülüyor. Bu yöntem, tek tek evcil hayvan eklemek için kesin konumlara tıklamaktan daha kolay ve hızlıdır.

> [!TIP]
> **Alt** SHIFT ok tuşlarıyla bir kutu seçimi kullanmaya devam etmek isterseniz +  +  ve  +  + bir çoklu giriş işaretini genişlettiğinizde, alt SHIFT **fare sürükleme** ' a gidin, **Araçlar**  >  **Seçenekler**  >  **metin Düzenleyicisi**  >  **Gelişmiş** ' e gidin ve **kutu seçimini kullan**' ı seçin.

Çoklu şapka seçimine,  > **birden çok Evcil hayvan** 'yi Düzenle ' yi seçip istediğiniz eylemi seçerek de erişebilirsiniz.

:::image type="content" source="media/vs-2022/edit-menu-multiple-carets-find-replace.png" alt-text="Visual Studio 2022 ' deki çoklu evcil hayvan açılan menüsünün ekran görüntüsü.":::

::: moniker-end

::: moniker range="<=vs-2019"

Aşağıdaki ekran görüntüsünde, `-0000` üç konumda seçilidir; Kullanıcı **Sil**' i basarsa, üç seçim de silinir:

![Visual Studio bir XML dosyasında çoklu giriş işareti seçimi](media/multi-caret-selection.png)

Birden çok Evcil hayvan seçmek için her zamanki gibi ilk metin seçimini tıklatın veya seçin, sonra da her bir ek konumda metin ' i tıklattığınızda veya seçerken **alt** tuşuna basın. Ayrıca, eşleşen metni ek seçimler olarak otomatik olarak ekleyebilir veya her satırda aynı şekilde düzenlenecek metin kutusunu seçebilirsiniz.

> [!TIP]
> Fare tıklaması için değiştirici tuşu olarak **alt** öğesini seçtiyseniz **Araçlar** seçeneklerinde tanıma git ' e tıklayın  >  , çoklu şapka seçimi devre dışıdır.

### <a name="commands"></a>Komutlar

Çoklu giriş işareti seçim davranışları için aşağıdaki anahtarları ve eylemleri kullanın:

|Kısayol|Eylem|
|-|-|
|**CTRL** + **Alt** + tıklama|İkincil giriş işareti ekleme|
|**CTRL** + **Alt** + çift tıklama|İkincil sözcük seçimi ekleme|
|**CTRL** + **Alt** + tıklatıp + sürükleyin|İkincil bir seçim ekleyin|
|**SHIFT** + **Alt** + **.**|Sonraki eşleşen metni seçim olarak ekle|
|**SHIFT** + **Alt** + **;**|Tüm eşleşen metni seçimler olarak ekle|
|**SHIFT** + **Alt** + **,**|Son seçili oluşumu kaldır|
|**SHIFT** + **Alt**+**/**|Sonraki eşleşen oluşumu atla|
|**Alt** + tıklama|Kutu seçimi Ekle|
|**ESC** veya tıklama|Tüm Seçimleri Temizle|

Komutlardan bazıları Düzenle menüsünde, Birden **Çok** **Carets altında da kullanılabilir:**

:::image type="content" source="media/edit-menu-multiple-carets-find-replace.png" alt-text="Visual Studio'daki Birden Çok Carets açılır menüsünün ekran Visual Studio":::

::: moniker-end

## <a name="see-also"></a>Ayrıca bkz.

- [Normal ifadeleri Visual Studio](../ide/using-regular-expressions-in-visual-studio.md)
- [Kodda yeniden düzenleme Visual Studio](../ide/refactoring-in-visual-studio.md)
- [Seçimi engelle (Mac için Visual Studio)](/visualstudio/mac/block-selection)
