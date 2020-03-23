---
title: if deyimini switch deyimine veya switch ifadesine dönüştürme
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 93ad96809c77d5644b13e6221a41f0b182fb448f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094152"
---
# <a name="convert-if-statement-to-switch-statement-or-switch-expression"></a>if deyimini switch deyimine veya switch ifadesine dönüştürme

Bu yeniden düzenleme aşağıdakiler için geçerlidir:

- C#

**Ne:** If deyimini bir [anahtar deyimine](/dotnet/csharp/language-reference/keywords/switch) veya C# 8.0 [anahtar ifadesine](/dotnet/csharp/whats-new/csharp-8#switch-expressions)dönüştürün.

**Ne zaman:** Bir `if` deyimi bir `switch` deyime veya `switch` ifadeye dönüştürmek istiyorsunuz ve bunun tersi de var. 

**Neden:** Bir `if` deyim kullanıyorsanız, bu yeniden düzenleme deyimlere `switch` veya `switch` ifadelere kolay bir geçiş sağlar.

## <a name="how-to"></a>Nasıl yapılır

1. İmlecinizi anahtar `if` kelimeye yerleştirin.
2. **Ctrl**+tuşuna**basın.** **Hızlı Eylemler ve Refactorings** menüsünü tetiklemek için.
3. Aşağıdaki iki seçenek arasından seçim: 

    **'Anahtarla' deyimine Dönüştür'ü**seçin.

   !["Geçiş deyimi" ifadesini dönüştürün](media/convert-if-to-switch-statement.png) 

    **'Anahtarla' ifadesine Dönüştür'ü**seçin. 

    ![İfadeyi değiştirmek için if deyimini dönüştürme](media/convert-if-to-switch-expression.png) 

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
