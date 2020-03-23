---
title: For döngüsüne dönüştürülecek refaktör kodu
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: af52761f5cb199c7f842d01589c35501898b09aa
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094599"
---
# <a name="refactoring-to-convert-between-a-for-loop-and-a-foreach-statement"></a>For döngüsü ile foreach deyimi arasında dönüştürmeyi yeniden düzenleme

Bu makalede, iki döngü yapıları arasında dönüştüren Hızlı Eylemler refactorings açıklanır. Kodunuzda [for](/dotnet/csharp/language-reference/keywords/for) döngüsü ile [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) deyimi arasında geçiş yapmak isteyebileceğin bazı nedenler içerir.

## <a name="convert-a-for-loop-to-a-foreach-statement"></a>For döngüsüne foreach deyimini dönüştürme

Kodunuzda [for](/dotnet/csharp/language-reference/keywords/for) döngüsü varsa, bu yeniden düzenlemeyi [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) deyimine dönüştürmek için kullanabilirsiniz.

Bu yeniden düzenleme aşağıdakiler için geçerlidir:

- C#

- Visual Basic

> [!NOTE]
> Foreach Hızlı Eylem refactoring **dönüştürün** yalnızca üç bölümden oluşan döngüler [için](/dotnet/csharp/language-reference/keywords/for) kullanılabilir: bir baş harf, durum ve yineleyici.

### <a name="why-convert"></a>Neden dönüştürmek

[For](/dotnet/csharp/language-reference/keywords/for) döngüsüne dönüştürmek isteyebileceğin [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) nedenler şunlardır:

- Öğelere erişmek için bir dizin dışında döngü içindeki yerel döngü değişkenini kullanmazsınız.

- Kodunuzu basitleştirmek ve baş harf, koşul ve yineleyici bölümlerindeki mantık hataları olasılığını azaltmak istiyorsunuz.

### <a name="how-to-use-it"></a>Nasıl kullanılır?

1. Caret'inizi anahtar `for` kelimeye yerleştirin.

1. **Ctrl**+tuşuna**basın.** veya kod dosyasının kenar boşluğundaki tornavida ![simgesi](../media/screwdriver-icon.png) simgesine tıklayın.

   ![Foreach menüsüne dönüştürün](media/convert-to-foreach.png)

1. **'Foreach' için Dönüştür'ü**seçin. Veya, [Değişiklikleri Önizleme](../../ide/preview-changes.md) iletişim kutusunu açmak için Değişiklikleri **Önizleyin'i** seçin ve ardından **Uygula'yı**seçin.

## <a name="convert-a-foreach-statement-to-a-for-loop"></a>Foreach deyimini for döngüsüne dönüştürme

Eğer bir [foreach (C# veya](/dotnet/csharp/language-reference/keywords/foreach-in) [Her biri için varsa ... Kodunuzda sonraki (Visual Basic)](/dotnet/visual-basic/language-reference/statements/for-each-next-statement) deyimi, bir [for](/dotnet/csharp/language-reference/keywords/for) döngüsüne dönüştürmek için bu refactoring kullanabilirsiniz.

Bu yeniden düzenleme aşağıdakiler için geçerlidir:

- C#

- Visual Basic

### <a name="why-convert"></a>Neden dönüştürmek

[Foreach](/dotnet/csharp/language-reference/keywords/foreach-in) deyimini [for](/dotnet/csharp/language-reference/keywords/for) döngüsüne dönüştürmek isteyebileceğin nedenler şunlardır:

- Öğeye erişmekten daha fazlası için döngü içindeki yerel döngü değişkenini kullanmak istiyorsunuz.

- Çok [boyutlu bir dizi aracılığıyla yinelediğiniz](/dotnet/csharp/programming-guide/arrays/using-foreach-with-arrays) ve dizi öğeleri üzerinde daha fazla denetim istiyorsunuz.

### <a name="how-to-use-it"></a>Nasıl kullanılır?

1. Caret'inizi `For Each` anahtar `foreach` kelimeye yerleştirin.

1. **Ctrl**+tuşuna**basın.** veya kod dosyasının kenar boşluğundaki tornavida ![simgesi](../media/screwdriver-icon.png) simgesine tıklayın.

   ![Menü için dönüştürün](media/convert-to-for.png)

1. **'for' olarak dönüştür'ü**seçin. Veya, [Değişiklikleri Önizleme](../../ide/preview-changes.md) iletişim kutusunu açmak için Değişiklikleri **Önizleyin'i** seçin ve ardından **Uygula'yı**seçin.

1. Yeniden düzenleme yeni bir yineleme sayısı değişkeni tanıdığından, **Yeniden adlandırma** kutusu editörün sağ üst köşesinde görünür. Değişken için farklı bir ad seçmek istiyorsanız, bunu yazın ve sonra **Enter** tuşuna basın veya **Yeniden Adlandır** kutusunda **Uygula'yı** seçin. Yeni bir ad seçmek istemiyorsanız, **Yeniden Adlandır** kutusunu kapatmak için **Esc** tuşuna basın veya **Uygula'yı** seçin.

> [!NOTE]
> C# için, bu yeniden faktörler tarafından oluşturulan kod, koleksiyondaki öğelerin türü için açık bir tür veya [var](/dotnet/csharp/language-reference/keywords/var) kullanır. Oluşturulan koddaki açık veya örtülü tür, kapsamda bulunan kod stili ayarlarına bağlıdır. Bu özel kod stili **ayarları, Araçlar** > **Seçenekleri** > **Metin Düzenleyicisi** > **C#** > **Code Style** > **General** > **\'var' tercihleri**altında makine düzeyinde veya [EditorConfig](../../ide/editorconfig-language-conventions.md#implicit-and-explicit-types) dosyasındaki çözüm düzeyinde yapılandırılır. **Seçenekler'de**kod stili ayarını değiştirirseniz, değişikliklerin etkili olması için kod dosyasını yeniden açın.

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
- [Değişiklikleri Önizleme](../../ide/preview-changes.md)
