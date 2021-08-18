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
ms.openlocfilehash: 018e3fd27753a33a763d716f17648e51b92dc52e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122101225"
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
