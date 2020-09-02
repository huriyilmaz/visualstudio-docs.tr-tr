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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65531584"
---
# <a name="invert-if-statement"></a>if deyimini tersine çevirme

Bu yeniden düzenleme için geçerlidir:

- C#
- Visual Basic

**Ne:** `if` Kodun anlamını değiştirmeden bir veya ifadesini ters çevirmenize olanak sağlar `if else` .

**Ne zaman:** `if` `if else` Ters çevrilme sırasında daha iyi anlaşılabilecek bir veya deyiminiz olduğunda.

**Neden:** `if` Or `if else` ifadesinin el ile tersine gelmesi çok daha uzun sürebilir ve muhtemelen hata verebilir. Bu kod çözümü, bu yeniden düzenlemeyi otomatik olarak yapmanıza yardımcı olur.

## <a name="invert-if-statement-refactoring"></a>İf deyiminizi yeniden düzenlemeyi ters çevir

1. İmlecinizi bir `if` or `if else` ifadesine yerleştirin.

    ![Değilse ters çevir](media/invert-if.png)

2. **CTRL**tuşuna basın + **.** **hızlı eylemleri ve yeniden düzenlemeler** menüsünü tetiklemek için.

    ![Değilse kod düzeltmesini ters çevir](media/invert-if-codefix.png)

3. **Ters çevir**' i seçin.

    ![Başka bir sonuç varsa ters çevir](media/invert-if-codefix-result.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
- [.NET geliştiricileri için ipuçları](../csharp-developer-productivity.md)
