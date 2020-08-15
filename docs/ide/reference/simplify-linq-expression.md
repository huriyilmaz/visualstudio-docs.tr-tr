---
title: LINQ ifadesini Basitleştir
ms.date: 08/12/2020
ms.topic: reference
author: m-redding
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 04485d6ce67c822fd0620bd63f3557851db6dbb9
ms.sourcegitcommit: 577c905de52057a741e68c2ed168ea527813fda5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/15/2020
ms.locfileid: "88251317"
---
# <a name="simplify-linq-expression"></a>LINQ ifadesini Basitleştir

Bu yeniden düzenleme için geçerlidir:

- C#

**Ne:** Ve için şunların `SomeEnumerableType.Where(<LambdaExpression>).Single()` örneklerinin `SomeEnumerable.Single(<LambdaExpression>)` `Enumerable.Single()` yanı sıra aşağıdaki sıralanabilir Yöntemler: `SingleOrDefault()` , `Last()` ,, `LastOrDefault()` `Any()` , `Count()` , `First()` ve `FirstOrDefault()` .

**Ne zaman:**  Yöntemin,, vb. çağırdığı tüm örnekler `Single()` `SingleOrDefault()` , hiçbir bağımsız değişkeni içermez ve önünde bir `Where()` ifade gelir. `Where()`İfadenin girişi bir ifade ağacı olarak oluşturulamıyor.

**Neden:** Yöntemi için numaralandırılabilir çağrıya gereksiz çağrının kaldırılması `.Where()` performansı ve okunabilirliğini geliştirir.

## <a name="how-to"></a>Nasıl yapılır

1. İmlecinizi `SomeEnumerableType.Where(<LambdaExpression>).Single()` Visual Studio 'daki örnek içine yerleştirin.
2. **CTRL**tuşuna basın + **.** **hızlı eylemleri ve yeniden düzenlemeler** menüsünü tetiklemek için.
3. Bir **LINQ Ifadesini Basitleştir** seçeneğini belirleyin

   ![Typeof 'ı NameOf öğesine Dönüştür](media/simplify-linq-expression.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
