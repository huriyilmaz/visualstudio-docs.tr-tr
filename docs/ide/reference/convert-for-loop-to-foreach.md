---
title: For döngüsüne foreach deyimini dönüştürmek için yeniden düzenleme
description: For döngüsü ile foreach deyimi arasında dönüştürme yapmak için Hızlı Eylemler ve Yeniden Düzenleme menüsünü kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 9e24b262ebd0ddb169ae754ddc9a57cfffba342e7cb4ed836d195b41d3a58605
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121430296"
---
# <a name="refactoring-to-convert-between-a-for-loop-and-a-foreach-statement"></a>For döngüsü ile foreach deyimi arasında dönüştürme için yeniden düzenleme

Bu makalede, iki döngü yapısı arasında dönüştürmeye neden olan Hızlı Eylemler yeniden düzenlemeleri açıklanmıştır. Kodunda for döngüsü ile [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) deyimi arasında geçiş yapmak istemenizin bazı nedenleri vardır. [](/dotnet/csharp/language-reference/keywords/for)

## <a name="convert-a-for-loop-to-a-foreach-statement"></a>For döngüsünden foreach deyimine dönüştürme

Kodunda [for döngüsü](/dotnet/csharp/language-reference/keywords/for) varsa bu yeniden düzenlemeyi kullanarak [foreach deyimine dönüştürebilirsiniz.](/dotnet/csharp/language-reference/keywords/foreach-in)

Bu yeniden düzenleme aşağıdakiler için geçerlidir:

- C#

- Visual Basic

> [!NOTE]
> **Foreach'e** Dönüştür Hızlı Eylem yeniden düzenlemesi yalnızca üç bölümü de içeren döngüler için kullanılabilir: başlatıcı, koşul ve tekrarlayıcı. [](/dotnet/csharp/language-reference/keywords/for)

### <a name="why-convert"></a>Neden dönüştürmeli?

For döngüsünden [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) [deyimine](/dotnet/csharp/language-reference/keywords/for) dönüştürmek isteme nedenlerinden bazıları şunlardır:

- Öğelere erişmek için bir dizin olarak dışında döngü içinde yerel döngü değişkenlerini kullanmazsiniz.

- Kodunuzu basitleştirmek ve başlatıcı, koşul ve tekrarlayıcı bölümlerindeki mantık hatalarının olasılığını azaltmak istiyorsanız.

### <a name="how-to-use-it"></a>Nasıl kullanılır?

1. Caret'inizi anahtar sözcüğüne `for` ekleyin.

1. **Ctrl tuşuna** + **basın.** veya kod dosyasının kenar ![ boşluğundaki ](../media/screwdriver-icon.png) tornavida Tornavida simgesine tıklayın.

   ![Foreach menüsüne dönüştürme](media/convert-to-foreach.png)

1. **'foreach' olarak dönüştür seçeneğini seçin.** Veya Değişiklikleri **önizle'yi** seçerek Değişiklikleri [Önizle iletişim kutusunu](../../ide/preview-changes.md) açın ve uygula'ya **tıklayın.**

## <a name="convert-a-foreach-statement-to-a-for-loop"></a>Foreach deyimini for döngüsüne dönüştürme

Foreach [(C#)](/dotnet/csharp/language-reference/keywords/foreach-in) veya [For Each... Ardından (Visual Basic)](/dotnet/visual-basic/language-reference/statements/for-each-next-statement) deyimini kullanarak bu yeniden düzenlemeyi kullanarak for döngüsüne [dönüştürebilirsiniz.](/dotnet/csharp/language-reference/keywords/for)

Bu yeniden düzenleme aşağıdakiler için geçerlidir:

- C#

- Visual Basic

### <a name="why-convert"></a>Neden dönüştürmeli?

Foreach deyimini [for döngüsüne](/dotnet/csharp/language-reference/keywords/foreach-in) dönüştürmek isteme [nedenlerinden](/dotnet/csharp/language-reference/keywords/for) bazıları şunlardır:

- Yalnızca öğeye erişmekten daha fazlası için döngü içinde yerel döngü değişkenlerini kullanmak istediğiniz.

- Çok [boyutlu bir dizide tekrar ediyor ve dizi](/dotnet/csharp/programming-guide/arrays/using-foreach-with-arrays) öğeleri üzerinde daha fazla denetime sahip olmak istiyor.

### <a name="how-to-use-it"></a>Nasıl kullanılır?

1. Veya anahtar sözcüğüne `foreach` `For Each` caret'inizi ekleyin.

1. **Ctrl tuşuna** + **basın.** veya kod dosyasının kenar ![ boşluğundaki ](../media/screwdriver-icon.png) tornavida Tornavida simgesine tıklayın.

   ![Menü için 'ye dönüştür](media/convert-to-for.png)

1. **'for' olarak dönüştür seçeneğini seçin.** Veya Değişiklikleri **önizle'yi** seçerek Değişiklikleri [Önizle iletişim kutusunu](../../ide/preview-changes.md) açın ve uygula'ya **tıklayın.**

1. Yeniden düzenleme yeni bir yineleme sayısı değişkenine  sahip olduğundan düzenleyicinin sağ üst köşesinde Yeniden Adlandır kutusu görünür. Değişken için farklı bir ad seçmek için yazın ve **Enter** tuşuna basın veya Yeniden Adlandır **kutusunda** **Uygula'ya** tıklayın. Yeni bir ad seçmek istemiyorsanız Esc tuşuna basın veya **Uygula'ya** **seçerek** Yeniden Adlandır **kutusunu** temizleyin.

> [!NOTE]
> C# için, bu yeniden düzenleme tarafından oluşturulan kod, koleksiyondaki öğelerin türü için açık bir tür veya [var](/dotnet/csharp/language-reference/keywords/var) kullanır. Oluşturulan kod türü açık veya örtülü, kapsamda olan kod stili ayarlarına bağlıdır. Bu kod stili ayarları, Araçlar Seçenekler Metin Düzenleyici C# Kod Stili Genel  >    >    >    >    >    >  **\' var'ın** [](/dotnet/fundamentals/code-analysis/style-rules/language-rules#implicit-and-explicit-types) tercihleri altında veya editorConfig dosyasında çözüm düzeyinde makine düzeyinde yapılandırılır. Seçenekler'de bir kod stili ayarını **değiştirirseniz** değişikliklerin etkili olmak için kod dosyasını yeniden açın.

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
- [Değişiklikleri Önizleme](../../ide/preview-changes.md)
