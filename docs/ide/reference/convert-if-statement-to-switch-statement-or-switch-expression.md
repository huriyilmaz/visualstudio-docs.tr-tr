---
title: İf deyimini deyim veya ifadeye Dönüştür
description: Bir IF deyimini switch deyimine veya C# 8,0 anahtar ifadesine dönüştürmek için hızlı eylemler ve yeniden düzenlemeler menüsünü nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 0d857338eb1c9b5bb66ccb89e20e6f892944d608
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99936837"
---
# <a name="convert-if-statement-to-switch-statement-or-switch-expression"></a>if deyimini switch deyimine veya switch ifadesine dönüştürme

Bu yeniden düzenleme için geçerlidir:

- C#

**Ne:** IF deyimini bir [switch deyimine](/dotnet/csharp/language-reference/keywords/switch) veya C# 8,0 [anahtar ifadesine](/dotnet/csharp/whats-new/csharp-8#switch-expressions)Dönüştür.

**Ne zaman:** Bir `if` deyimi ifadeye `switch` veya ifadeye dönüştürmek istiyorsunuz `switch` ve tam tersi de geçerlidir.

**Neden:** Bir `if` deyim kullanıyorsanız, bu yeniden düzenleme `switch` deyimlere veya ifadelere kolay bir geçişe olanak sağlar `switch` .

## <a name="how-to"></a>Nasıl yapılır

1. İmlecinizi `if` anahtar sözcüğe yerleştirin.
2. **CTRL** tuşuna basın + **.** **hızlı eylemleri ve yeniden düzenlemeler** menüsünü tetiklemek için.
3. Aşağıdaki iki seçenekten seçim yapın:

    **' Switch ' Ifadesine Dönüştür '** ü seçin.

   ![If ifadesini Switch ifadesine Dönüştür](media/convert-if-to-switch-statement.png)

    **' Switch ' Ifadesine Dönüştür '** ü seçin.

    ![IF deyimini anahtar ifadesine Dönüştür](media/convert-if-to-switch-expression.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
