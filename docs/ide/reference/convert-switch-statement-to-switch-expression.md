---
title: Switch deyimini switch ifadesine dönüştürme
ms.date: 06/19/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: cc13cffe8352d9fb57f5bb991c3af615eddb2a14
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "68740051"
---
# <a name="convert-switch-statement-to-switch-expression"></a>Switch deyimini switch ifadesine dönüştürme

Bu yeniden düzenleme aşağıdakiler için geçerlidir:

- C#

**Ne:** Bir [anahtar deyimini](/dotnet/csharp/language-reference/keywords/switch) C# 8.0 [anahtar ifadesine](/dotnet/csharp/whats-new/csharp-8#switch-expressions)dönüştürün.

**Ne zaman:** Bir `switch` deyimi bir `switch` ifadeye dönüştürmek istiyorsunuz ve bunun tersi de var. 

**Neden:** Yalnızca ifadeler kullanıyorsanız, bu yeniden düzenleme geleneksel `switch` ifadelerden kolay bir geçiş sağlar.

## <a name="how-to"></a>Nasıl yapılır

1. Proje dosyanızda, ifadeler yeni bir `switch` C# 8.0 özelliği olduğundan [dil sürümünü önizlemeye ayarlayın.](/dotnet/csharp/language-reference/configure-language-version#edit-the-project-file)
2. İmlecinizi anahtar `switch` kelimeye yerleştirin ve **Ctrl**+tuşuna**basın.** **Hızlı Eylemler ve Refactorings** menüsünü tetiklemek için.
3. **Geçiş ifadesini ifadeye dönüştür'ü**seçin.

   ![Switch deyimini switch ifadesine dönüştürme](media/convert-switch-statement-to-switch-expression.png) 

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
