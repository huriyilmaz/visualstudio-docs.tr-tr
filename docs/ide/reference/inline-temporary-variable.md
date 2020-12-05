---
title: Geçici bir değişkeni değeriyle değiştir
description: Geçici bir değişkeni kaldırmak ve bunun yerine değeri ile değiştirmek için hızlı eylemler ve yeniden düzenlemeler menüsünü nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: d24c63bdc1908ecc15c206faeda3e9de511f8f9b
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2020
ms.locfileid: "96617415"
---
# <a name="inline-a-temporary-variable-refactoring"></a>Geçici bir değişken yeniden düzenleme

Bu yeniden düzenleme için geçerlidir:

- C#

- Visual Basic

**Ne:** Geçici bir değişkeni kaldırmanıza ve bunun yerine değeri ile değiştirmenize izin verir.

**Ne zaman:** Geçici değişkenin kullanımı, kodun anlaşılması daha zor hale getirir.

**Neden:** Geçici bir değişkenin kaldırılması kodu daha kolay okunabilir hale gelebilir.

## <a name="how-to"></a>Nasıl yapılır

1. Metin imlecini satır içine eklenecek geçici değişkenin içine vurgulayın veya yerleştirin:

   - C#:

       ![Vurgulanan kod-C #](media/inline-highlight-cs.png)

   - Visual Basic:

       ![Vurgulanan kod Visual Basic](media/inline-highlight-vb.png)

2. Sonra, aşağıdakilerden birini yapın:

   - **Klavye**
      - **CTRL** tuşuna basın + **.** **hızlı eylemleri ve yeniden düzenlemeler** menüsünü tetiklemek için.
   - **Fare**
      - Koda sağ tıklayın ve **Hızlı Eylemler ve yeniden düzenlemeler** menüsünü seçin.

3. Önizleme penceresi açılır penceresinde **satır içi geçici değişken** ' i seçin.

   Değişken kaldırılır ve kullanımları değişkenin değerine göre değişir.

   - C#:

      ![Satır içi sonuç-C #](media/inline-result-cs.png)

   - Visual Basic:

      ![Satır içi sonuç-Visual Basic](media/inline-result-vb.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
