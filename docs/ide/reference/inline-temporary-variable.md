---
title: Geçici bir değişkeni değeriyle değiştirme
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
ms.openlocfilehash: 8f0199436f5f9b1013a4c49cfb5909e760c73dcc
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75568873"
---
# <a name="inline-a-temporary-variable-refactoring"></a>Geçici değişken refactoring inline

Bu yeniden düzenleme aşağıdakiler için geçerlidir:

- C#

- Visual Basic

**Ne:** Geçici bir değişkeni kaldırmanızı ve bunun yerine değeriyle değiştirmenizi sağlar.

**Ne zaman:** Geçici değişkenin kullanımı kodun anlaşılmasını zorlaştırır.

**Neden:** Geçici bir değişkenin kaldırılması kodun okunmasını kolaylaştırabilir.

## <a name="how-to"></a>Nasıl yapılır

1. Metin imlecini geçici değişkenin içine çizgili olarak vurgulayın veya yerleştirin:

   - C#:

       ![Vurgulanan kod - C #](media/inline-highlight-cs.png)

   - Visual Basic:

       ![Vurgulanan kod- Visual Basic](media/inline-highlight-vb.png)

2. Ardından, aşağıdakilerden birini yapın:

   - **Klavye**
      - **Ctrl**+tuşuna**basın.** **Hızlı Eylemler ve Refactorings** menüsünü tetiklemek için.
   - **Fare**
      - Kodu sağ tıklatın ve **Hızlı Eylemler ve Refactorings** menüsünü seçin.

3. Önizleme penceresi açılır penceresinden **Satır Çizgisi geçici değişkenini** seçin.

   Değişken kaldırılır ve kullanımları değişkenin değeri ile değiştirilir.

   - C#:

      ![Satır içi sonuç - C #](media/inline-result-cs.png)

   - Visual Basic:

      ![Satır içi sonuç - Visual Basic](media/inline-result-vb.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
