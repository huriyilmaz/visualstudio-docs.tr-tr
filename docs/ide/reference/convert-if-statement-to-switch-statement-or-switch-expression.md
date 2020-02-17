---
title: Deyim veya anahtar ifadesi için IF deyimi Dönüştür
ms.date: 02/12/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: cb0c06fe0493f973ea9cf0a566ffda45a49eeeff
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/15/2020
ms.locfileid: "77280784"
---
# <a name="convert-if-statement-to-switch-statement-or-switch-expression"></a>Deyim veya anahtar ifadesi için IF deyimi Dönüştür

Bu yeniden düzenleme için geçerlidir:

- C#

**Ne:** IF deyimini bir [switch deyimine](/dotnet/csharp/language-reference/keywords/switch) veya C# 8,0 [anahtar ifadesine](/dotnet/csharp/whats-new/csharp-8#switch-expressions)Dönüştür.

**Ne zaman:** `if` deyimini `switch` deyimine veya `switch` ifadesine dönüştürmek istiyorsunuz ve tam tersi de geçerlidir. 

**Neden:** `if` deyimi kullanıyorsanız, bu yeniden düzenleme `switch` deyimlere veya `switch` ifadelerine kolay bir geçişe olanak sağlar.

## <a name="how-to"></a>Nasıl yapılır

1. İmlecinizi `if` anahtar sözcüğüne yerleştirin.
2. **Ctrl**+tuşuna basın **.** **hızlı eylemleri ve yeniden düzenlemeler** menüsünü tetiklemek için.
3. **' Switch ' Ifadesine Dönüştür '** ü seçin.

   ![Deyim veya anahtar ifadesi için IF deyimi Dönüştür](media/convert-if-statement-to-switch-statement-or-switch-expression.png) 

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenleme](../refactoring-in-visual-studio.md)
