---
title: LINQ ifadesini basitleştirme
description: Bu yeniden düzenleme, Where yöntemi için Numaralanabilir'e yapılan gereksiz çağrıları kaldırmak için kullanılır.
ms.date: 07/05/2021
ms.topic: reference
author: m-redding
ms.author: midumont
manager: jmartens
ms.technology: vs-ide-general
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 4d97f56dbf3e8c4e3b198de413f6f4700ea4eb16
ms.sourcegitcommit: 8e74969ff61b609c89b3139434dff5a742c18ff4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2021
ms.locfileid: "128426306"
---
# <a name="simplify-linq-expression"></a>LINQ ifadesini basitleştirme

Bu yeniden düzenleme aşağıdakiler için geçerlidir:

- C#

**Ne:** için örneklerini ve aşağıdaki Numaralanabilir yöntemleri yeniden `SomeEnumerableType.Where(<LambdaExpression>).Single()` sıralar: , , , , , `SomeEnumerable.Single(<LambdaExpression>)` ve `Enumerable.Single()` `SingleOrDefault()` `Last()` `LastOrDefault()` `Any()` `Count()` `First()` `FirstOrDefault()` .

**Ne zaman:**  yönteminin , ve gibi çağıran tüm örneklerin bağımsız değişkeni yok ve önünde `Single()` `SingleOrDefault()` bir ifade `Where()` var. İfadeye yapılan `Where()` giriş bir ifade ağacı olarak oluşturulur.

**Neden:** yöntemi için Numaralanabilir için gereksiz çağrının kaldırılması okunabilirliği artırır ve `.Where()` bazı durumlarda performans için açıklamalara bakın.

## <a name="how-to"></a>Nasıl yapılır

1. İmlecinizi `SomeEnumerableType.Where(<LambdaExpression>).Single()` Visual Studio'daki örneğine yerleştirin.
2. **Ctrl tuşuna** + **basın.** Hızlı Eylemler **ve Yeniden Düzenleme menüsünü tetiklemek** için.
3. **LINQ ifadesini basitleştir'i seçin**

   ![typeof ifadesini nameof ifadesine dönüştürme](media/simplify-linq-expression.png)
   
## <a name="remarks"></a>Açıklamalar

Bazı durumlarda bu yeniden düzenleme performansı düşürebilir. ve üzerinde LINQ `List<T>` işlemleri `T[]` bu durumda iyileştirilmiş değildir ve daha düşük performansa neden olur.

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
