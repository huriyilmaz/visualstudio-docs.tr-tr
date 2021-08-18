---
title: LINQ ifadesini basitleştirme
description: Bu yeniden düzenleme, Where yöntemi için Numaralanabilir'e yapılan gereksiz çağrıları kaldırmak için kullanılır.
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
ms.openlocfilehash: dc52c81b8899d5b2d2ef3fb22581d3f7ef6c1a68
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122041106"
---
# <a name="simplify-linq-expression"></a>LINQ ifadesini basitleştirme

Bu yeniden düzenleme aşağıdakiler için geçerlidir:

- C#

**Ne:** için örneklerini ve aşağıdaki Numaralanabilir yöntemleri yeniden `SomeEnumerableType.Where(<LambdaExpression>).Single()` sıralar: , , , , , , `SomeEnumerable.Single(<LambdaExpression>)` ve `Enumerable.Single()` `SingleOrDefault()` `Last()` `LastOrDefault()` `Any()` `Count()` `First()` `FirstOrDefault()` .

**Ne zaman:**  yönteminin , ve gibi çağıran tüm örneklerin bağımsız değişkeni yok ve önünde `Single()` `SingleOrDefault()` bir ifade `Where()` var. İfadeye yapılan `Where()` giriş bir ifade ağacı olarak oluşturulur.

**Neden:** yöntemi için Numaralanabilir gereksiz çağrının kaldırılması `.Where()` performansı ve okunabilirliği artırır.

## <a name="how-to"></a>Nasıl yapılır

1. İmlecinizi `SomeEnumerableType.Where(<LambdaExpression>).Single()` Visual Studio'daki örneğine yerleştirin.
2. **Ctrl tuşuna** + **basın.** Hızlı Eylemler **ve Yeniden Düzenleme menüsünü tetiklemek** için.
3. **LINQ ifadesini basitleştir'i seçin**

   ![typeof ifadesini nameof ifadesine dönüştürme](media/simplify-linq-expression.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
