---
title: Erişilemeyen kodu yeniden düzenlemeyi kaldır
description: Hiçbir şey yürütülemeyecek kodu kaldırmak için hızlı eylemler ve yeniden düzenlemeler menüsünü nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 66ea34ff9cf8ba60775d12da001d49b58747d1c6
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122117208"
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
      - **CTRL** tuşuna basın + **.** **hızlı eylemleri ve yeniden düzenlemeler** menüsünü tetiklemek ve Önizleme penceresi açılır penceresinde **ulaşılamaz kodu kaldır** ' ı seçin.
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
