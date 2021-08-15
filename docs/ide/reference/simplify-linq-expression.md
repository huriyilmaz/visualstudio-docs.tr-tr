---
title: LINQ ifadesini basitleştirme
description: Bu yeniden düzenleme, Where yöntemi için gereksiz yere gereksiz çağrıları kaldırmak için kullanılır.
ms.date: 08/12/2020
ms.topic: reference
author: m-redding
ms.author: midumont
manager: jmartens
ms.technology: vs-ide-general
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 951f7bebe8e63139326081c70615d91cf0b958018a964ac1928651a0cb2ac0f6
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121446959"
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
