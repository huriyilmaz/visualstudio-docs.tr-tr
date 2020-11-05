---
title: typeof ifadesini nameof ifadesine dönüştürme
ms.date: 08/12/2020
ms.topic: reference
author: m-redding
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 96bd4d67302fb09e5c1cb7837ad73b345ad88c81
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93400330"
---
# <a name="convert-typeof-to-nameof"></a>Dönüştür `typeof``nameof`

Bu yeniden düzenleme için geçerlidir:

- C#
- Visual Basic

**Ne:** , ' In bir örneğini C# ' de `typeof(<QualifiedType>).Name` `nameof(<QualifiedType>)` ve bir örneğini Visual Basic olarak dönüştürmenize imkan tanır `GetType(<QualifiedType>).Name` `NameOf(<QualifiedType>)` .

**Ne zaman:**  Öğesinin tüm örnekleri `typeof(<QualifiedType>).Name` `someType` genel tür değildir. Bu dışlama gereklidir çünkü bu durum, ile aynı dize değerini döndürmez `nameof(<QualifiedType>)` . Aynı değer Visual Basic örneği için de geçerlidir.

**Neden:** `nameof` Öğesinin adı yerine kullanılarak, `type` bir nesneyi alma ile ilgili yansımayı önler `type` ve bunu yazmanın daha kolay bir yoludur.

## <a name="how-to"></a>Nasıl yapılır

1. İmlecinizi `typeof(<QualifiedType>).Name` C# örneği Içine veya `GetType(<QualifiedType>).Name` Visual Basic içine yerleştirin.

2. **CTRL** tuşuna basın + **.** **hızlı eylemleri ve yeniden düzenlemeler** menüsünü tetiklemek için.

3. Aşağıdaki seçeneklerden birini belirleyin:

    - C#
      <br>**' Typeof ' öğesini ' NameOf ' olarak Dönüştür** ' ü seçin: ![ typeof 'ı NameOf olarak Dönüştür](media/convert-type-of.PNG)

    - Visual Basic
      <br>**' GetType ' öğesini ' NameOf ' öğesine Dönüştür** ' ü seçin: ![ typeof adını NameOf olarak Dönüştür](media/convert-get-type.PNG)

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
