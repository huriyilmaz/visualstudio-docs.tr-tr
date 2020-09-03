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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68740051"
---
# <a name="convert-switch-statement-to-switch-expression"></a>Switch deyimini switch ifadesine dönüştürme

Bu yeniden düzenleme için geçerlidir:

- C#

**Ne:** [Switch deyimini](/dotnet/csharp/language-reference/keywords/switch) C# 8,0 [anahtar ifadesine](/dotnet/csharp/whats-new/csharp-8#switch-expressions)Dönüştür.

**Ne zaman:** Bir deyimi ifadeye dönüştürmek istiyorsunuz, `switch` `switch` tersi de geçerlidir. 

**Neden:** Yalnızca ifadeler kullanıyorsanız, bu yeniden düzenleme geleneksel deyimlerden kolay bir geçişe izin vermez `switch` .

## <a name="how-to"></a>Nasıl yapılır

1. Proje dosyanızda, ifadeler yeni bir C# 8,0 özelliği olduğundan, [dil sürümünü önizleme olarak ayarlayın](/dotnet/csharp/language-reference/configure-language-version#edit-the-project-file) `switch` .
2. İmlecinizi `switch` anahtar sözcüğe yerleştirip **CTRL**tuşuna basın + **.** **hızlı eylemleri ve yeniden düzenlemeler** menüsünü tetiklemek için.
3. **Switch deyimini Ifadeye Dönüştür**' ü seçin.

   ![Switch deyimini switch ifadesine dönüştürme](media/convert-switch-statement-to-switch-expression.png) 

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
