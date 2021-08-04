---
title: Dosyalarda Bul
description: Dosya içinde Bul özelliğini ve belirli bir dosya kümesinde arama yapmak için nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 08/02/2021
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
ms.workload:
- multiple
ms.openlocfilehash: c2f3756b63cc07ed701a36b34a96c581acd9eb38
ms.sourcegitcommit: 2430a38f23ac17b65dd8d3baa806e90433aba24f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/04/2021
ms.locfileid: "115094690"
---
# <a name="find-in-files"></a>Dosyalarda Bul

**Dosyalarda bul** , belirtilen dosya kümesinde arama yapmanıza olanak tanır. bulduğu Visual Studio eşleşmeler ıde 'deki **sonuçları bul** penceresinde listelenir. Sonuçların görünmesi, **Bul ve Değiştir** Iletişim kutusunun **dosyalarda bul** sekmesinde belirlediğiniz seçeneklere bağlıdır.

::: moniker range=">=vs-2019"

:::image type="content" source="media/find-files-vs2019.png" alt-text="Visual Studio 2019 ' deki bul ve değiştir iletişim kutusunun, dosyaları bul sekmesinde açık olan ekran görüntüsü.":::

> [!IMPORTANT]
> **Visual Studio 2019** [**sürüm 16,6**](/visualstudio/releases/2019/release-notes-v16.6/) veya önceki bir sürümünü kullanıyorsanız **bul ve değiştir** iletişim kutusu burada göründüğü gibi görünmeyebilir. ekranınızda gördüklerinize uyacak açıklamalar için bu sayfanın [Visual Studio 2017](find-in-files.md?view=vs-2017&preserve-view=true) sürümüne geçin.

::: moniker-end

::: moniker range="vs-2017"

:::image type="content" source="media/find-files-vs2017.png" alt-text="Visual Studio 2017 ' deki bul ve değiştir iletişim kutusunun, dosyaları bul sekmesinde açık olan ekran görüntüsü.":::

::: moniker-end

## <a name="how-to-display-find-in-files"></a>Dosyalarda bulma görüntüleme

**Bul ve Değiştir** iletişim kutusunu açmak için aşağıdaki adımları kullanın veya **CTRL** + **SHIFT** + **F** tuşlarına basın.

1. Menü çubuğunda **Düzenle**  >  **Bul ve Değiştir**' i seçin.

1. Dışarı açılan menüden **dosyalarda bul '** ı seçin.

Bir bul işlemini iptal etmek için **CTRL** + **Kes**' e basın.

> [!NOTE]
> **Bul ve Değiştir** Aracı, `Hidden` veya özniteliğiyle Dizin aramaz `System` .

::: moniker range="vs-2017"

## <a name="find-what"></a>Şunları bulun:

Yeni bir metin dizesi veya ifade aramak **için, bunu Aranan kutusunda belirtin** .

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="search-box"></a>Arama kutusu

Yeni bir metin dizesi veya ifade aramak için arama kutusunda belirtin. En son aradığınız 20 dizeden herhangi birini aramak için, açılan listeyi açın ve dizeyi seçin.

Aşağıdaki seçenekleri seçebilir veya temizleyebilirsiniz:

- **Büyük/küçük harf eşleştir** -aramanızın büyük/küçük harfe duyarlı olduğundan emin olmak için bu seçeneği kullanın.
- **Sözcüğün tamamını Eşleştir** -bu seçeneği kullanarak aramanızın yalnızca tam sözcük eşleşmeleri döndürdüğünden emin olun.
- **Normal Ifadeleri kullan** -bu seçeneği, arama kutusunda (veya **Değiştir** metin kutusunda) eşleştirilecek metin desenlerini tanımlayan özel gösterimler kullanmak için kullanın. Bu gösterimlerin bir listesi için bkz. [Visual Studio normal Ifadeleri kullanma](../ide/using-regular-expressions-in-visual-studio.md).

    > [!Important]
    > **Ifade Oluşturucu** düğmesi, arama kutusunun yanında görünür ve yalnızca **Normal ifadeleri kullan** onay kutusunu işaretlediyseniz görünür.
    >
    > :::image type="content" source="media/find-files-expression-builder-vs-2019.png" alt-text="Dosya içinde bul iletişim kutusunun, Ifade Oluşturucusu düğmesine ve normal Ifadeler kullan onay kutusu etrafında anahat içeren ekran görüntüsü.":::

## <a name="look-in"></a>Arama yeri

**Içinde ara** açılan listesinden seçtiğiniz seçenek, **dosyalarda bul** 'un tüm çalışma alanını, tüm çözümü, geçerli projeyi, geçerli dizini, tüm açık belgeleri veya geçerli belgeyi arayacağını belirler.

Ayrıca, aramak istediğiniz yeri bulmak için bitişik **gezinme (...)** düğmesini de kullanabilirsiniz. Daha da iyi bir dizin belirttiyseniz, bu düğme değiştirmek yerine yeni dizini ekler. Örneğin, "bak" değeri ".\Code" ise, **göz at (...)** düğmesine tıklayıp "paylaşılan kod" adlı bir klasöre gidebilirsiniz. **(...)** Kutusu artık ".\Code;" öğesini gösterir. \Shared Code "ve Find komutu yürütüldüğünde, her iki klasörde da arama yapılır.

Aramanızı iyileştirmek için aşağıdaki seçenekleri seçebilir veya temizleyebilirsiniz:

- **Dış öğe Ekle** -bu seçeneği, "Windows. h" gibi, bir çözümün parçası olmayan, örneğin "Windows. h" gibi harici öğeleri dahil etmek için kullanın.
- **Çeşitli dosyaları dahil et** -bu seçeneği, açtığınız ve bir çözümün parçası olmayan dosyalar gibi çeşitli dosyaları dahil etmek için kullanın.

## <a name="file-types"></a>Dosya türleri

**Dosya türleri** seçeneği, dizinde **Bakılacak** dosya türlerini gösterir. Belirli türlerin dosyalarını bulacak önceden yapılandırılmış bir arama dizesi girmek için listedeki herhangi bir öğeyi seçin.

:::image type="content" source="media/find-file-types.png" alt-text="Dosyalarda bul iletişim kutusunun dosya türleri bölümünün ekran görüntüsü.":::

Birden çok dosya türünü, noktalı virgül () ile ayırarak arayabilirsiniz `;` . Ayrıca, bir ünlem işaretiyle () herhangi bir yola veya dosya türüne önek ekleyerek klasörleri ve dosyaları dışlayabilirsiniz `!` .

### <a name="append-results"></a>Sonuçları sona Ekle

Geçerli aramadan önceki arama sonuçlarına sonuçları eklemek için bu seçeneği kullanın.

::: moniker-end

::: moniker range="vs-2017"

### <a name="expression-builder"></a>İfade Oluşturucusu

Arama dizenizde normal ifadeler kullanmak istiyorsanız, arama kutusunun yanındaki bitişik  **Ifade Oluşturucu** düğmesini seçin. Daha fazla bilgi için bkz. [Visual Studio normal Ifadeleri kullanma](../ide/using-regular-expressions-in-visual-studio.md).

> [!NOTE]
> **Ifade Oluşturucu** düğmesi yalnızca **Bul seçenekleri** altında **Normal ifadeleri kullan** seçeneğini belirlediyseniz etkindir.

## <a name="look-in"></a>Konum:

**Arama** açılan listesinden seçilen seçenek, **dosyalarda bul '** un yalnızca şu anda etkin olan dosyalarda mi yoksa belirli klasörlerde depolanan tüm dosyalarda mı arayacağını belirler.

Listeden bir arama kapsamı seçin veya **Arama Klasörleri seç** iletişim kutusunu ve kendi dizin kümesini girmek Için, **Araştır (...)** düğmesine tıklayın. Ayrıca, doğrudan **Ara** kutusuna bir yol yazabilirsiniz.

> [!WARNING]
> **tüm çözümü** veya **geçerli Project** seçeneklerini belirlerseniz, proje ve çözüm dosyaları aranmaz. Proje dosyalarına bakmak isterseniz, bir arama klasörü seçin.

> [!NOTE]
> Kaynak kodu denetiminden kullanıma aldığınız bir dosyayı aramak için **Ara '** yı kullanırsanız, yalnızca yerel makinenize yüklenmiş olan dosyanın sürümü bulunur.

::: moniker-end

::: moniker range="vs-2017"

## <a name="include-subfolders"></a>Alt klasörleri dahil et

**Arama** klasörü alt klasörlerinin aranacağını belirtir.

## <a name="find-options"></a>Bulma seçenekleri

**Seçenekleri bul** bölümünü genişletebilir veya daraltabilirsiniz. Aşağıdaki seçenekleri seçebilir veya temizleyebilirsiniz:

**Büyük/küçük harf eşleştir**

Seçildiğinde, bir **bul sonucu** arama büyük/küçük harfe duyarlı olacaktır

**Sözcüğün tamamını Eşleştir**

Seçildiğinde, **sonuçları bul** penceresi yalnızca tüm sözcük eşleşmelerini döndürür.

**Normal Ifadeleri kullanma**

Bu onay kutusu işaretliyse, **bulma** veya **değiştirme** metin kutularında eşleşmek üzere metin desenleri tanımlamak için özel gösterimler kullanabilirsiniz. Bu gösterimlerin bir listesi için bkz. [Visual Studio normal Ifadeleri kullanma](../ide/using-regular-expressions-in-visual-studio.md).

**Bu dosya türlerine bakın**

Bu liste, dizinde **Bakılacak** dosya türlerini gösterir. Bu alan boşsa, dizinlerde **Ara içindeki** tüm dosyalar aranacaktır.

Belirli türlerin dosyalarını bulacak önceden yapılandırılmış bir arama dizesi girmek için listedeki herhangi bir öğeyi seçin.

## <a name="result-options"></a>Sonuç seçenekleri

**Sonuç seçenekleri** bölümünü genişletebilir veya daraltabilirsiniz. **Liste sonuçları** altındaki aşağıdaki seçenekler seçilebilir veya temizlenemez:

**Arama sonuçları 1 penceresi**

Seçildiğinde, geçerli aramanın sonuçları, **sonuçları Bul 1** penceresinin içeriğini değiştirir. Bu pencere, arama sonuçlarınızı göstermek için otomatik olarak açılır. bu pencereyi el ile açmak için, **görünüm** menüsünden **diğer Windows** ' yi seçin ve ardından **sonuçları bul 1**' i seçin.

**Sonuçları bul 2 penceresi**

Seçildiğinde, geçerli aramanın sonuçları, **bulma sonuçları 2** penceresinin içeriğinin yerini alır. Bu pencere, arama sonuçlarınızı göstermek için otomatik olarak açılır. bu pencereyi el ile açmak için, **görünüm** menüsünden **diğer Windows** ' yi seçin ve **sonuçları bul 2**' yi seçin.

> [!TIP]
> **Diğer** + **1** veya **alt** + **2** tuşlarına basarak sonuçlar penceresi arasında geçiş yapabilirsiniz.

**Sonuçları bul tablosu**

Aramanın sonuçlarını metin listesi yerine tablo biçiminde görüntüler.

**Sonuçları sona Ekle**

Aramadan sonuçları önceki arama sonuçlarına ekler.

**Yalnızca dosya adlarını görüntüle**

Arama eşleşmeleri içeren dosyaların bir listesini görüntüler.

::: moniker-end

## <a name="multiple-searches"></a>Birden çok arama

Diğer aramaları gerçekleştirirken sonuçları tek bir aramadan tutabilirsiniz. Bu, sonuçları karşılaştırmayı ve yan yana görmeyi kolaylaştırır.

:::image type="content" source="media/find-files-search-results.png" alt-text="Üç arama sonucu olan arama sonuçları penceresinin, sekmeler olarak gösterildiği ekran görüntüsü.":::

Birkaç arama sonucunu tutmak için, her aramadan sonra **sonuçları tut** düğmesini seçin. Daha sonra, başka bir şey aradığınızda sonuçlar yeni bir sekmede gösterilir. En fazla beş arama sonucunu izleyebilirsiniz. Gösterildiği beş arama sonucu zaten varsa, sonraki arama en eski arama sonucu sekmesini yeniden kullanacaktır.

## <a name="see-also"></a>Ayrıca bkz.

- [Dosyalarda Değiştir](../ide/replace-in-files.md)
- [Metin bulma ve değiştirme](../ide/finding-and-replacing-text.md)
- [Visual Studio komutları](../ide/reference/visual-studio-commands.md)