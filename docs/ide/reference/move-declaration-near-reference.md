---
title: Değişken bildirimini başvuru yakınına taşı
ms.date: 01/26/2018
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: c0a82b48a556e26866393661d4b87836db765abb
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666495"
---
# <a name="move-declaration-near-reference-refactoring"></a>Bildirimi başvuru yeniden düzenlemesi yakınında taşı

Bu yeniden düzenleme için geçerlidir:

- C#

**Ne:** Değişken bildirimlerini kullanımlarına yaklaştırmanızı sağlar.

**Ne zaman:** Daha dar bir kapsamda olabilecek değişken bildirimlerinizde yer vardır.

**Neden:** Bunu olduğu gibi bırakabilirsiniz, ancak bu durum okunabilirlik sorunları veya bilgi gizlenmesine neden olabilir. Bu, okunabilirliği artırmak için yeniden düzenleme şansı sağlar.

## <a name="how-to"></a>Nasıl yapılır

1. İmlecinizi değişken bildirimine yerleştirin.

1. Sonra, aşağıdakilerden birini yapın:

   - **Klavyenizdeki**
      - **Ctrl** + tuşuna basın **.** **hızlı eylemleri ve yeniden düzenlemeler** menüsünü tetiklemek ve Önizleme penceresi açılır penceresinde **bildirimi başvuru yakınına taşı** ' yı seçin.
   - **Tığında**
      - Koda sağ tıklayın, **Hızlı Eylemler ve yeniden düzenlemeler** menüsünü seçip Önizleme penceresi açılır penceresinde **bildirimi başvuru yakınına taşı** ' yı seçin.

1. Değişikliğin ne kadar memnunsanız, **ENTER** tuşuna basın veya menüdeki değişikliğe tıklayın ve değişiklikler uygulanır.

Örnek:

```csharp
// Before
int x;
if (condition)
{
    x = 1;
    Console.WriteLine(x);
}

// Move declaration near reference

// After
if (condition)
{
    int x = 1;
    Console.WriteLine(x);
}
```

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
- [Değişiklikleri Önizleme](../../ide/preview-changes.md)