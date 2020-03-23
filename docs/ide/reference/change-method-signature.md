---
title: Metot imzasını değiştirme
description: Yöntemin parametrelerinin sırasını kaldırın veya değiştirin. Yönteme sağ tıklayın, Hızlı Eylemler ve Yeniden Düzenleme'yi seçin ve İmzayı Değiştir'i seçin.
ms.date: 01/26/2018
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.remove
- vs.csharp.refactoring.reorder
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 97c03c798732b5d722b2dc49f3ec7ffa490b4f06
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "68711256"
---
# <a name="change-a-method-signature-refactoring"></a>Yöntem imza refactoring değiştirme

Bu yeniden düzenleme aşağıdakiler için geçerlidir:

- C#

- Visual Basic

**Ne:** Yöntemin parametrelerinin sırasını kaldırmanızı veya değiştirmenizi sağlar.

**Ne zaman:** Şu anda çeşitli konumlarda kullanılmakta olan bir yöntem parametresini taşımak veya kaldırmak istiyorsunuz.

**Neden:** Parametreleri el ile kaldırAbilir ve yeniden sipariş edebilir ve ardından bu yönteme yapılan tüm çağrıları bulabilir ve bunları tek tek değiştirebilirsiniz, ancak bu hatalara neden olabilir.  Bu yeniden düzenleme aracı görevi otomatik olarak gerçekleştirir.

## <a name="how-to"></a>Nasıl yapılır

1. Metin imlecini değiştirmek için yöntemin adının veya kullanımlarından birinin içine vurgulayın veya yerleştirin:

   - C#:

       ![Vurgulanan kod C #](media/changesignature-highlight-cs.png)

   - VB:

       ![Vurgulanan kod Visual Basic](media/changesignature-highlight-vb.png)

2. Ardından, aşağıdakilerden birini yapın:

   - **Klavye**
      - **Ctrl+R**tuşuna basın, sonra **Ctrl+V**tuşuna basın.  (Klavye kısayol'unuzun seçtiğiniz profile bağlı olarak farklı olabileceğini unutmayın.)
      - **Ctrl**+tuşuna**basın.** **Hızlı Eylemler ve Yeniden Çarpanlara Yönelikmenü'yü** tetiklemek ve Önizleme penceresinden **İmzayı Değiştir'i** seçin.
   - **Fare**
      - **Parametreleri Kaldır> > Yeniden Düzenleme'yi**seçin.
      - **Re >factor > Yeniden Düzenle parametrelerini**seçin.
      - Kodu sağ tıklatın, **Hızlı Eylemler ve Yeniden Faktörler** menüsünü seçin ve Önizleme penceresinden **İmzayı Değiştir'i** seçin.

3. Açılan **İmzayı Değiştir** iletişim kutusunda, yöntem imzasını değiştirmek için sağ taraftaki düğmeleri kullanabilirsiniz:

   ![İmza iletişim kutusunu değiştir](media/changesignature-dialog-cs.png)

   | Düğme | Açıklama
   | ------ | ---
   | **Yukarı/Aşağı** | Seçili parametreyi listeyi yukarı ve aşağı taşıma
   | **Kaldır** | Seçili parametreyi listeden kaldırma
   | **Geri yükleme** | Seçili, çapraz parametreyi listeye geri yükleme

   > [!TIP]
   > Önizleme **başvurusu değişiklikleri** onay kutusunu kullanarak [sonucun ne olacağını görün.](../../ide/preview-changes.md)

4. İşi bittiğinde, değişiklikleri yapmak için **Tamam** düğmesine basın.

   - C#:

      ![İmza sonucunu değiştir - C #](media/changesignature-result-cs.png)

   - Visual Basic:

      ![İmza sonucunu değiştir - Visual Basic](media/changesignature-result-vb.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
- [Değişiklikleri Önizleme](../../ide/preview-changes.md)