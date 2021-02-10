---
title: LINQ ifadesini basitleştirme
ms.date: 08/12/2020
ms.topic: reference
author: m-redding
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 006fc0fe84b11573ece98019a4446d83de52d62c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99957562"
---
# <a name="simplify-linq-expression"></a>LINQ ifadesini basitleştirme

Bu yeniden düzenleme için geçerlidir:

- C#

**Ne:** Ve için şunların `SomeEnumerableType.Where(<LambdaExpression>).Single()` örneklerinin `SomeEnumerable.Single(<LambdaExpression>)` `Enumerable.Single()` yanı sıra aşağıdaki sıralanabilir Yöntemler: `SingleOrDefault()` , `Last()` ,, `LastOrDefault()` `Any()` , `Count()` , `First()` ve `FirstOrDefault()` .

**Ne zaman:**  Yöntemin,, vb. çağırdığı tüm örnekler `Single()` `SingleOrDefault()` , hiçbir bağımsız değişkeni içermez ve önünde bir `Where()` ifade gelir. `Where()`İfadenin girişi bir ifade ağacı olarak oluşturulamıyor.

**Neden:** Yöntemi için numaralandırılabilir çağrıya gereksiz çağrının kaldırılması `.Where()` performansı ve okunabilirliğini geliştirir.

## <a name="how-to"></a>Nasıl yapılır

1. İmlecinizi `SomeEnumerableType.Where(<LambdaExpression>).Single()` Visual Studio 'daki örnek içine yerleştirin.
2. **CTRL** tuşuna basın + **.** **hızlı eylemleri ve yeniden düzenlemeler** menüsünü tetiklemek için.
3. Bir **LINQ Ifadesini Basitleştir** seçeneğini belirleyin

   ![typeof ifadesini nameof ifadesine dönüştürme](media/simplify-linq-expression.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
