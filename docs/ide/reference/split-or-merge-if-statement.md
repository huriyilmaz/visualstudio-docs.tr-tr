---
title: Birleştir veya ayır if deyimleri
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
ms.openlocfilehash: a3b42f83faacda6be34b282150cf4fb4c0f379f1
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79093695"
---
# <a name="split-or-merge-if-statements"></a>Birleştir veya ayır if deyimleri

Bu yeniden düzenleme aşağıdakiler için geçerlidir:

- C#

- Visual Basic

**Ne: Ne:** **What:** Bölme veya birleştirme [eğer](/dotnet/csharp/language-reference/keywords/if-else) ifadeleri.

**Ne zaman:** Veya `if` `&&` `||` işleçleri iç içe olan bir `if` deyime kullanan bir `if` deyimi `if` bölmek veya bir deyimle dış deyimle birleştirmek istiyorsunuz.

**Neden:** Bu bir stil tercihi meselesi.  

## <a name="how-to"></a>Nasıl yapılır

İfadeyi `if` bölmek isterseniz:

1. İmlecinizi ekstreye `if` `&&` yerleştirin `||` veya operatör tarafından.

2. **Ctrl**+tuşuna**basın.** **Hızlı Eylemler ve Refactorings** menüsünü tetiklemek için.

    ![Bölünmüş If Deyimi](../media/split-if-statement.png)

3. **İfadeler iç içe yse Bölün'i**seçin.

    ![İfade Tamamlandıysa Böl](../media/split-if-statement-complete.png)

İç `if` deyimi dış `if` ifadeyle birleştirmek istiyorsanız: 

1. İmlecinizi iç `if` anahtar kelimeye yerleştirin.

2. **Ctrl**+tuşuna**basın.** **Hızlı Eylemler ve Refactorings** menüsünü tetiklemek için.

    ![If Bildirimini Birleştir](../media/merge-if-statement.png)

3. **Dışife ile Birleştir'i**seçin.

    ![İfade Tamamlandıysa Birleştir](../media/merge-if-statement-complete.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)