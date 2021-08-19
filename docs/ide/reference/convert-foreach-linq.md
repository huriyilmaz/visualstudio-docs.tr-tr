---
title: Foreach döngüsü LINQ'ye dönüştürme
description: IEnumerable kullanan foreach döngülerini LINQ sorgusuna veya LINQ çağrı formuna (LINQ yöntemi olarak da bilinir) dönüştürebilirsiniz.
ms.date: 07/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
ms.technology: vs-ide-general
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 564c18a439da1f12c5be36b53839f57ad07fb440
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122117468"
---
# <a name="convert-a-foreach-loop-to-linq"></a>Foreach döngüsü LINQ'ye dönüştürme

Bu yeniden düzenleme aşağıdakiler için geçerlidir:

- C#

**Ne:** IEnumerable kullanan *foreach* döngüyü bir LINQ sorgusuna veya LINQ çağrı formuna (LINQ yöntemi olarak da bilinir) kolayca dönüştürmenize olanak sağlar.

**Ne zaman:** IEnumerable kullanan bir foreach döngüyüz var ve bu döngüyü LINQ sorgusu olarak okumak istiyor.

**Neden:** Foreach döngüsü yerine LINQ söz dizimi kullanmayı tercih edersiniz. [LINQ,](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq) C# dilinde birinci sınıf dil yapısına bir sorgu oluşturur. LINQ, bir dosyada kod miktarını azaltır, kodun okunmasını kolaylaştırır ve farklı veri kaynaklarının benzer sorgu ifadesi desenlerine sahip olmasına olanak sağlar.

> [!NOTE]
> LINQ söz dizimi genellikle foreach döngüsünden daha az verimlidir. Kodunuzun okunabilirliğini geliştirmek için LINQ'i kullanırken ortaya çıkabilir performans farklarının farkında olmak iyi bir fikirdir.

## <a name="convert-a-foreach-loop-to-linq-refactoring"></a>Foreach döngüsü linQ yeniden düzenlemeye dönüştürme

1. İmlecinizi anahtar sözcüğüne `foreach` ekleyin.

    ![IEnumerable kullanan Foreach örneği](media/convert-foreach-to-LINQ.png)

2. **Ctrl tuşuna** + **basın.** Hızlı Eylemler **ve Yeniden Düzenleme menüsünü tetiklemek** için.

   ![LINQ menü örneğine dönüştürme](media/convert-foreach-to-LINQ-codefix.png)

3. **LINQ'ye Dönüştür veya Linq'e** **Dönüştür (çağrı formu) öğesini seçin.**

   ![LINQ sorgu sonucu örneği](media/convert-foreach-to-LINQ-result.png)

   ![LINQ çağrı formu sonuç örneği](media/convert-foreach-to-LINQ-callform-result.png)

### <a name="sample-code"></a>Örnek kod

```csharp
using System.Collections.Generic;

public class Class1
{
    public void MyMethod()
    {
        var greetings = new List<string>()
            { "hi", "yo", "hello", "howdy" };

        IEnumerable<string> enumerable()
        {
            foreach (var greet in greetings)
            {
                if (greet.Length < 3)
                {
                    yield return greet;
                }
            }

            yield break;
        }
    }
}
```

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
- [Değişiklikleri Önizle penceresi](../../ide/preview-changes.md)
- [.NET İpuçları için geliştirmeler](../csharp-developer-productivity.md)
