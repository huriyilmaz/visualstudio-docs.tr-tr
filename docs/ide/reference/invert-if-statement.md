---
title: if deyimini tersine çevirme
description: Kodun anlamını değiştirmeden bir if veya If Else ifadesini tersine çevirmek için hızlı eylemler ve yeniden düzenlemeler menüsünü nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 71b3a11e053b6a600d0b33db7c52a91c4950bf5b
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2020
ms.locfileid: "96616986"
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

2. **CTRL** tuşuna basın + **.** **hızlı eylemleri ve yeniden düzenlemeler** menüsünü tetiklemek için.

    ![Değilse kod düzeltmesini ters çevir](media/invert-if-codefix.png)

3. **Ters çevir**' i seçin.

    ![Başka bir sonuç varsa ters çevir](media/invert-if-codefix-result.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
- [.NET geliştiricileri için ipuçları](../csharp-developer-productivity.md)
