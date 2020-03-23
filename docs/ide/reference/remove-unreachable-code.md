---
title: Erişilemene bilen kod yeniden düzenlemeyi kaldırma
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79093985"
---
# <a name="remove-unreachable-code-refactoring"></a>Erişilemene bilen kod yeniden düzenlemeyi kaldırma

Bu yeniden düzenleme aşağıdakiler için geçerlidir:

- C#

- Visual Basic

**Ne:** Asla yürütülmeyecek kodu kaldırır.

**Ne zaman:** Programınızın bir kod parçacığına giden yolu yoktur ve bu da kod parçacıkını gereksiz kılar.

**Neden:** Gereksiz olan ve hiçbir zaman yürütülmeyecek kodu kaldırarak okunabilirliği ve bakımı geliştirin.

## <a name="how-to"></a>Nasıl yapılır

1. İmlecinizi erişilenebilen soluk çıkış koduna yerleştirin:

![Soluk erişilemez kod](media/unreachablecode-faded-cs.png)

1. Ardından, aşağıdakilerden birini yapın:

   - **Klavye**
      - **Ctrl**+tuşuna**basın.** **Hızlı Eylemler ve Yeniden Faktörler** menüsünü tetiklemek ve Önizleme penceresinden **erişilemeyen kodu kaldır'ı** seçin.
   - **Fare**
      - Kodu sağ tıklatın, **Hızlı Eylemler ve Yeniden Faktörler** menüsünü seçin ve Önizleme penceresi açılır penceresinden **erişilemeyen kodu kaldır'ı** seçin.

1. Değişiklikten memnun olduğunuzda, menüdeki düzeltmeyi **Girin'e** veya düzeltmeye tıklayın ve değişiklikler işlenir.

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
