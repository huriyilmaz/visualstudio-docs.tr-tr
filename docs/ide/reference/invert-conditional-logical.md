---
title: Koşullu ifadeleri ve mantıksal işlemleri tersine çevirme
description: Hızlı Eylemler ve Yeniden Düzenleme menüsünü kullanarak koşullu ifadeyi veya koşullu AND/OR işlecini ters çevirebilirsiniz.
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
ms.openlocfilehash: 878ea8ec1d41421a9c9418eefba795c6f9fffd15e7f48127a7ff9292deac22de
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121372457"
---
# <a name="invert-conditional-expressions-and-conditional-andor-operators"></a>Koşullu ifadeleri ve koşullu AND/OR işleçlerini ters çevir

Bu yeniden düzenleme aşağıdakiler için geçerlidir:

- C#
- Visual Basic

**Ne:** Koşullu ifadeyi veya koşullu AND/OR işlecini ters çeviren bir özellik sağlar.

**Ne zaman:** Ters çevirseniz daha iyi anlaşılacak bir koşullu ifadeye veya koşullu AND/OR işlecine sahipsiniz.

**Neden:** Bir ifadeyi veya koşullu AND/OR işleci el ile ters çevirerek çok daha uzun sürebilir ve muhtemelen hatalara neden olabilir. Bu kod düzeltmesi, bu yeniden düzenlemeyi otomatik olarak yapmanıza yardımcı olur.

## <a name="invert-conditional-expressions-and-conditional-andor-operators-refactoring"></a>Koşullu ifadeleri ve koşullu AND/OR işleçlerini yeniden düzenlemeyi ters çevir

1. İmlecinizi koşullu ifadeye veya koşullu AND/OR işlecine yerleştirin.
2. **Ctrl tuşuna** + **basın.** Hızlı Eylemler **ve Yeniden Düzenleme menüsünü tetiklemek** için.
3. Koşullu **ters çevir'i** **veya '&&' öğesini '||' olarak değiştirin**

    ![Koşullu seçeneği ters çevir seçeneğinin ekran görüntüsü.](media/invert-conditional.png)

    ![ && 'i || ekran görüntüsü Seçeneği.](media/invert-logical-operator.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
- [.NET İpuçları için geliştirmeler](../csharp-developer-productivity.md)
