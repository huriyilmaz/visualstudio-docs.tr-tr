---
title: Erişilemeyen kodu yeniden düzenlemeyi kaldır
ms.date: 01/26/2018
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 1e5bdab773cf70963e1d0f485a7779e57084c8a0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655599"
---
# <a name="remove-unreachable-code-refactoring"></a>Erişilemeyen kodu yeniden düzenlemeyi kaldır

Bu yeniden düzenleme için geçerlidir:

- C#

**Ne:** Hiçbir şekilde yürütülmeyecek kodu kaldırır.

**Ne zaman:** Programınızın bir kod parçacığı yolu yoktur ve bu kod parçacığı gereksiz hale getirir.

**Neden:** Gereksiz olan ve hiçbir şekilde Yürütülmeyen kodu kaldırarak okunabilirliği ve bakımlılığını iyileştirin.

## <a name="how-to"></a>Nasıl yapılır

1. İmlecinizi, erişilemeyen, erişilebilir olmayan kodun herhangi bir yerine yerleştirin:

![Erişilebilir erişilemeyen kod](media/unreachablecode-faded-cs.png)

1. Sonra, aşağıdakilerden birini yapın:

   - **Klavyenizdeki**
      - **Ctrl** + tuşuna basın **.** **hızlı eylemleri ve yeniden düzenlemeler** menüsünü tetiklemek ve Önizleme penceresi açılır penceresinde **ulaşılamaz kodu kaldır** ' ı seçin.
   - **Tığında**
      - Koda sağ tıklayın, **Hızlı Eylemler ve yeniden düzenlemeler** menüsünü seçip Önizleme penceresi açılır penceresinde **ulaşılamaz kodu kaldır** ' ı seçin.

1. Değişikliğin ne kadar memnunsanız, **ENTER** tuşuna basın veya menüdeki değişikliğe tıklayın ve değişiklikler uygulanır.

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