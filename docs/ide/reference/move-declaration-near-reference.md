---
title: Değişken bildirimini başvuru yakınına taşı
description: Değişken bildirimlerini kullanımlarına yaklaştırmak için hızlı eylemler ve yeniden düzenlemeler menüsünü nasıl kullanacağınızı öğrenin.
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
ms.openlocfilehash: 81d87f80a5cc9ab7d228c808045afd6d891b5d1f
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628718"
---
# <a name="move-declaration-near-reference-refactoring"></a>Bildirimi başvuru yeniden düzenlemesi yakınında taşı

Bu yeniden düzenleme için geçerlidir:

- C#

- Visual Basic

**Ne:** Değişken bildirimlerini kullanımlarına yaklaştırmanızı sağlar.

**Ne zaman:** Daha dar bir kapsamda olabilecek değişken bildirimlerinizde yer vardır.

**Neden:** Bunu olduğu gibi bırakabilirsiniz, ancak bu durum okunabilirlik sorunları veya bilgi gizlenmesine neden olabilir. Bu, okunabilirliği artırmak için yeniden düzenleme şansı sağlar.

## <a name="how-to"></a>Nasıl yapılır

1. İmlecinizi değişken bildirimine yerleştirin.

1. Sonra, aşağıdakilerden birini yapın:

   - **Klavye**
      - **CTRL** tuşuna basın + **.** **hızlı eylemleri ve yeniden düzenlemeler** menüsünü tetiklemek ve Önizleme penceresi açılır penceresinde **bildirimi başvuru yakınına taşı** ' yı seçin.
   - **Fare**
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
