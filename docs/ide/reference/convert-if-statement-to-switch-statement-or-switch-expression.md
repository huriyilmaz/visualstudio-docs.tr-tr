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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "79094152"
---
# <a name="convert-if-statement-to-switch-statement-or-switch-expression"></a>if deyimini switch deyimine veya switch ifadesine dönüştürme

Bu yeniden düzenleme için geçerlidir:

- C#

**Ne:** IF deyimini bir [switch deyimine](/dotnet/csharp/language-reference/keywords/switch) veya C# 8,0 [anahtar ifadesine](/dotnet/csharp/whats-new/csharp-8#switch-expressions)Dönüştür.

**Ne zaman:** Bir `if` deyimi ifadeye `switch` veya ifadeye dönüştürmek istiyorsunuz `switch` ve tam tersi de geçerlidir. 

**Neden:** Bir `if` deyim kullanıyorsanız, bu yeniden düzenleme `switch` deyimlere veya ifadelere kolay bir geçişe olanak sağlar `switch` .

## <a name="how-to"></a>Nasıl yapılır

1. İmlecinizi `if` anahtar sözcüğe yerleştirin.
2. **CTRL**tuşuna basın + **.** **hızlı eylemleri ve yeniden düzenlemeler** menüsünü tetiklemek için.
3. Aşağıdaki iki seçenekten seçim yapın: 

    **' Switch ' Ifadesine Dönüştür '** ü seçin.

   ![If ifadesini Switch ifadesine Dönüştür](media/convert-if-to-switch-statement.png) 

    **' Switch ' Ifadesine Dönüştür '** ü seçin. 

    ![IF deyimini anahtar ifadesine Dönüştür](media/convert-if-to-switch-expression.png) 

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
