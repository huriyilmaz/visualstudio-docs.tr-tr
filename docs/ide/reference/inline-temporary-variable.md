---
title: Geçici bir değişkeni değeriyle değiştir
ms.date: 01/26/2018
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 8b758407dc5500630157050c10f881a6515e1216
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661008"
---
# <a name="inline-a-temporary-variable-refactoring"></a>Geçici bir değişken yeniden düzenleme

Bu yeniden düzenleme için geçerlidir:

- C#

- Visual Basic

**Ne:** Geçici bir değişkeni kaldırmanıza ve bunun yerine değeri ile değiştirmenize izin verir.

**Ne zaman:** Geçici değişkenin kullanımı, kodun anlaşılması daha zor hale getirir.

**Neden:** Geçici bir değişkenin kaldırılması kodu daha kolay okunabilir hale gelebilir.

## <a name="how-to"></a>Nasıl yapılır

1. Metin imlecini satır içine eklenecek geçici değişkenin içine vurgulayın veya yerleştirin:

   - C#:

       ![Vurgulanan kod-C#](media/inline-highlight-cs.png)

   - Visual Basic:

       ![Vurgulanan kod Visual Basic](media/inline-highlight-vb.png)

2. Sonra, aşağıdakilerden birini yapın:

   - **Klavyenizdeki**
      - **Ctrl** + tuşuna basın **.** **hızlı eylemleri ve yeniden düzenlemeler** menüsünü tetiklemek için.
   - **Tığında**
      - Koda sağ tıklayın ve **Hızlı Eylemler ve yeniden düzenlemeler** menüsünü seçin.

3. Önizleme penceresi açılır penceresinde **satır içi geçici değişken** ' i seçin.

   Değişken kaldırılır ve kullanımları değişkenin değerine göre değişir.

   - C#:

      ![Satır içi sonuç-C#](media/inline-result-cs.png)

   - Visual Basic:

      ![Satır içi sonuç-Visual Basic](media/inline-result-vb.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)