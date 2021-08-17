---
title: Geçici bir değişkeni değeriyle değiştirme
description: Geçici bir değişkeni kaldırmak ve bunun yerine değeriyle değiştirmek için Hızlı Eylemler ve Yeniden Düzenleme menüsünü kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 0d9a498cb8c6b6f8a52b590e6f080ff9e0d0dbcd742b916abc035648d921ce65
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121357290"
---
# <a name="inline-a-temporary-variable-refactoring"></a>Satır içi geçici değişken yeniden düzenlemesi

Bu yeniden düzenleme aşağıdakiler için geçerlidir:

- C#

- Visual Basic

**Ne:** Geçici bir değişkeni kaldırmanız ve bunun yerine değerini değiştirmenize olanak sağlar.

**Ne zaman:** Geçici değişkenin kullanımı, kodun daha zor an anlamalarını sağlar.

**Neden:** Geçici bir değişkenin kaldırılması, kodun okunmalarını kolaylaştırabilir.

## <a name="how-to"></a>Nasıl yapılır

1. Metin imlecini vurgulayın veya satır içine yerleştirerek geçici değişkenin içine girin:

   - C#:

       ![Vurgulanan kod - C #](media/inline-highlight-cs.png)

   - Visual Basic:

       ![Vurgulanan kod- Visual Basic](media/inline-highlight-vb.png)

2. Ardından, aşağıdakilerden birini yapın:

   - **Klavye**
      - **Ctrl tuşuna** + **basın.** hızlı eylemler **ve yeniden düzenleme menüsünü tetiklemek** için.
   - **Fare**
      - Koda sağ tıklayın ve Hızlı **Eylemler ve Yeniden Düzenleme menüsünü** seçin.

3. Önizleme **penceresi açılır penceresinde Satır** içi geçici değişken'i seçin.

   değişkeni kaldırılır ve kullanımları değişkenin değeriyle değiştirilir.

   - C#:

      ![Satır içi sonuç - C #](media/inline-result-cs.png)

   - Visual Basic:

      ![Satır içi sonuç - Visual Basic](media/inline-result-vb.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
