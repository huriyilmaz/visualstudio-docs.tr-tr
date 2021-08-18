---
title: Metin bulma ve değiştirme ve çoklu imtiyaz seçimi
description: Bul ve Değiştir özelliği hakkında bilgi edinmek ve bir desenin örneklerini bulmak ve değiştirmek için bu özelliği nasıl kullanabileceğiniz hakkında bilgi edinmek.
ms.custom: SEO-VS-2020
ms.date: 10/17/2020
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
ms.openlocfilehash: f12d801fc54088c79d22a3c69cd27206a8b667e8
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122048992"
---
# <a name="find-and-replace-text"></a>Metin bulma ve değiştirme

Bul ve Değiştir [(](#find-and-replace-control) Ctrl F veya Ctrl H ) Visual Studio veya Dosyalarda Bul/Değiştir (**Ctrl** Shift F veya +   +  [](#find-in-files-and-replace-in-files) **Ctrl** Shift H ) +  +   +  + tuşlarını kullanarak metin düzenleyicide metin bulabilir ve değiştirebilirsiniz. Ayrıca, çoklu imtiyaz *seçimini* kullanarak bir desenin yalnızca *[bazı örneklerini bulup değiştirebilirsiniz.](#multi-caret-selection)*

> [!TIP]
> Değişkenler ve yöntemler gibi kod simgelerini yeniden adı kullanıyorsanız, bul *[](../ide/reference/rename.md)* ve değiştir kullanmak yerine bunları yeniden düzenlemeniz daha iyi olur. Yeniden düzenleme akıllıdır ve kapsamı anlarken bul ve değiştir, tüm örneklerin yerini kör bir şekilde değiştirir.

Bul ve değiştir işlevi düzenleyicide, Sonuçları Bul pencereleri gibi diğer metin  tabanlı bazı pencerelerde, XAML tasarımcısı ve Windows Forms tasarımcısı gibi tasarımcı pencerelerinde ve araç pencerelerinde kullanılabilir.

Geçerli belge, geçerli çözüm veya özel bir klasör kümesi için kapsam aramaları kullanabilirsiniz. Çok dosyalı aramalar için bir dizi dosya adı uzantısı da belirtebilirsiniz. .NET normal ifadelerini kullanarak arama söz [dizimlerini özelleştirin.](../ide/using-regular-expressions-in-visual-studio.md)

> [!TIP]
> [Bul/Komut](../ide/find-command-box.md) kutusu bir araç çubuğu denetimi olarak kullanılabilir, ancak varsayılan olarak görünür değildir. **Bul/Komut kutusunu görüntülemek için** Standart araç çubuğunda Düğme Ekle veya **Kaldır'ı** **ve** ardından Bul'ı **seçin.**

## <a name="find-and-replace-control"></a>Bul ve Değiştir denetimi

- Geçerli **dosyada bir** dizeyi bulmak için kısayol olarak Ctrl + **F** tuşlarına basın. 
- Geçerli **dosyada bir** dizeyi bulup değiştirmek için kısayol olarak Ctrl + **H** tuşlarına basın. 

Kod **düzenleyicisi penceresinin** sağ üst köşesinde Bul ve Değiştir denetimi görüntülenir. Geçerli belgede verilen arama dizesinin her oluşumunu hemen vurgular. Arama denetiminde Sonrakini Bul düğmesini veya Öncekini **Bul** düğmesini seçerek bir **oluşumdan** diğerine gezinebilirsiniz.

![Içinde Bul ve Değiştir Visual Studio](media/find-and-replace-box.png)

Bul metin kutusunun yanındaki düğmeyi seçerek değiştirme **seçeneklerine** erişebilirsiniz. Bir kez değişiklik yapmak için Değiştir metin **kutusunun** yanındaki Sonrakini Değiştir **düğmesini** seçin. Tüm eşleşmeleri değiştirmek için, Tüm Eşleşmeleri **Değiştir düğmesini** seçin.

Eşleşmelerin vurgu rengini değiştirmek için  Araçlar menüsünü seçin, Seçenekler'i ve ardından Ortam'ı **ve** Yazı Tipleri ve **Renkler'i seçin.** Listenin Ayarlarını **göster'de** Metin **Düzenleyici'yi seçin** ve öğeleri **görüntüle** listesinde Vurgu Bul **(Uzantı) öğesini seçin.**

### <a name="search-tool-windows"></a>Arama aracı pencereleri

Bul ve **Değiştir'i** seçerek veya     >   **Ctrl+F** tuşlarına basarak Kod veya metin pencerelerde Bul denetimi kullanabilirsiniz( Çıkış pencereleri ve Sonuçları Bul pencereleri gibi).

Bul denetimi **sürümü** bazı araç pencerelerde de kullanılabilir. Örneğin, araç kutusu penceresindeki denetim listesini **arama kutusuna** metin girerek filtre edebilirsiniz. İçeriklerinde aramanızı sağlayan diğer araç pencereleri **Çözüm Gezgini,** **Özellikler penceresi** ve **Takım Gezgini.**

## <a name="find-in-files-and-replace-in-files"></a>Dosyalarda Bulma ve Dosyalarda Değiştirme

- Birden **çok dosyada** bir dizeyi bulmak için kısayol olarak Ctrl + **Shift** + **F**  tuşlarına basın.
- Birden **çok dosyada** bir dizeyi bulup değiştirmek için kısayol olarak Ctrl + **Shift** + **H**  tuşlarına basın.

**Dosyalarda Bul/Değiştir,** **Bul ve Değiştir** denetimi gibi çalışır ancak aramanız için bir kapsam tanımlayabilirsiniz. Düzenleyicide geçerli açık dosyayı aramakla birlikte tüm açık belgeleri, çözümün tamamını, geçerli projeyi ve seçili klasör kümelerini de arayabilirsiniz. Dosya adı uzantısına göre de arama yapabilirsiniz. Dosyalarda **Bul/Değiştir iletişim kutusuna erişmek için** Düzenle  menüsünde Bul ve Değiştir'i seçin (veya Ctrl Shift F   +  + **tuşlarına basın).**

![Dosyalarda Bul Visual Studio](media/find-in-files-box.png)

### <a name="find-results"></a>Sonuçları Bulma

Hepsini **Bul'ı** seçtiğiniz **zaman Sonuçları Bul** penceresi açılır ve aramanıza uygun eşleşmeleri listeler. Listede bir sonuç seçerek ilişkili dosya görüntülenir ve eşleşme vurgulanır. Dosya düzenleme için açık durumda değilse, sekmenin sağ tarafındaki önizleme sekmesinde açılır. Sonuçları Bul listesinde **arama** yapmak için Bul denetimi **kullanabilirsiniz.**

### <a name="create-custom-search-folder-sets"></a>Özel arama klasörü kümeleri oluşturma

Arama klasörünün yanındaki Arama **Klasörlerini** Seç düğmesini (şuna **benzer... gibi** görünür) seçerek bir arama kapsamı **tanımlayabilirsiniz.** Arama **Klasörleri Seç iletişim** kutusunda, aranecek bir klasör kümesi belirtebilirsiniz ve daha sonra yeniden kullanmak üzere belirtimi kaydedebilirsiniz.

> [!TIP]
> Bir uzak makinenin sürücüsüne yerel makinenize eşle yaptıysanız, uzak makinede arama yapmak için klasörler belirtebilirsiniz.

### <a name="create-custom-component-sets"></a>Özel bileşen kümeleri oluşturma

Görünüm kutusunun yanındaki Özel Bileşen Kümesi Düzenle düğmesini seçerek bileşen **kümelerini** arama kapsamınız **olarak tanımlayabilirsiniz.** Yüklü .NET veya COM bileşenlerini, Visual Studio projelerini veya herhangi bir derleme ya da tür kitaplığını (*.dll*, *.tlb*, *.olb*,.exeveya *.ocx) belirtebilirsiniz.* ** Başvurularda arama yapmak için **Başvurularda ara kutusunu** seçin.

## <a name="multi-caret-selection"></a>Çoklu imtiyaz seçimi

> [!NOTE]
> Bu bölüm, Visual Studio için Windows. Daha Mac için Visual Studio için [bkz. Seçimi engelleme.](/visualstudio/mac/block-selection)

**Visual Studio 2017 sürüm 15.8'de tanıtıldı**

Aynı *anda iki veya daha* fazla yerde aynı düzenlemeyi yapmak için çoklu imtiyazlı seçimi kullanın. Örneğin, aynı metni eklemek veya birden çok konumdaki mevcut metni aynı anda değiştirmek için kullanabilirsiniz.

Aşağıdaki ekran görüntüsünde, üç konumda seçilidir; kullanıcı Sil'e `-0000` **basıyorsa,** üç seçimin de silinir:

![Visual Studio'de bir XML dosyasında çoklu Visual Studio](media/multi-caret-selection.png)

Birden çok giriş imli seçmek için, her zamanki gibi ilk metin seçimine tıklayın veya yapın ve ardından ek konumlarda yer alan metinlere tıklar veya metinleri seçerken **Alt** tuşuna basın. Ayrıca, eşleşen metni otomatik olarak ek seçim olarak ekleyebilir veya her satırda aynı şekilde düzenlemek için bir metin kutusu seçin.

> [!TIP]
> Değiştirici anahtarı olarak **Alt'ı** seçtiysanız, Araçlar Seçenekler'de Tanıma Git'e tıklarsanız   >  çoklu girişli seçim devre dışı bırakılır.

### <a name="commands"></a>Komutlar

Çok satırlı seçim davranışları için aşağıdaki anahtarları ve eylemleri kullanın:

|Kısayol|Eylem|
|-|-|
|**Ctrl tuşunu basılı tutarak** + **Alt** + tıklama|İkincil bir caret ekleme|
|**Ctrl tuşunu basılı tutarak** + **Alt** + çift tıklama|İkincil sözcük seçimi ekleme|
|**Ctrl tuşunu basılı tutarak** + **Alt** + tıklama + sürükleme|İkincil seçim ekleme|
|**Shift ile kaydırma** + **Alt** + **.**|Sonraki eşleşen metni seçim olarak ekleme|
|**Shift ile kaydırma** + **Alt** + **;**|Eşleşen tüm metni seçim olarak ekleme|
|**Shift ile kaydırma** + **Alt** + **,**|Son seçilen oluşum kaldırma|
|**Shift ile kaydırma** + **Alt**+**/**|Sonraki eşleştirme oluşumunu atla|
|**Alt** + tıklama|Kutu seçimi ekleme|
|**Esc tuşuna** basın veya tıklayın|Tüm seçimleri temizle|

Komutlardan bazıları Düzenle menüsünde, Birden **Çok** **Carets altında da kullanılabilir:**

:::image type="content" source="media/edit-menu-multiple-carets-find-replace.png" alt-text="Visual Studio'daki Birden Çok Carets açılır menüsünün ekran Visual Studio":::

## <a name="see-also"></a>Ayrıca bkz.

- [Normal ifadeleri Visual Studio](../ide/using-regular-expressions-in-visual-studio.md)
- [Kodda yeniden düzenleme Visual Studio](../ide/refactoring-in-visual-studio.md)
- [Seçimi engelle (Mac için Visual Studio)](/visualstudio/mac/block-selection)
