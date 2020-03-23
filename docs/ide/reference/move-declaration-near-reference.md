---
title: Değişken bildirimini başvuruya yakın taşıma
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
ms.openlocfilehash: 1339f4a9d151ef41d9a35c5aac0a96f220a297b3
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79093998"
---
# <a name="move-declaration-near-reference-refactoring"></a>Bildirgeyi referans refactoring'e yaklaştır

Bu yeniden düzenleme aşağıdakiler için geçerlidir:

- C#

- Visual Basic

**Ne:** Değişken bildirimleri kullanıma daha yakın taşımanızı sağlar.

**Ne zaman:** Daha dar bir kapsamda olabilecek değişken bildirimleriniz vardır.

**Neden:** Olduğu gibi bırakabilirsiniz, ancak bu okunabilirlik sorunları veya bilgi gizleme neden olabilir. Bu okunabilirliği artırmak için yeniden faktör için bir şanstır.

## <a name="how-to"></a>Nasıl yapılır

1. İmlecinizi değişken bildirimine yerleştirin.

1. Ardından, aşağıdakilerden birini yapın:

   - **Klavye**
      - **Ctrl**+tuşuna**basın.** **Hızlı Eylemler ve Yeniden Çarpanlara Yönelikler** menüsünü tetiklemek ve Önizleme penceresinden **başvuruya yakın taşı bildirimini** seçin.
   - **Fare**
      - Kodu sağ tıklatın, **Hızlı Eylemler ve Yeniden Faktörler** menüsünü seçin ve Önizleme penceresi açılır penceresinden **başvuruya yakın bildirimi taşı'yı** seçin.

1. Değişiklikten memnun olduğunuzda, menüdeki düzeltmeyi **Girin'e** veya düzeltmeye tıklayın ve değişiklikler işlenir.

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
