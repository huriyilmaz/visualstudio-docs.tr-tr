---
title: Foreach döngüyü LINQ'ya dönüştürün
descritpion: Convert any foreach loop that uses an IEnumerable to a LINQ query or a LINQ call form (also known as a LINQ method).
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
ms.openlocfilehash: 12c03830ccd37e0970e3c74bc78cdd9c8a8732b7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094220"
---
# <a name="convert-a-foreach-loop-to-linq"></a>Foreach döngüyü LINQ'ya dönüştürün

Bu yeniden düzenleme aşağıdakiler için geçerlidir:

- C#

- Visual Basic

**Ne:** Ayrılmaz bir LINQ sorgusuna veya LINQ çağrı formuna (LINQ yöntemi olarak da bilinir) kolayca dönüştüren *foreach* döngünüzü kolayca dönüştürmenizi sağlar.

**Ne zaman:** Bir Ayrılmaz kullanan bir foreach döngü var ve bu döngü bir LINQ sorgusu olarak okunmasını istiyorum.

**Neden:** Her bir döngü yerine LINQ sözdizimini kullanmayı tercih edersiniz. [LINQ,](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq) C#'da birinci sınıf bir dil yapısına sorgu yapar. LINQ, bir dosyadaki kod miktarını azaltabilir, kodun okunmasını kolaylaştırabilir ve farklı veri kaynaklarının benzer sorgu ifade şekillerine sahip olmasını sağlayabilir.

> [!NOTE]
> LINQ sözdizimi genellikle foreach döngüsünden daha az verimlidir. Kodunuzu okunabilirliğini artırmak için LINQ kullandığınızda oluşabilecek herhangi bir performans tradeoff farkında olmak iyidir.

## <a name="convert-a-foreach-loop-to-linq-refactoring"></a>Foreach döngüyü LINQ refactoring'e dönüştürün

1. İmlecinizi anahtar `foreach` kelimeye yerleştirin.

    ![Her biri, Tümesiye edilebilir numuneyi kullanarak](media/convert-foreach-to-LINQ.png)

2. **Ctrl**+tuşuna**basın.** **Hızlı Eylemler ve Refactorings** menüsünü tetiklemek için.

   ![LINQ menü örneğine dönüştürün](media/convert-foreach-to-LINQ-codefix.png)

3. **LINQ'a Dönüştür'ü** veya **Linq'e Dönüştür 'ü (çağrı formu) seçin.**

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
- [Değişiklikleri Önizleme penceresi](../../ide/preview-changes.md)
- [.NET Geliştiricileri için ipuçları](../csharp-developer-productivity.md)
