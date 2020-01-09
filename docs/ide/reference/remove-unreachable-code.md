---
title: Erişilemeyen kodları yeniden düzenleme Kaldır
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 62002e78513ecb6ebaefd8130255471d6ba93d0c
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75565493"
---
# <a name="remove-unreachable-code-refactoring"></a>Erişilemeyen kodları yeniden düzenleme Kaldır

Bu yeniden düzenleme için geçerlidir:

- C#

**Ne:** hiçbir zaman yürütülecek kodu kaldırır.

**Ne zaman:** programınızda Bu kod parçacığı gereksiz yapmadan bir kod parçacığı için yol yok.

**Neden:** geliştirmek okunabilirlik ve sürdürülebilirliği gereksiz kod kaldırarak ve hiçbir zaman yürütülür.

## <a name="how-to"></a>Nasıl Yapılır Konuları

1. İmlecinizi, erişilemeyen soluk çıkış kodu herhangi bir yere yerleştirebilirsiniz:

![Soluk erişilemeyen kod](media/unreachablecode-faded-cs.png)

1. Ardından, aşağıdakilerden birini yapın:

   - **Klavye**
      - Tuşuna **Ctrl**+ **.** Tetikleyici için **hızlı Eylemler ve yeniden düzenlemeler** menü ve select **erişilemeyen kodları kaldırma** gelen önizleme penceresi açılır.
   - **Fare**
      - Kod sağ tıklayın, **hızlı Eylemler ve yeniden düzenlemeler** menü ve select **erişilemeyen kodları kaldırma** gelen önizleme penceresi açılır.

1. Değişiklik ile tamamladığınızda basın **Enter** veya düzeltmeyi menüsünde tıklatın ve değişiklikler uygulanır.

Örnek:

```csharp
// Before
private void Method()
{
    throw new Exception(nameof(Method));
    Console.WriteLine($"Exception for method {nameof(Method)}");
}

// Remove unreachable code

// After
private void Method()
{
    throw new Exception(nameof(Method));
}
```

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
- [Değişiklikleri Önizleme](../../ide/preview-changes.md)
