---
title: Değişken bildirimini başvuruya yakın taşıma
description: Değişken bildirimlerini kullanımlarına daha yakın bir yere taşımak için Hızlı Eylemler ve Yeniden Düzenleme menüsünü kullanmayı öğrenin.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122101082"
---
# <a name="move-declaration-near-reference-refactoring"></a>Bildirimi başvuru yeniden düzenlemeye yakın taşıma

Bu yeniden düzenleme aşağıdakiler için geçerlidir:

- C#

- Visual Basic

**Ne:** Değişken bildirimlerini kullanımlarına daha yakın bir yere taşımaya olanak sağlar.

**Ne zaman:** Daha dar bir kapsamda yer alan değişken bildirimlerine sahipsiniz.

**Neden:** Olduğu gibi bırakabilirsiniz, ancak bu okunabilirlik sorunlarına veya bilgilerin gizlemeye neden olabilir. Bu, okunabilirliği geliştirmek için yeniden düzenleme yapma şansıdır.

## <a name="how-to"></a>Nasıl yapılır

1. İmlecinizi değişken bildirimine yerleştirin.

1. Ardından, aşağıdakilerden birini yapın:

   - **Klavye**
      - **Ctrl tuşuna** + **basın.** Hızlı Eylemler ve **Yeniden Düzenleme menüsünü tetiklemek için Önizleme** penceresi açılır penceresinde **Bildirimi** başvuruya yakın taşı'ya tıklayın.
   - **Fare**
      - Koda sağ tıklayın, Hızlı Eylemler ve **Yeniden** Düzenleme menüsünü seçin ve Önizleme **penceresi** açılır penceresinde Bildirimi başvuruya yakın taşı'yı seçin.

1. Değişiklik sizi memnun edecekse **Enter** tuşuna basın veya menüde düzeltmeye tıklayın; değişiklikler işlendi.

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
