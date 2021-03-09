---
title: LINQ ifadesini basitleştirme
description: Bu yeniden düzenleme, Where yöntemi için gereksiz yere gereksiz çağrıları kaldırmak için kullanılır.
ms.date: 08/12/2020
ms.topic: reference
author: m-redding
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 20a3524d786b1f03fc3e221d1b257892d9439a0b
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2021
ms.locfileid: "102466173"
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
