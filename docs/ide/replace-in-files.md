---
title: Dosyalarda Değiştir
description: Dosyaları değiştirme özelliği hakkında bilgi edinin ve bir dize veya ifade için belirtilen dosya kümesinin kodunu aramanıza ve bulunan eşleşmelerin bazılarını veya tümünü değiştirmenize nasıl izin verdiğini öğrenin.
ms.custom: SEO-VS-2020
ms.date: 01/04/2022
ms.topic: conceptual
f1_keywords:
- vs.findreplace.replaceinfiles
- vs.replaceinfiles
helpviewer_keywords:
- text searches, replacing text
- find and replace
- replace in files
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: cd864bb7423e95694ae63643ffd1f1be75224a72
ms.sourcegitcommit: 965372ad0d75f015403c1af508080bf799914ce3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "135804521"
---
# <a name="replace-in-files"></a>Dosyalarda Değiştir

**Dosyalardaki Değiştir** bir dize veya ifade için belirtilen dosya kümesinin kodunu aramanıza ve bulunan eşleşmelerin bazılarını veya tümünü değiştirmenize izin verir. Bulunan eşleşmeler ve gerçekleştirilen eylemler, **sonuç seçeneklerinde** seçilen **sonuçları bul** penceresinde listelenir.

::: moniker range=">=vs-2022"

:::image type="content" source="media/vs-2022/find-replace-files.png" alt-text="Visual Studio 2022 ' deki bul ve değiştir iletişim kutusunun, dosyaları değiştir sekmesi açık olan ekran görüntüsü.":::

::: moniker-end

::: moniker range="vs-2019"

:::image type="content" source="media/vs-2019/find-replace-files.png" alt-text="Visual Studio 2019 ' deki bul ve değiştir iletişim kutusunun, dosyaları değiştir sekmesi açık olan ekran görüntüsü.":::

> [!IMPORTANT]
> **Visual Studio 2019** [**sürüm 16,6**](/visualstudio/releases/2019/release-notes-v16.6/) veya önceki bir sürümünü kullanıyorsanız **bul ve değiştir** iletişim kutusu burada göründüğü gibi görünmeyebilir. ekranınızda gördüklerinize uyacak açıklamalar için bu sayfanın [Visual Studio 2017](find-in-files.md?view=vs-2017&preserve-view=true) sürümüne geçin.

::: moniker-end

::: moniker range="vs-2017"

:::image type="content" source="media/find-replace-files.png" alt-text="Visual Studio 2017 ' deki bul ve değiştir iletişim kutusunun, dosyaları değiştir sekmesi açık olan ekran görüntüsü.":::

::: moniker-end

**Bul ve Değiştir** penceresinde **dosyaları değiştir** ' i göstermek için aşağıdaki yöntemlerden herhangi birini kullanabilir veya **CTRL** + **SHIFT** + **H**' yi kullanabilirsiniz.

## <a name="to-display-replace-in-files"></a>Dosyaların değiştirilmesini görüntüleme

::: moniker range=">=vs-2019"

1. **CTRL** + **Q** tuşlarına basın ve ekranın üst kısmındaki arama kutusuna "Değiştir" yazın.

1. Sonuçlar listesinden **dosyalarda Değiştir '** i seçin.

   veya

::: moniker-end

1. **Düzenle** menüsünde **Bul ve Değiştir**' i genişletin.

2. **Dosyalarda Değiştir '** i seçin.

   veya

   **Bul ve Değiştir** penceresi zaten açıksa, araç çubuğunda, **dosyalarda Değiştir**' i seçin.

> [!NOTE]
> **Bul ve Değiştir** Aracı, `Hidden` veya özniteliğiyle Dizin aramaz `System` .

**Dosyaları değiştir** seçenekleri, iki özel durum dışında, **[dosyalardaki bul](find-in-files.md)** iletişim kutusunda olanlarla aynıdır: iletişim kutusunun alt kısmında ek eylem düğmeleri vardır. Ve iletişim kutusunda aşağıdaki değiştirme seçenekleri mevcuttur.

::: moniker range=">=vs-2019"

## <a name="replace-textbox"></a>Metin kutusunu Değiştir

**Bul** metin kutusundaki dize örneklerini başka bir dizeyle değiştirmek Için, **Replace** metin kutusuna değiştirme dizesini girin. **Bul** metin kutusunda dize örneklerini silmek için bu alanı boş bırakın. En son aradığınız dizeleri göstermek için listeyi açın. Değiştirme dizenizde bir veya daha fazla normal ifade kullanmak istiyorsanız bitişik **Ifade Oluşturucu** düğmesini seçin. Daha fazla bilgi için bkz. [Visual Studio normal Ifadeleri kullanma](../ide/using-regular-expressions-in-visual-studio.md).

::: moniker-end

::: moniker range="vs-2017"

## <a name="replace-with"></a>Şununla Değiştir

**Bulunacak** kutusunda bulunan dize örneklerini başka bir dizeyle değiştirmek Için, **Değiştir** kutusuna değiştirme dizesini girin. **Bulunacak** kutusunda dize örneklerini silmek için bu alanı boş bırakın. En son aradığınız 20 dizeyi göstermek için listeyi açın. Değiştirme dizenizde bir veya daha fazla normal ifade kullanmak istiyorsanız bitişik **Ifade Oluşturucu** düğmesini seçin. Daha fazla bilgi için bkz. [Visual Studio normal Ifadeleri kullanma](../ide/using-regular-expressions-in-visual-studio.md).

## <a name="display-file-names-only"></a>Yalnızca dosya adlarını görüntüle

Bu onay kutusu seçildiğinde, **sonuçları bul** penceresi, arama dizesini içeren tüm dosyalar için tam adları ve yolları listeler. Ancak sonuçlar, dizenin göründüğü kod satırını içermez. Bu onay kutusu yalnızca **dosyalarda bul** için kullanılabilir.

::: moniker-end

## <a name="keep-modified-files-open-after-replace-all"></a>Tümünü değiştirdikten sonra değiştirilen dosyaları açık tut

Bu seçenek belirlendiğinde, değişiklikleri geri alabilir veya kaydedebilirsiniz. böylece, değişikliklerin yapıldığı tüm dosyalar açık bırakılır. Bellek kısıtlamaları, bir değiştirme işleminden sonra açık kalabilecek dosya sayısını sınırlayabilir.

> [!CAUTION]
> Yalnızca düzenlenmek üzere açık kalan dosyalar üzerinde **geri al** ' i kullanabilirsiniz. Bu seçenek seçilmezse, zaten düzenlenmek üzere açık olmayan dosyalar kapalı kalır ve bu dosyalarda **geri alma** seçeneği kullanılabilir olmaz.

::: moniker range=">=vs-2022"

> [!NOTE]
> Visual Studio 2022 ' den başlayarak, arama performansı, son sonuçlar kullanılabilir olmayan dosyalar gibi kısmi sonuçları göstererek en iyi duruma getirilir. Ancak değiştirme işlemleri gerçekleştirdiğinizde, değiştirme işlemleri yalnızca tam arama sonuçları döndürüldüğünden başlatıldığından bu performans avantajı uygulanmaz.

::: moniker-end

## <a name="see-also"></a>Ayrıca bkz.

- [Metin bulma ve değiştirme](../ide/finding-and-replacing-text.md)
- [Dosyalarda bul](../ide/find-in-files.md)
- [Visual Studio komutları](../ide/reference/visual-studio-commands.md)
