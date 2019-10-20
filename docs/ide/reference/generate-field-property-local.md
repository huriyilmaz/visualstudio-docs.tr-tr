---
title: Alan, özellik, yerel değişken Oluştur
ms.date: 01/26/2018
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 626138341e398e67ff41ea116729dd349a1bb044
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660022"
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

       ![Vurgulanan kodC#](media/field-highlight-cs.png)

   - Visual Basic:

       ![Vurgulanan kod VB](media/field-highlight-vb.png)

2. Sonra, aşağıdakilerden birini yapın:

   - **Klavyenizdeki**
      - **Ctrl** + tuşuna basın **.** **hızlı eylemleri ve yeniden düzenlemeler** menüsünü tetiklemek için.
   - **Tığında**
      - Sağ tıklayın ve **Hızlı Eylemler ve yeniden düzenlemeler** menüsünü seçin.
      - Kırmızı dalgalı çizgi üzerine gelin ve ![ampul hatası](media/error-bulb.png) görüntülenen simge.
      - &nbsp; ![ampul hatası](media/error-bulb.png) Sol kenar boşluğunda, metin imleci kırmızı dalgalı çizgi ile zaten varsa görüntülenen simge.

      ![Alan/özellik/yerel Önizleme Oluştur](media/field-preview-cs.png)

3. Açılan menüden oluşturma seçeneklerinden birini belirleyin.

   > [!TIP]
   > Seçiminizi yapmadan önce yapılacak [tüm değişiklikleri görmek için](../../ide/preview-changes.md) Önizleme penceresinin altındaki **Değişiklikleri Önizle** bağlantısını kullanın.

   Alanı, özelliği veya yerel, kullanımı tarafından gösterilen tür ile oluşturulur.

   - C#:

       ![Yöntem sonucu üretC#](media/field-result-cs.png)

   - Visual Basic:

       ![Yöntem sonucu oluştur VB](media/field-result-vb.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Kod Oluşturma](../code-generation-in-visual-studio.md)
- [Değişiklikleri Önizleme](../../ide/preview-changes.md)