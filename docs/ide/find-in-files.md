---
title: Dosyalarda Bul
description: Dosyalarda Bul özelliğini ve bu özelliği kullanarak belirli bir dosya kümesinde arama yapmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/29/2021
ms.topic: conceptual
f1_keywords:
- vs.findinfiles
helpviewer_keywords:
- objects [Visual Studio], finding
- text searches, replacing text
- objects [Visual Studio], searching for
- Find and Replace window, Find in Files tab
- text searches, Find and Replace window
- documents, searching
- files, searching
- Find in Files tab, Find and Replace window
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 41902f7e629864d355d0aa7067e82eeace9a3736
ms.sourcegitcommit: 965372ad0d75f015403c1af508080bf799914ce3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "135804746"
---
# <a name="find-in-files"></a>Dosyalarda Bul

**Dosyalarda Bul,** belirli bir dosya kümesinde aramanızı sağlar. Bulan Visual Studio eşleşmeler **IDE'nin** Sonuçları Bul penceresinde listelenir. Sonuçların nasıl görünmesi, Bul ve Değiştir iletişim kutusunun **Dosyalarda** Bul sekmesinde **seçtiğiniz seçeneklere** bağlıdır.

::: moniker range=">=vs-2022"

:::image type="content" source="media/vs-2022/find-files.png" alt-text="20222'de Dosyalarda Bul sekmesi açık Visual Studio Bul ve Değiştir iletişim kutusunun ekran görüntüsü.":::

::: moniker-end

::: moniker range="vs-2019"

:::image type="content" source="media/find-files-vs2019.png" alt-text="Visual Studio 2019'da Dosyalarda Bul sekmesinin açık olduğu Bul ve Değiştir iletişim kutusunun ekran görüntüsü.":::

> [!IMPORTANT]
> **Visual Studio 2019** sürüm [**16.6**](/visualstudio/releases/2019/release-notes-v16.6/) veya önceki bir sürümü  kullanıyorsanız, Bul ve Değiştir iletişim kutusu burada göründüğü gibi görünmüyor olabilir. Bu sayfanın [Visual Studio 2017](find-in-files.md?view=vs-2017&preserve-view=true) sürümüne geçiş yapmak için ekranda gördüğünüz açıklamalara bakın.

::: moniker-end

::: moniker range="vs-2017"

:::image type="content" source="media/find-files-vs2017.png" alt-text="Visual Studio 2017'de Dosyalarda Bul sekmesinin açık olduğu Bul ve Değiştir iletişim kutusunun ekran görüntüsü.":::

::: moniker-end

## <a name="how-to-display-find-in-files"></a>Dosyalarda Bul'ı görüntüleme

Bul ve Değiştir iletişim kutusunu açmak **için aşağıdaki** adımları kullanın veya Ctrl Shift F  + **tuşlarına** + **basın.**

:::moniker range="<=vs-2019"

1. **Ctrl** + **Q tuşlarına** basın ve ekranın üst kısmında yer alan arama kutusuna "bul" yazın.

1. Sonuçlar **listesinden Dosyalarda** bul'ı seçin.

veya
:::moniker-end

1. Menü çubuğunda Bul ve **Değiştir'i**  >  **seçin.**

1. Açılır **menüden Dosyalarda** Bul'a tıklayın.

Bul işlemini iptal etmek için **Ctrl** Break tuşlarına + **basın.**

> [!NOTE]
> Bul **ve Değiştir** aracı, veya özniteliğine sahip dizinlerde arama `Hidden` `System` yapar.

::: moniker range="vs-2017"

## <a name="find-what"></a>Neyi bul

Yeni bir metin dizesi veya ifade aramak için, Bunu Bul **kutusunda** belirtin.

::: moniker-end

::: moniker range=">=vs-2022"

## <a name="search-box"></a>Arama kutusu

Yeni bir metin dizesini veya ifadeyi aramak için Arama kutusunda belirtin. En son aramak istediğiniz 20 dizeden herhangi birini aramak için açılan listeyi açın ve dizeyi seçin.

Aşağıdaki seçenekleri kullanabilir veya temizebilirsiniz:

- **Eşleşme durumu** - Aramanızı büyük/büyük/büyük harfe duyarlı olduğundan emin olmak için bu seçeneği kullanın.
- **Tam sözcüğü eşle** - Aramanızı yalnızca tam sözcük eşleşmeleri döndürecek şekilde emin olmak için bu seçeneği kullanın.
- **Normal ifadeler kullan** - Bu seçeneği, Arama kutusunda (veya Değiştir metin kutusunda) eşleşmeye yönelik metin desenlerini tanımlayan özel ifadeler **kullanmak** için kullanın. Bu ifadelerin listesi için [bkz. Visual Studio'de normal ifadeler kullanma.](../ide/using-regular-expressions-in-visual-studio.md)

    > [!Important]
    > İfade **Oluşturucusu** düğmesi, Arama kutusunun yanında yalnızca Normal ifadeler kullan **onay kutusunu seçtiyebilirsiniz.**
    >
    > :::image type="content" source="media/vs-2022/find-files-expression-builder.png" alt-text="İfade Oluşturucusu düğmesinin ve Normal İfadeleri Kullan onay kutusunun çevresindeki ve ana hatlarını içeren Dosyalarda Bul iletişim kutusunun ekran görüntüsü.":::

## <a name="look-in"></a>Şuna bakın:

Görünüm açılan listesinden  seçtiğiniz seçenek, Dosyalarda  Bul seçeneğinin çalışma alanının tamamına, çözümün tamamına, geçerli projeye, geçerli dizine, tüm açık belgelere veya geçerli belgeye bakıp arama olmadığını belirler.

Aramak istediğiniz yeri bulmak için **bitişik Gözat (...)** düğmesini de kullanabilirsiniz. Daha da iyisi, zaten bir dizin belirttiyseniz, bu düğme dizini değiştirmek yerine yeni dizini ekler. Örneğin, "Look in" değeriniz ".\Code" ise Gözat **(...)** düğmesine tıklayabilirsiniz ve "Paylaşılan Kod" adlı bir klasöre gitebilirsiniz. Gözat **(...) kutusunda** artık ".\Code;. \Shared Code" (Paylaşılan Kod) ve Find komutu yürütülürken bu klasörlerin her ikisi de aranacak.

Aramanızı geliştirmek için aşağıdaki seçenekleri kullanabilir veya temizebilirsiniz:

- **Dış öğeleri dahil** etme - Başvurabilirsiniz ancak çözümün parçası olmayan "windows.h" gibi dosyalar gibi dış öğeleri dahil etmek için bu seçeneği kullanın.
- **Çeşitli dosyaları dahil etme** - Bu seçeneği, açtığım ancak çözümün parçası olmayan dosyalar gibi çeşitli dosyaları dahil etmek için kullanın.

## <a name="file-types"></a>Dosya türleri

Dosya **türleri seçeneği,** Dizinlerde ara içinde aranan **dosya türlerini** gösterir. Bu belirli türlerde dosyaları bulacak önceden yapılandırılmış bir arama dizesi girmek için listeden herhangi bir öğeyi seçin.

:::image type="content" source="media/vs-2022/find-file-types.png" alt-text="Dosyalarda Bul iletişim kutusunun Dosya Türleri bölümünün ekran görüntüsü.":::

Bunları noktalı virgül () ile ayırarak birden çok dosya türü `;` arayabilirsiniz. Ayrıca, herhangi bir yola veya dosya türüne ünlem işareti () ön eki eklerini kullanarak klasörleri ve dosyaları hariç `!` tutabilirsiniz.

### <a name="append-results"></a>Sonuçları ekleme

Geçerli aramanın sonuçlarını önceki arama sonuçlarına eklemek için bu seçeneği kullanın.

::: moniker-end

::: moniker range="vs-2019"

## <a name="search-box"></a>Arama kutusu

Yeni bir metin dizesini veya ifadeyi aramak için Arama kutusunda belirtin. En son aramak istediğiniz 20 dizeden herhangi birini aramak için açılan listeyi açın ve dizeyi seçin.

Aşağıdaki seçenekleri kullanabilir veya temizebilirsiniz:

- **Eşleşme durumu** - Aramanızı büyük/büyük/büyük harfe duyarlı olduğundan emin olmak için bu seçeneği kullanın.
- **Tam sözcüğü eşle** - Aramanızı yalnızca tam sözcük eşleşmeleri döndürecek şekilde emin olmak için bu seçeneği kullanın.
- **Normal ifadeler kullan** - Bu seçeneği, Arama kutusunda (veya Değiştir metin kutusunda) eşleşmeye yönelik metin desenlerini tanımlayan özel ifadeler **kullanmak** için kullanın. Bu ifadelerin listesi için [bkz. Visual Studio'de normal ifadeler kullanma.](../ide/using-regular-expressions-in-visual-studio.md)

    > [!Important]
    > İfade **Oluşturucusu** düğmesi, Arama kutusunun yanında yalnızca Normal ifadeler kullan **onay kutusunu seçtiyebilirsiniz.**
    >
    > :::image type="content" source="media/find-files-expression-builder-vs-2019.png" alt-text="İfade Oluşturucusu düğmesinin ve Normal İfadeleri Kullan onay kutusunun çevresindeki ve ana hatlarını içeren Dosyalarda Bul iletişim kutusunun ekran görüntüsü.":::

## <a name="look-in"></a>Şuna bakın:

Görünüm açılan listesinden  seçtiğiniz seçenek, Dosyalarda  Bul seçeneğinin çalışma alanının tamamına, çözümün tamamına, geçerli projeye, geçerli dizine, tüm açık belgelere veya geçerli belgeye bakıp arama olmadığını belirler.

Aramak istediğiniz yeri bulmak için **bitişik Gözat (...)** düğmesini de kullanabilirsiniz. Daha da iyisi, zaten bir dizin belirttiyseniz, bu düğme dizini değiştirmek yerine yeni dizini ekler. Örneğin, "Look in" değeriniz ".\Code" ise Gözat **(...)** düğmesine tıklayabilirsiniz ve "Paylaşılan Kod" adlı bir klasöre gitebilirsiniz. Gözat **(...) kutusunda** artık ".\Code;. \Shared Code" (Paylaşılan Kod) ve Find komutu yürütülürken bu klasörlerin her ikisi de aranacak.

Aramanızı geliştirmek için aşağıdaki seçenekleri kullanabilir veya temizebilirsiniz:

- **Dış öğeleri dahil** etme - Başvurabilirsiniz ancak çözümün parçası olmayan "windows.h" gibi dosyalar gibi dış öğeleri dahil etmek için bu seçeneği kullanın.
- **Çeşitli dosyaları dahil etme** - Bu seçeneği, açtığım ancak çözümün parçası olmayan dosyalar gibi çeşitli dosyaları dahil etmek için kullanın.

## <a name="file-types"></a>Dosya türleri

Dosya **türleri seçeneği,** Dizinlerde ara içinde aranan **dosya türlerini** gösterir. Bu belirli türlerde dosyaları bulacak önceden yapılandırılmış bir arama dizesi girmek için listeden herhangi bir öğeyi seçin.

:::image type="content" source="media/find-file-types.png" alt-text="Dosyalarda Bul iletişim kutusunun Dosya Türleri bölümünün ekran görüntüsü.":::

Bunları noktalı virgül () ile ayırarak birden çok dosya türü `;` arayabilirsiniz. Ayrıca, herhangi bir yola veya dosya türüne ünlem işareti () ön eki eklerini kullanarak klasörleri ve dosyaları hariç `!` tutabilirsiniz.

### <a name="append-results"></a>Sonuçları ekleme

Geçerli aramanın sonuçlarını önceki arama sonuçlarına eklemek için bu seçeneği kullanın.

::: moniker-end

::: moniker range="vs-2017"

### <a name="expression-builder"></a>İfade Oluşturucusu

Arama dizesinde normal ifadeler kullanmak için, arama kutusunun yanındaki bitişik  **expression Builder** düğmesini seçin. Daha fazla bilgi için [bkz. normal ifadeleri Visual Studio.](../ide/using-regular-expressions-in-visual-studio.md)

> [!NOTE]
> İfade **Oluşturucusu** düğmesi yalnızca Bul seçenekleri altında Normal **İfadeleri Kullan'ı** **seçtiydiyseniz etkinleştirilir.**

## <a name="look-in"></a>Şuna bakın:

Arama açılan listesinden **seçilen** seçenek, Dosyalarda  Bul seçeneğinin yalnızca şu anda etkin olan dosyalarda mı yoksa belirli klasörlerde depolanan tüm dosyalarda mı arama yaptığına karar verilsin.

Listeden bir arama kapsamı seçin veya Gözat **(...)**  düğmesine tıklayarak Arama Klasörlerini Seç iletişim kutusunu görüntüleyin ve kendi dizin kümenizi girin. Ayrıca, Doğrudan Arama kutusuna bir **yol da girebilirsiniz.**

> [!WARNING]
> Çözümün Tamamı **veya Geçerli Çözüm** **Project** seçerseniz proje ve çözüm dosyaları aranır. Proje dosyalarına bakmak için bir arama klasörü seçin.

> [!NOTE]
> Kaynak kodu **denetiminden** kullanıma alınmış bir dosyayı aramak için Arama seçeneğini kullanırsanız, yalnızca yerel makinenize indirilen dosyanın sürümü bulunur.

::: moniker-end

::: moniker range="vs-2017"

## <a name="include-subfolders"></a>Alt klasörleri dahil etmek

Look in klasörünün alt **klasörlerinin aranacak** olduğunu belirtir.

## <a name="find-options"></a>Seçenekleri bulma

Seçenekleri bul bölümünü genişletebilirsiniz **veya daraltabilirsiniz.** Aşağıdaki seçenekleri kullanabilir veya temizebilirsiniz:

**Eşleşme durumu**

Seçildiğinde, Sonuçları **Bul araması** büyük/küçük harfe duyarlı olur

**Tam sözcüğü eşle**

Seçildiğinde, Sonuçları **Bul pencereleri** yalnızca tam sözcük eşleşmeleri geri döner.

**Normal İfadeler Kullanma**

Bu onay kutusu seçiliyse, Bul veya Değiştir metin kutularında eşleşmek üzere metin desenlerini tanımlamak **için özel** **notalar** kullanabilirsiniz. Bu ifadelerin listesi için [bkz. Visual Studio'de normal ifadeler kullanma.](../ide/using-regular-expressions-in-visual-studio.md)

**Bu dosya türlerine bakın**

Bu liste, Dizinlerde ara içinde aranan **dosya türlerini** gösterir. Bu alan boşsa Dizinlerde ara **dizininde yer alan tüm** dosyalar aranır.

Bu belirli türlerde dosyaları bulacak önceden yapılandırılmış bir arama dizesi girmek için listeden herhangi bir öğeyi seçin.

## <a name="result-options"></a>Sonuç seçenekleri

Sonuç seçenekleri bölümünü genişletebilirsiniz **veya daraltabilirsiniz.** Liste sonuçları altındaki **aşağıdaki seçenekler** seçilebilir veya temiz olabilir:

**Sonuçları bulma 1 penceresi**

Seçildiğinde, geçerli aramanın sonuçları Sonuçları Bul **1 penceresinin içeriğinin yerini** alar. Arama sonuçlarınızı görüntülemek için bu pencere otomatik olarak açılır. Bu pencereyi el ile açmak için Görünüm **menüsünden Diğer Windows'ı** **ve** ardından Sonuçları Bul **1'i seçin.**

**Sonuçları bulma 2 penceresi**

Seçildiğinde, geçerli aramanın sonuçları Sonuçları Bul **2 penceresinin içeriğinin yerini** alar. Arama sonuçlarınızı görüntülemek için bu pencere otomatik olarak açılır. Bu pencereyi el ile açmak için Görünüm **menüsünden Diğer** **Windows'yi** seçin ve Sonuçları Bul **2'yi seçin.**

> [!TIP]
> Alt 1 veya Alt 2 **tuşlarına** basarak sonuçlar + **pencereleri** arasında  + **geçişler yapmak için kullanabilirsiniz.**

**Sonuç tablosu bulma**

Aramanın sonuçlarını metin listesi yerine tablo biçiminde görüntüler.

**Sonuçları ekleme**

Aramanın sonuçlarını önceki arama sonuçlarına ekler.

**Yalnızca dosya adlarını görüntüleme**

Arama eşleşmelerini görüntülemek yerine arama eşleşmelerini içeren dosyaların listesini görüntüler.

::: moniker-end

## <a name="search-results"></a>Arama sonuçları

:::moniker range=">=vs-2022"

Tüm sonuçlar için bir arama gerçekleştirin, sonuçlar kullanılabilir hale geldi olarak görünür.

> [!NOTE]
> Visual Studio proje açma, dalları değiştirme veya dosya listesini başka bir şekilde değiştirme gibi kod bağlamınız yüklendikten sonra dizin oluşturmaya başlar. Kaynak dosyalarınızın dizinini Visual Studio arama yaparken arama yaptıysanız, sonuçların eksik olduğuyla ilgili bir uyarıyla karşınıza çıktı.

:::moniker-end

### <a name="keep-results"></a>Sonuçları tut

Diğer aramaları yaparken sonuçları bir aramadan tutabilirsiniz. Bu, sonuçları karşılaştırmayı ve yan yana görmeyi kolaylaştırır.

:::moniker range=">=vs-2022"

:::image type="content" source="media/vs-2022/find-files-search-results.png" alt-text="Sekmeler olarak gösterilen üç arama sonuçlarının yer alan Arama Sonuçları penceresinin ekran görüntüsü.":::

:::moniker-end

:::moniker range="<=vs-2019"

:::image type="content" source="media/find-files-search-results.png" alt-text="Sekmeler olarak gösterilen üç arama sonuçlarının yer alan Arama Sonuçları penceresinin ekran görüntüsü.":::

:::moniker-end

Çeşitli arama sonuçlarını tutmak için, her **aramadan sonra** Sonuçları Tut düğmesini seçin. Ardından, başka bir şey için arama yapınca sonuçlar yeni bir sekmede gösterilir. En fazla beş aramanın sonuçlarını tutabilirsiniz. Gösterilen beş arama sonucu varsa, sonraki arama en eski arama sonucu sekmesini yeniden kullanmalıdır.

:::moniker range=">=vs-2022"

2022 ve sonraki bir Visual Studio, sonuçları her zaman tutmak Visual Studio için bu ayardan geçebilirsiniz. Araçlar Seçenekler **Genel**  >    >  **Bul ve**  >  **Değiştir'e** gidin ve Arama sonuçlarını varsayılan olarak tut onay kutusunu **seçin.**

:::moniker-end

## <a name="see-also"></a>Ayrıca bkz.

- [Dosyalarda değiştirme](../ide/replace-in-files.md)
- [Metin bulma ve değiştirme](../ide/finding-and-replacing-text.md)
- [Visual Studio komutları](../ide/reference/visual-studio-commands.md)