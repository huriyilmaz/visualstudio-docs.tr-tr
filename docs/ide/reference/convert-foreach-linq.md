---
title: Foreach döngüsünü LINQ 'a Dönüştür
descritpion: Convert any foreach loop that uses an IEnumerable to a LINQ query or a LINQ call form (also known as a LINQ method).
ms.date: 07/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 390e66fa01d49f217140c3c030bcc54fd349e402
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86285400"
---
# <a name="convert-a-foreach-loop-to-linq"></a>Foreach döngüsünü LINQ 'a Dönüştür

Bu yeniden düzenleme için geçerlidir:

- C#

**Ne:** IEnumerable kullanan *foreach* DÖNGÜNÜZÜ bir LINQ SORGUSUNA veya LINQ çağrı formuna (LINQ yöntemi olarak da bilinir) kolayca dönüştürmenize olanak sağlar.

**Ne zaman:** IEnumerable kullanan bir foreach döngüsüne sahipsiniz ve bu döngünün LINQ sorgusu olarak okunmasını istiyorsunuz.

**Neden:** Bir foreach döngüsü yerine LINQ sözdizimini kullanmayı tercih edersiniz. [LINQ](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq) , C# içindeki birinci sınıf dil yapısına bir sorgu oluşturur. LINQ bir dosyadaki kod miktarını azaltabilir, kodu daha kolay okunabilir hale getirir ve farklı veri kaynaklarının benzer sorgu ifadesi desenlerine sahip olmasına izin verir.

> [!NOTE]
> LINQ sözdizimi genellikle bir foreach döngüsünden daha az verimlidir. Kodunuzun okunabilirliğini geliştirmek için LINQ kullandığınızda oluşabilecek herhangi bir performans zorunluluğunu getirir dikkat etmeniz iyidir.

## <a name="convert-a-foreach-loop-to-linq-refactoring"></a>Foreach döngüsünü LINQ yeniden düzenlemeye Dönüştür

1. İmlecinizi `foreach` anahtar sözcüğe yerleştirin.

    ![IEnumerable örneği kullanan foreach](media/convert-foreach-to-LINQ.png)

2. **CTRL**tuşuna basın + **.** **hızlı eylemleri ve yeniden düzenlemeler** menüsünü tetiklemek için.

   ![LINQ menü örneğine Dönüştür](media/convert-foreach-to-LINQ-codefix.png)

3. **LINQ 'A Dönüştür** veya **LINQ 'a Dönüştür (çağrı formu)** seçeneğini belirleyin.

   ![LINQ sorgu sonucu örneği](media/convert-foreach-to-LINQ-result.png)

   ![LINQ Call form sonuç örneği](media/convert-foreach-to-LINQ-callform-result.png)

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
- [.NET geliştiricileri için ipuçları](../csharp-developer-productivity.md)
