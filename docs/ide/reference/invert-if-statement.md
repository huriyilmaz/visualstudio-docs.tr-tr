---
title: if deyimini tersine çevirme
description: Kodun anlamını değiştirmeden bir if veya If Else ifadesini tersine çevirmek için hızlı eylemler ve yeniden düzenlemeler menüsünü nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jmartens
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: d1dfb73749774e5ae9409b7f00a78bd59008d271
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628761"
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
- [.net geliştiricileri için İpuçları](../csharp-developer-productivity.md)
