---
title: For döngüsünü foreach ifadesine dönüştürmek için yeniden Düzenle
description: For döngüsü ve foreach ifadesi arasında dönüştürme yapmak için hızlı eylemler ve yeniden düzenlemeler menüsünü nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 6a435824d3186cee7a32db9966cfde3db9b093bf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919706"
---
# <a name="refactoring-to-convert-between-a-for-loop-and-a-foreach-statement"></a>For döngüsü ve foreach ifadesi arasında dönüştürmek için yeniden düzenleme

Bu makalede, iki döngü yapısı arasında dönüştürme yapan hızlı eylemler yeniden düzenlemeler açıklanır. Kodunuzda bir [for](/dotnet/csharp/language-reference/keywords/for) döngüsü ve [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) ifadesi arasında geçiş yapmak isteyebileceğiniz bazı nedenleri içerir.

## <a name="convert-a-for-loop-to-a-foreach-statement"></a>For döngüsünü foreach ifadesine Dönüştür

Kodunuzda bir [for](/dotnet/csharp/language-reference/keywords/for) Loop varsa, bu yeniden düzenlemeyi bir [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) ifadesine dönüştürmek için kullanabilirsiniz.

Bu yeniden düzenleme için geçerlidir:

- C#

- Visual Basic

> [!NOTE]
> **ForEach** hızlı eylemine Dönüştür yeniden düzenlemesi yalnızca üç bölümden [oluşan Döngülerde](/dotnet/csharp/language-reference/keywords/for) kullanılabilir: Başlatıcı, koşul ve yineleyici.

### <a name="why-convert"></a>Neden dönüştürme

[For](/dotnet/csharp/language-reference/keywords/for) döngüsünü [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) ifadesine dönüştürmek isteyebileceğiniz nedenler şunlardır:

- Bir dizin olarak, öğelere erişmek için bir dizin olması dışında yerel döngü değişkenini döngü içinde kullanamazsınız.

- Kodunuzu basitleştirmek ve Başlatıcı, koşul ve yineleyici bölümlerindeki mantık hatalarının olasılığını azaltmak istiyorsunuz.

### <a name="how-to-use-it"></a>Nasıl kullanılır?

1. Giriş işaretinizi `for` anahtar sözcüğe yerleştirin.

1. **CTRL** tuşuna basın + **.** ya da ![ kod dosyasının kenar boşluğundaki screwdriver screwdriver simge ](../media/screwdriver-icon.png) simgesine tıklayın.

   ![Foreach menüsüne Dönüştür](media/convert-to-foreach.png)

1. **' Foreach ' olarak Dönüştür**' ü seçin. Ya [da Değişiklikleri Önizle iletişim kutusunu](../../ide/preview-changes.md) açmak Için **Değişiklikleri Önizle** ' yi seçin ve ardından **Uygula**' yı seçin.

## <a name="convert-a-foreach-statement-to-a-for-loop"></a>Foreach ifadesini for döngüsüne Dönüştür

Bir [foreach (C#)](/dotnet/csharp/language-reference/keywords/foreach-in) veya [her biri için... Sonraki (Visual Basic)](/dotnet/visual-basic/language-reference/statements/for-each-next-statement) deyiminizde, bu yeniden düzenlemeyi bir [for](/dotnet/csharp/language-reference/keywords/for) döngüsüne dönüştürmek için kullanabilirsiniz.

Bu yeniden düzenleme için geçerlidir:

- C#

- Visual Basic

### <a name="why-convert"></a>Neden dönüştürme

[Foreach](/dotnet/csharp/language-reference/keywords/foreach-in) ifadesini bir [for](/dotnet/csharp/language-reference/keywords/for) döngüsüne dönüştürmek isteyebileceğiniz nedenler şunlardır:

- Yalnızca öğeye erişenden daha fazla bilgi için döngü içinde yerel döngü değişkenini kullanmak istiyorsunuz.

- [Çok boyutlu bir dizide yineleme](/dotnet/csharp/programming-guide/arrays/using-foreach-with-arrays) yapılır ve dizi öğeleri üzerinde daha fazla denetim istiyorsunuz.

### <a name="how-to-use-it"></a>Nasıl kullanılır?

1. Giriş işaretini `foreach` veya `For Each` anahtar sözcüğüne yerleştirin.

1. **CTRL** tuşuna basın + **.** ya da ![ kod dosyasının kenar boşluğundaki screwdriver screwdriver simge ](../media/screwdriver-icon.png) simgesine tıklayın.

   ![Menüye Dönüştür](media/convert-to-for.png)

1. **' For ' olarak Dönüştür '** ü seçin. Ya [da Değişiklikleri Önizle iletişim kutusunu](../../ide/preview-changes.md) açmak Için **Değişiklikleri Önizle** ' yi seçin ve ardından **Uygula**' yı seçin.

1. Yeniden düzenleme yeni bir yineleme sayısı değişkeni tanıtıldığı için, düzenleyicinin sağ üst köşesinde **Yeniden Adlandır** kutusu görünür. Değişken için farklı bir ad seçmek istiyorsanız, yazın ve **ENTER tuşuna basın** veya **Yeniden Adlandır** kutusuna **Uygula** ' yı seçin. Yeni bir ad seçmek istemiyorsanız, **ESC** tuşuna basın veya **Yeniden Adlandır** kutusunu kapatmak için **Uygula** ' yı seçin.

> [!NOTE]
> C# için, bu yeniden düzenlemeler tarafından oluşturulan kod, koleksiyondaki öğelerin türü için açık bir tür ya da [var](/dotnet/csharp/language-reference/keywords/var) kullanır. Oluşturulan koddaki tür açık veya örtük, kapsamdaki kod stili ayarlarına bağlıdır. Bu özel kod stili ayarları, **Araçlar**  >  **Seçenekler**  >  **metin düzenleyici**  >  **C#**  >  **kod stili**  >  **genel**  >  **\' var ' tercihleri** altında makine düzeyinde veya bir [editorconfig](/dotnet/fundamentals/code-analysis/style-rules/language-rules#implicit-and-explicit-types) dosyasındaki çözüm düzeyinde yapılandırılır. **Seçenekler**' de bir kod stili ayarını değiştirirseniz değişikliklerin etkili olması için kod dosyasını yeniden açın.

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
- [Değişiklikleri Önizleme](../../ide/preview-changes.md)
