---
title: Metin bulma ve değiştirme ve çoklu imtiyaz seçimi
description: Bul ve Değiştir özelliği hakkında bilgi edinmek ve bir desenin örneklerini bulmak ve değiştirmek için bu özelliği nasıl kullanabileceğiniz hakkında bilgi edinmek.
ms.custom: SEO-VS-2020
ms.date: 02/01/2022
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
ms.openlocfilehash: 60a97bb589ce05ba95f1af4b2b92fc90dd1e9877
ms.sourcegitcommit: 3766c051f9a8b35106b16f751db7fecde0b92254
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/02/2022
ms.locfileid: "137951708"
---
# <a name="find-and-replace-text"></a>Metin bulma ve değiştirme

Bul ve [Değiştir (](#find-and-replace-control)**CtrlF veya CtrlH**) veya Dosyalarda Bul [/](#find-in-files-and-replace-in-files)+Değiştir (**CtrlShiftF**+ veya **CtrlShiftH**+++) kullanarak metinleri Visual Studio düzenleyicisinde bulabilir ve **değiştirebilirsiniz**+. Ayrıca çok satırlı seçim kullanarak *bir* desenin yalnızca bazı örneklerini *[bulup değiştirebilirsiniz](#multi-caret-selection)*.

> [!TIP]
> Değişkenler ve yöntemler gibi kod simgelerini yeniden adı kullanıyorsanız, bul ve değiştir kullanmak yerine bunları yeniden düzenlemeniz daha *[](../ide/reference/rename.md)* iyi olur. Yeniden düzenleme akıllıdır ve kapsamı anlarken bul ve değiştir, tüm örneklerin yerini kör bir şekilde değiştirir.

Bul ve değiştir işlevi düzenleyicide, Sonuçları Bul pencereleri gibi diğer metin tabanlı bazı pencerelerde, XAML tasarımcısı ve  Windows Forms tasarımcısı gibi tasarımcı pencerelerinde ve araç pencerelerinde kullanılabilir.

Geçerli belge, geçerli çözüm veya özel bir klasör kümesi için kapsam aramaları kullanabilirsiniz. Çok dosyalı aramalar için bir dizi dosya adı uzantısı da belirtebilirsiniz. .NET normal ifadelerini kullanarak arama söz [dizimlerini özelleştirin](../ide/using-regular-expressions-in-visual-studio.md).

> [!TIP]
> Bul [/Komut](../ide/find-command-box.md) kutusu bir araç çubuğu denetimi olarak kullanılabilir, ancak varsayılan olarak görünür değildir. Bul **/Komut kutusunu görüntülemek için** Standart araç çubuğunda **Düğme Ekle veya Kaldır'ı** **ve** ardından Bul'ı **seçin**.

## <a name="find-and-replace-control"></a>Bul ve Değiştir denetimi

- Geçerli **dosyada** bir dizeyi bulmak için *kısayol olarak* **CtrlF**+ tuşlarına basın.
- Geçerli **dosyada bir** dizeyi bulup değiştirmek *için kısayol olarak* **CtrlH**+ tuşlarına basın.

Kod **düzenleyicisi penceresinin** sağ üst köşesinde Bul ve Değiştir denetimi görüntülenir. Geçerli belgede verilen arama dizesinin her oluşumunu hemen vurgular. Arama denetiminde Sonrakini Bul düğmesini veya Öncekini **Bul düğmesini** seçerek bir **oluşumdan** diğerine gezinebilirsiniz.

::: moniker range="vs-2022"

:::image type="content" source="media/vs-2022/find-and-replace-box.png" alt-text="Visual Studio 2022'de Düzenleyici'de Bul ve Değiştir iletişim kutusunun ekran görüntüsü.":::

::: moniker-end

::: moniker range="<=vs-2019"

:::image type="content" source="media/find-and-replace-box.png" alt-text="Visual Studio 2019 ve önceki sürümlerde Düzenleyici'de Bul ve Değiştir iletişim kutusunun ekran görüntüsü.":::

::: moniker-end

Bul metin kutusunun yanındaki düğmeyi seçerek değiştirme **seçeneklerine** erişebilirsiniz. Bir kez değişiklik yapmak için Değiştir metin **kutusunun** yanındaki Sonrakini Değiştir **düğmesini** seçin. Tüm eşleşmeleri değiştirmek için, Tüm Eşleşmeleri **Değiştir düğmesini** seçin.

Eşleşmelerin vurgu rengini değiştirmek için Araçlar menüsünü seçin, Seçenekler'i ve ardından Ortam'ı ve Yazı Tipleri ve **Renkler'i seçin**. Listenin Ayarlarını **göster'de** Metin **Düzenleyici'yi seçin** ve ardından Öğeleri **görüntüle listesinde** Eşleşme Vurgusu **Bul'a tıklayın**.

### <a name="search-tool-windows"></a>Arama aracı pencereleri

  DüzenleFind ve **Değiştir'i** >  seçerek veya **Ctrl+F** tuşlarına basarak Kod veya metin pencerelerde Bul denetimi kullanabilirsiniz.

Bul **denetimi sürümü bazı** araç pencerelerde de kullanılabilir. Örneğin, araç kutusu penceresindeki denetim listesini **arama kutusuna** metin girerek filtre edebilirsiniz. İçeriklerinde aramanızı sağlayan diğer araç pencereleri **Çözüm Gezgini,** **Özellikler** penceresi ve **Takım Gezgini.**

## <a name="find-in-files-and-replace-in-files"></a>Dosyalarda Bulma ve Dosyalarda Değiştirme

- Birden **çok dosyada** **bir dizeyi** bulmak için kısayol *olarak* **CtrlShiftF**++ tuşlarına basın.
- Birden **çok dosyada** bir dizeyi bulup değiştirmek *için kısayol olarak* **CtrlShiftH**++ tuşlarına basın.

**Dosyalarda Bul/Değiştir** , **Bul ve Değiştir** denetimi gibi çalışır ancak aramanız için bir kapsam tanımlayabilirsiniz. Düzenleyicide geçerli açık dosyayı aramakla birlikte tüm açık belgeleri, çözümün tamamını, geçerli projeyi ve seçili klasör kümelerini de arayabilirsiniz. Dosya adı uzantısına göre de arama yapabilirsiniz. Dosyalarda Bul **/Değiştir iletişim kutusuna erişmek için** Düzenle menüsünde Bul  ve Değiştir'i seçin  (veya **CtrlShiftF tuşlarına**++ **basın**).

::: moniker range=">=vs-2022"

:::image type="content" source="media/vs-2022/find-files.png" alt-text="20222'de Dosyalarda Bul sekmesi açık Visual Studio Bul ve Değiştir iletişim kutusunun ekran görüntüsü.":::

Daha ayrıntılı bilgi için Dosyalarda [Bul ve Dosyalarda](find-in-files.md) [Değiştir sayfalarına](replace-in-files.md) bakın.

::: moniker-end

::: moniker range="vs-2019"

:::image type="content" source="media/find-files-vs2019.png" alt-text="Visual Studio 2019'da Dosyalarda Bul sekmesinin açık olduğu Bul ve Değiştir iletişim kutusunun ekran görüntüsü.":::

Daha ayrıntılı bilgi için Dosyalarda [Bul ve Dosyalarda](find-in-files.md) [Değiştir sayfalarına](replace-in-files.md) bakın.

> [!IMPORTANT]
> **Visual Studio 2019** sürüm [**16.6**](/visualstudio/releases/2019/release-notes-v16.6/) veya önceki bir sürümü kullanıyorsanız, Bul ve Değiştir iletişim kutusu burada göründüğü  gibi görünmüyor olabilir. Bu sayfanın [Visual Studio 2017](?view=vs-2017&preserve-view=true) sürümüne geçiş yapmak için ekranda gördüğünüz açıklamalara bakın.

::: moniker-end

::: moniker range="vs-2017"

:::image type="content" source="media/find-files-vs2017.png" alt-text="2017'de Dosyalarda Bul sekmesi açık Visual Studio Bul ve Değiştir iletişim kutusunun ekran görüntüsü.":::

Daha ayrıntılı bilgi için Dosyalarda [Bul ve Dosyalarda](find-in-files.md) [Değiştir sayfalarına](replace-in-files.md) bakın.

::: moniker-end

### <a name="find-results"></a>Sonuçları Bulma

Hepsini **Bul'ı** seçtiğiniz **zaman sonuçları bul** penceresi açılır ve aramanız için eşleşmeler liste olur. Listede bir sonuç seçerek ilişkili dosya görüntülenir ve eşleşme vurgulanır. Dosya düzenleme için açık durumda değilse, sekmenin sağ tarafındaki önizleme sekmesinde açılır. Sonuçları Bul listesinde **arama** yapmak için Bul denetimi **kullanabilirsiniz** .

### <a name="create-custom-search-folder-sets"></a>Özel arama klasörü kümeleri oluşturma

Arama klasörünün yanındaki Arama **Klasörlerini Seç** düğmesini (şuna benzer **...**) seçerek bir arama **kapsamı tanımlayabilirsiniz** . Arama **Klasörleri Seç iletişim** kutusunda, aranecek bir klasör kümesi belirtebilirsiniz ve daha sonra yeniden kullanmak üzere belirtimi kaydedebilirsiniz.

> [!TIP]
> Bir uzak makinenin sürücüsüne yerel makinenize eşle yaptıysanız, uzak makinede arama yapmak için klasörler belirtebilirsiniz.

### <a name="create-custom-component-sets"></a>Özel bileşen kümeleri oluşturma

Görünüm kutusunun yanındaki Özel Bileşen Kümesi Düzenle düğmesini seçerek bileşen **kümelerini** arama kapsamınız **olarak tanımlayabilirsiniz** . Yüklü .NET veya COM bileşenlerini, Visual Studio projelerini veya herhangi bir derleme veya tür kitaplığını (*.dll*, *.tlb*, *.olb*, *.exe* veya *.ocx) belirtebilirsiniz*. Başvurularda arama yapmak için **Başvurularda ara kutusunu** seçin.

## <a name="multi-caret-selection"></a>Çoklu imtiyaz seçimi

> [!NOTE]
> Bu bölüm, Visual Studio Windows. Daha Mac için Visual Studio için bkz[. Seçimi engelleme](/visualstudio/mac/block-selection).

::: moniker range="vs-2017"

**Visual Studio 2017 sürüm 15.8'de tanıtıldı**

::: moniker-end

Aynı *anda iki veya daha* fazla yerde aynı düzenlemeyi yapmak için çoklu imtiyazlı seçimi kullanın. Örneğin, aynı metni eklemek veya birden çok konumdaki mevcut metni aynı anda değiştirmek için kullanabilirsiniz.

::: moniker range="vs-2022"

2022 Visual Studio de çoklu caret kopyalama ve yapıştırma deneyimini iyileştirildi. Daha önce, birden çok giriş imtiyazına birden çok satır yapıştırarak panodaki tüm giriş imtiyazları çoğaltıldı. Şimdi, birden çok satırı aynı sayıda caret içine yapıştırarak her satırı ilgili caret'e ekler.

Çoklu giriş düğmesini kullanmak için **AltShiftmouse**++ tıklama **veya** **AltShift tuşlarına**+ **basın**+**.** ve ardından **seçimleri genişletmek için** **CtrlShiftarrow**++ tuşunu kullanın. Ardından **CtrlC tuşlarına**+ basarak metni birden çok seçimde kopyalayın. +**AltShiftmouse**+ **tıklamayı** kullanarak her satır için istediğiniz yere yapıştırmak üzere birden çok giriş çizgisi oluşturun. Son olarak **CtrlV tuşlarına**+ basarak her satırı kendi caret'ine yapıştırın.

:::image type="content" source="media/vs-2022/multi-caret-copy-paste.gif" alt-text="Birden çok satırlı seçim eyleminin bir animasyonu Visual Studio.":::

Ayrıca, birden çok tuş takımıyla seçmek **için** **AltShiftup**++ ok tuşunu (veya aşağı ok **tuşunu) veya** **AltShiftmouse**++ sürüklemeyi kullanabilirsiniz. Daha önce bu hareketler bir kutu seçimi oluşturdu. Artık bir kutu seçimi birden çok işarete dönüşür. Bu yöntem, tek tek giriş girişlerini eklemek için kesin konumlara tıklamak zorunda kalmadan daha kolaydır ve daha hızlıdır.

> [!TIP]
> **AltShiftarrow** anahtarları ile bir kutu seçimini kullanmaya devam etmek isterseniz ve çok noktalı bir seçimi genişlettikçe **AltShiftmouse**++++ sürükleme seçeneğine gidin, **AraçlarSeçeneklerMetin** >  >  **DüzenleyicisiÖzlemli'ye** >  gidin ve Kutu seçimini kullan'ı **seçin**.

### <a name="commands"></a>Komutlar

Aşağıdaki klavye kısayolları, çok satırlı seçim davranışlarına özgü eylemlere yöneliktir.

|Kısayol|Eylem|Komut|
|-|-|-|
| **Alt**+ **Üstkrkt**+ **.** | Çoklu imtiyaz kullanma | Edit.InsertNextMatchingCaret |
| **Ctrl**+ **Üstkrkt**+ **ok tuşu** | Seçimleri genişletme | Edit.SizeControlUp, Edit.SizeControlDown, Edit.SizeControlRight, Edit.SizeControlLeft |
| **Alt**+ **Üstkrkt**+ **yukarı ok tuşu** (veya **aşağı ok tuşu**)| Birden çok caret seçin | Edit.LineUpExtendColumn, Edit.LineDownExtendColumn |

Menü çubuğunda Birden Çok Giriş Çubuğunu Düzenle'yi  > ve ardından istediğiniz eylemi seçerek çoklu giriş imtiyazlı seçime de erişebilirsiniz.

:::image type="content" source="media/vs-2022/edit-menu-multiple-carets-find-replace.png" alt-text="Visual Studio 2022'de Çoklu Visual Studio açılır menüsünün ekran görüntüsü.":::

::: moniker-end

::: moniker range="<=vs-2019"

Aşağıdaki ekran görüntüsünde, `-0000` üç konumda seçilidir; kullanıcı Sil'e **basıyorsa**, üç seçimin de silinir:

![Visual Studio'de bir XML dosyasında çoklu Visual Studio](media/multi-caret-selection.png)

Birden çok giriş imtiyazı seçmek için, her zamanki gibi ilk metin seçimine tıklayın veya yapın ve ardından her ek konumdaki metne tıklar veya metin seçerken **CtrlAlt** + tuşlarına basın. Ayrıca, eşleşen metni otomatik olarak ek seçim olarak ekleyebilir veya her satırda aynı şekilde düzenlemek için bir metin kutusu seçin.

> [!TIP]
> AraçlarSeteneklerMetin >  **DüzenleyicisiGenel'den** "Tanıma Git"  >  >  içinde fare tıklaması için değiştirici anahtar olarak **Alt'ı** seçtiyebilirsiniz, çoklu giriş işareti seçimi devre dışıdır. Daha fazla bilgi için bkz [. Seçenekler iletişim kutusu: Metin Düzenleyici /> Genel](reference/options-text-editor-general.md).

### <a name="commands"></a>Komutlar

Çok satırlı seçim davranışları için aşağıdaki anahtarları ve eylemleri kullanın:

|Kısayol|Eylem|
|-|-|
|**Ctrl**+ **Alt** + tıklama|İkincil bir caret ekleme|
|**Ctrl**+ **Alt** + çift tıklama|İkincil sözcük seçimi ekleme|
|**Ctrl**+ **Alt** + tıklama + sürükleme|İkincil seçim ekleme|
|**Üstkrkt**+ **Alt**+ **.**|Sonraki eşleşen metni seçim olarak ekleme|
|**Üstkrkt**+ **Alt**+ **;**|Eşleşen tüm metni seçim olarak ekleme|
|**Üstkrkt**+ **Alt**+ **,**|Son seçilen oluşum kaldırma|
|**Üstkrkt**+ **Alt**+**/**|Sonraki eşleştirme oluşumunu atla|
|**Alt** + tıklama|Kutu seçimi ekleme|
|**Esc tuşuna** basın veya tıklayın|Tüm seçimleri temizle|

Komutlardan bazıları Düzenle menüsünde, Birden **Çok** **Carets altında da kullanılabilir**:

:::image type="content" source="media/edit-menu-multiple-carets-find-replace.png" alt-text="Visual Studio'daki Birden Çok Carets açılır menüsünün ekran Visual Studio":::

::: moniker-end

## <a name="see-also"></a>Ayrıca bkz.

- [Normal ifadeleri Visual Studio](../ide/using-regular-expressions-in-visual-studio.md)
- [Kodda yeniden düzenleme Visual Studio](../ide/refactoring-in-visual-studio.md)
- [Seçimi engelle (Mac için Visual Studio)](/visualstudio/mac/block-selection)
