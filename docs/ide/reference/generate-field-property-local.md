---
title: Alan, özellik, yerel değişken Oluştur
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: b554aa5586150942c0fc7d7aeada9356a67029ca
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75595611"
---
# <a name="generate-a-field-property-or-local-variable-in-visual-studio"></a>Visual Studio 'da alan, özellik veya yerel değişken oluşturma

Bu kod üretimi için geçerlidir:

- C#

- Visual Basic

**Ne:** Önceden bildirilmemiş bir alan, özellik veya yerel için kodu hemen oluşturmanıza olanak sağlar.

**Ne zaman:** Yazarken yeni bir alan, özellik veya yerel bir özelliktir ve bunu otomatik olarak doğru bir şekilde bildirmek istediğinizde.

**Neden:** Bu özelliği kullanmadan önce alanı, özelliği veya yerel olarak bildirebilirsiniz, ancak bu özellik bildirimi ve otomatik olarak türünü oluşturur.

## <a name="how-to"></a>Nasıl yapılır

1. İmlecinizi kırmızı dalgalı çizgi olan çizgiye yerleştirin. Kırmızı dalgalı çizgi, henüz mevcut olmayan bir alanı, yerel veya özelliği gösterir.

   - C#:

       ![Vurgulanmış kod C #](media/field-highlight-cs.png)

   - Visual Basic:

       ![Vurgulanan kod VB](media/field-highlight-vb.png)

2. Sonra, aşağıdakilerden birini yapın:

   - **Klavye**
      - **CTRL**tuşuna basın + **.** **hızlı eylemleri ve yeniden düzenlemeler** menüsünü tetiklemek için.
   - **Fare**
      - Sağ tıklayın ve **Hızlı Eylemler ve yeniden düzenlemeler** menüsünü seçin.
      - Kırmızı dalgalı çizgi üzerine gelin ve ![ampul hatası](media/error-bulb.png) görüntülenen simge.
      - Sağ üst köşedeki ![ampul hatası](media/error-bulb.png) Sol kenar boşluğunda, metin imleci kırmızı dalgalı çizgi ile zaten varsa görüntülenen simge.

      ![Alan/özellik/yerel Önizleme Oluştur](media/field-preview-cs.png)

3. Açılan menüden oluşturma seçeneklerinden birini belirleyin.

   > [!TIP]
   > Seçiminizi yapmadan önce yapılacak [tüm değişiklikleri görmek için](../../ide/preview-changes.md) Önizleme penceresinin altındaki **Değişiklikleri Önizle** bağlantısını kullanın.

   Alanı, özelliği veya yerel, kullanımı tarafından gösterilen tür ile oluşturulur.

   - C#:

       ![Yöntem sonuç C oluştur #](media/field-result-cs.png)

   - Visual Basic:

       ![Yöntem sonucu oluştur VB](media/field-result-vb.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Kod oluşturma](../code-generation-in-visual-studio.md)
- [Değişiklikleri Önizleme](../../ide/preview-changes.md)
