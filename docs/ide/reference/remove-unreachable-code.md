---
title: Erişilemeyen kodu yeniden düzenlemeyi kaldır
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: cd827870f07fb3161674d287d20f266942e61afe
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "79093985"
---
# <a name="remove-unreachable-code-refactoring"></a>Erişilemeyen kodu yeniden düzenlemeyi kaldır

Bu yeniden düzenleme için geçerlidir:

- C#

- Visual Basic

**Ne:** Hiçbir şekilde yürütülmeyecek kodu kaldırır.

**Ne zaman:** Programınızın bir kod parçacığı yolu yoktur ve bu kod parçacığı gereksiz hale getirir.

**Neden:** Gereksiz olan ve hiçbir şekilde Yürütülmeyen kodu kaldırarak okunabilirliği ve bakımlılığını iyileştirin.

## <a name="how-to"></a>Nasıl yapılır

1. İmlecinizi, erişilemeyen, erişilebilir olmayan kodun herhangi bir yerine yerleştirin:

![Erişilebilir erişilemeyen kod](media/unreachablecode-faded-cs.png)

1. Sonra, aşağıdakilerden birini yapın:

   - **Klavye**
      - **CTRL**tuşuna basın + **.** **hızlı eylemleri ve yeniden düzenlemeler** menüsünü tetiklemek ve Önizleme penceresi açılır penceresinde **ulaşılamaz kodu kaldır** ' ı seçin.
   - **Fare**
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
