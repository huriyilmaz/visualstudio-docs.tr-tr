---
title: Birleştir veya ayır if deyimleri
description: İf deyimlerini ayırmak veya birleştirmek için hızlı eylemler ve yeniden düzenlemeler menüsünü nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 9d34aa066d84deeaf4ac16f683822d539b0d1357
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122117078"
---
# <a name="split-or-merge-if-statements"></a>Birleştir veya ayır if deyimleri

Bu yeniden düzenleme için geçerlidir:

- C#

- Visual Basic

**Nedir** **: or** [IF](/dotnet/csharp/language-reference/keywords/if-else) deyimleri Böl veya birleştir.

**Ne zaman:** `if` OR işleçlerini kullanan bir ifadeyi `&&` `||` iç içe geçmiş bir `if` ifadeye bölmek veya bir ifadeyi bir dış ifadesiyle birleştirmek istiyorsunuz `if` `if` .

**Neden:** Stil tercihlerinin bir önemi vardır.  

## <a name="how-to"></a>Nasıl yapılır

İfadeyi ayırmak istiyorsanız `if` :

1. İmlecinizi `if` ifadeye `&&` or `||` işlecine koyun.

2. **CTRL** tuşuna basın + **.** **hızlı eylemleri ve yeniden düzenlemeler** menüsünü tetiklemek için.

    ![If Ifadesini Böl](../media/split-if-statement.png)

3. **İç içe geçmiş deyimlerine Böl**' ü seçin.

    ![Ekstre tamamlanarak Böl](../media/split-if-statement-complete.png)

İç `if` ifadeyi dış ifadesiyle birleştirmek istiyorsanız `if` : 

1. İmlecinizi iç `if` anahtar sözcüğe yerleştirin.

2. **CTRL** tuşuna basın + **.** **hızlı eylemleri ve yeniden düzenlemeler** menüsünü tetiklemek için.

    ![If Ifadesini Birleştir](../media/merge-if-statement.png)

3. **Outer If Ifadesiyle Birleştir**' i seçin.

    ![Deyimden sonra birleştir](../media/merge-if-statement-complete.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)