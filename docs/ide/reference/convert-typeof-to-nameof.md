---
title: typeof ifadesini nameof ifadesine dönüştürme
description: Visual Studio'de Hızlı Eylemler ve Yeniden Düzenleme menüsünü kullanarak C# içinde typeof ve GetType'i Visual Basic.
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
ms.openlocfilehash: d37ae59d34968f91c95624784ce647831ef51804c4d67e8ad278472cacc1208f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121429948"
---
# <a name="convert-typeof-to-nameof"></a>Dönüştür `typeof``nameof`

Bu yeniden düzenleme aşağıdakiler için geçerlidir:

- C#
- Visual Basic

**Ne:** C# içinde bir örneğini olarak, bir örneğini ise `typeof(<QualifiedType>).Name` `nameof(<QualifiedType>)` 'ye `GetType(<QualifiedType>).Name` `NameOf(<QualifiedType>)` dönüştürmenizi Visual Basic.

**Ne zaman:**  tüm örnekleri `typeof(<QualifiedType>).Name` burada `someType` genel bir tür değil. Bu dışlama gereklidir çünkü bu durum ile aynı dize değerini `nameof(<QualifiedType>)` döndürür. Aynı durum, örnek için Visual Basic olur.

**Neden:** yerine adını kullanmak, bir nesneyi almakla ilgili yansımayı önler ve `nameof` `type` daha `type` pragmatik bir yazma yolu olur.

## <a name="how-to"></a>Nasıl yapılır

1. İmlecinizi `typeof(<QualifiedType>).Name` C# örneğinin veya `GetType(<QualifiedType>).Name` Visual Basic.

2. **Ctrl tuşuna** + **basın.** hızlı eylemler **ve yeniden düzenleme menüsünü tetiklemek** için.

3. Aşağıdaki seçeneklerden birini belirleyin:

    - C#
      <br>**'typeof' türünü 'nameof'** olarak dönüştür seçeneğini belirleyin: Visual Studio 'typeof' öğesini 'nameof' olarak dönüştür seçeneğinin seçili olduğu ve C# kod değişikliklerinin gösterildiği Hızlı Eylemler ve Yeniden Düzenleme menüsünün ekran ![ görüntüsü.](media/convert-type-of.PNG)

    - Visual Basic
      <br>**'GetType' öğesini 'NameOf'** olarak dönüştür seçeneğini belirleyin: 'GetType' öğesini 'NameOf' olarak dönüştür seçeneğinin seçili olduğu Visual Studio Hızlı Eylemler ve Yeniden Düzenleme menüsünün ekran görüntüsü Visual Basic kod değişiklikleri ![ gösteriliyor.](media/convert-get-type.PNG)

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
