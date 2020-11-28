---
title: Switch deyimini switch ifadesine dönüştürme
description: Bir switch deyimini C# 8,0 anahtar ifadesine dönüştürmek için hızlı eylemler ve yeniden düzenlemeler menüsünü nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 06/19/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: add43010fcec04cbe12889672f561f22057efb8c
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2020
ms.locfileid: "96305517"
---
# <a name="convert-switch-statement-to-switch-expression"></a>Switch deyimini switch ifadesine dönüştürme

Bu yeniden düzenleme için geçerlidir:

- C#

**Ne:** [Switch deyimini](/dotnet/csharp/language-reference/keywords/switch) C# 8,0 [anahtar ifadesine](/dotnet/csharp/whats-new/csharp-8#switch-expressions)Dönüştür.

**Ne zaman:** Bir deyimi ifadeye dönüştürmek istiyorsunuz, `switch` `switch` tersi de geçerlidir. 

**Neden:** Yalnızca ifadeler kullanıyorsanız, bu yeniden düzenleme geleneksel deyimlerden kolay bir geçişe izin vermez `switch` .

## <a name="how-to"></a>Nasıl yapılır

1. Proje dosyanızda, ifadeler yeni bir C# 8,0 özelliği olduğundan, [dil sürümünü önizleme olarak ayarlayın](/dotnet/csharp/language-reference/configure-language-version#edit-the-project-file) `switch` .
2. İmlecinizi `switch` anahtar sözcüğe yerleştirip **CTRL** tuşuna basın + **.** **hızlı eylemleri ve yeniden düzenlemeler** menüsünü tetiklemek için.
3. **Switch deyimini Ifadeye Dönüştür**' ü seçin.

   ![Switch deyimini switch ifadesine dönüştürme](media/convert-switch-statement-to-switch-expression.png) 

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
