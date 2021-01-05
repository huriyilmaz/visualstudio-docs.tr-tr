---
title: typeof ifadesini nameof ifadesine dönüştürme
description: Visual Studio 'daki hızlı eylemler ve yeniden düzenlemeler menüsünü kullanarak Visual Basic typeof for C# ve GetType ' deki NameOf öğesinin NameOf öğesine nasıl dönüştüreceğiniz hakkında bilgi edinin.
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
ms.openlocfilehash: ce76b82e2ebc68634be7cf4d463f6b8216d81e06
ms.sourcegitcommit: 3c571f44bfd6402efea5187af43df287bac5b6ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/24/2020
ms.locfileid: "97761205"
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
      <br>' **Typeof ' öğesini ' NameOf ' olarak Dönüştür**' ![ ü seçin: ' typeof ' öğesini ' NameOf ' olarak Dönüştür ve Visual Studio 'daki hızlı eylemler ve yeniden düzenlemeler menüsünün ekran görüntüsü ' NameOf ' seçili ve C# kod değişiklikleri gösteriliyor.](media/convert-type-of.PNG)

    - Visual Basic
      <br>' **GetType ' öğesini ' NameOf ' öğesine Dönüştür**' i seçin: ![ Visual Studio 'daki hızlı eylemler ve yeniden düzenlemeler menüsünün ekran görüntüsü ' ' NameOf ' seçili ve Visual Basic kod değişikliği gösteriliyor.](media/convert-get-type.PNG)

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
