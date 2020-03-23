---
title: if deyimini tersine çevirme
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: a0419100cbc5fcd543eb250fa85cbfe2ebd1c97f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "65531584"
---
# <a name="invert-if-statement"></a>if deyimini tersine çevirme

Bu yeniden düzenleme aşağıdakiler için geçerlidir:

- C#
- Visual Basic

**Ne:** Kodun anlamını değiştirmeden bir `if` veya `if else` ifadeyi tersine çevirmenizi sağlar.

**Ne zaman:** Ters çevrildiğinde `if` `if else` daha iyi anlaşılacak bir ifadeniz veya ifadeniz olduğunda.

**Neden:** Bir `if` ifadenin `if else` veya ifadenin elle ters çevrilmesi çok daha uzun sürebilir ve büyük olasılıkla hatalara neden olabilir. Bu kod düzeltmesi, bu yeniden düzenlemeyi otomatik olarak yapmanıza yardımcı olur.

## <a name="invert-if-statement-refactoring"></a>İfade refactoring eğer ters

1. İmlecinizi bir `if` veya `if else` ifadeye yerleştirin.

    ![Eğer başka bir şey ters çevir](media/invert-if.png)

2. **Ctrl**+tuşuna**basın.** **Hızlı Eylemler ve Refactorings** menüsünü tetiklemek için.

    ![Eğer başka bir kod düzeltmesi tersine çevir](media/invert-if-codefix.png)

3. **Eğer Ters Çevir'i**seçin.

    ![Eğer başka bir sonuç ters çevir](media/invert-if-codefix-result.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
- [.NET Geliştiricileri için ipuçları](../csharp-developer-productivity.md)
