---
title: typeof ifadesini nameof ifadesine dönüştürme
description: Visual Studio ' de hızlı eylemler ve yeniden düzenlemeler menüsünü kullanarak, typeof 'yi C# ve GetType ' de nameof ' a dönüştürmek için Visual Basic.
ms.date: 08/12/2020
ms.topic: reference
author: m-redding
ms.author: midumont
manager: jmartens
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 98f1680b63060f820bf8c7a8b23efd2731e18f98
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122101524"
---
# <a name="convert-typeof-to-nameof"></a>Dönüştür `typeof``nameof`

Bu yeniden düzenleme için geçerlidir:

- C#
- Visual Basic

**Ne:** , ' In bir örneğini C# ' de `typeof(<QualifiedType>).Name` `nameof(<QualifiedType>)` ve bir örneğini Visual Basic olarak dönüştürmenize imkan tanır `GetType(<QualifiedType>).Name` `NameOf(<QualifiedType>)` .

**Ne zaman:**  Öğesinin tüm örnekleri `typeof(<QualifiedType>).Name` `someType` genel tür değildir. Bu dışlama gereklidir çünkü bu durum, ile aynı dize değerini döndürmez `nameof(<QualifiedType>)` . aynı değer Visual Basic örneği için de geçerlidir.

**Neden:** `nameof` Öğesinin adı yerine kullanılarak, `type` bir nesneyi alma ile ilgili yansımayı önler `type` ve bunu yazmanın daha kolay bir yoludur.

## <a name="how-to"></a>Nasıl yapılır

1. İmlecinizi `typeof(<QualifiedType>).Name` C# örneği Içine veya `GetType(<QualifiedType>).Name` Visual Basic içine yerleştirin.

2. **CTRL** tuşuna basın + **.** **hızlı eylemleri ve yeniden düzenlemeler** menüsünü tetiklemek için.

3. Aşağıdaki seçeneklerden birini belirleyin:

    - C#
      <br>' **typeof ' öğesini ' nameof ' olarak dönüştür**' ![ ü seçin: ' typeof ' öğesini ' nameof ' olarak dönüştür ' Visual Studio içindeki hızlı eylemler ve yeniden düzenlemeler menüsünün ekran görüntüsü ' nameof ' seçili ve C# kod değişiklikleri gösteriliyor.](media/convert-type-of.PNG)

    - Visual Basic
      <br>' **gettype ' öğesini ' nameof ' olarak dönüştür**' ü seçin: ![ ' gettype ' öğesini ' nameof ' öğesine dönüştür ve Visual Basic kod değişikliği gösterilen Visual Studio hızlı eylemlerin ve yeniden düzenlemeler menüsünün ekran görüntüsü.](media/convert-get-type.PNG)

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
