---
title: Alan, özellik, yerel değişken oluşturma
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: b554aa5586150942c0fc7d7aeada9356a67029ca
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595611"
---
# <a name="generate-a-field-property-or-local-variable-in-visual-studio"></a>Visual Studio'da bir alan, özellik veya yerel değişken oluşturma

Bu kod oluşturma için geçerlidir:

- C#

- Visual Basic

**Ne:** Daha önce bildirilmemiş bir alan, özellik veya yerel için kodu hemen oluşturmanıza olanak tanır.

**Ne zaman:** Yazarken yeni bir alan, özellik veya yerel tanıtın ve otomatik olarak düzgün bir şekilde bildirmek istiyorsunuz.

**Neden:** Kullanmadan önce alanı, özelliği veya yerel alanı bildirebilirsiniz, ancak bu özellik bildirimi oluşturur ve otomatik olarak yazar.

## <a name="how-to"></a>Nasıl yapılır

1. İmlecinizi kırmızı bir dalganın olduğu çizgiye yerleştirin. Kırmızı dalgalı henüz var olmayan bir alanı, yerel veya özelliği gösterir.

   - C#:

       ![Vurgulanan kod C #](media/field-highlight-cs.png)

   - Visual Basic:

       ![Vurgulanan kod VB](media/field-highlight-vb.png)

2. Ardından, aşağıdakilerden birini yapın:

   - **Klavye**
      - **Ctrl**+tuşuna**basın.** **Hızlı Eylemler ve Refactorings** menüsünü tetiklemek için.
   - **Fare**
      - Hızlı Eylemler ve **Yeniden Faktörler** menüsünü sağ tıklatın ve seçin.
      - Kırmızı dalgalı üzerinde hover ve tıklayın ![hata ampul](media/error-bulb.png) görünen simge.
      - &nbsp; ![hata ampul](media/error-bulb.png) metin imleci kırmızı dalgalı çizgide yse sol kenar boşluğunda görünen simge.

      ![Alan/özellik/yerel önizleme oluşturma](media/field-preview-cs.png)

3. Açılan menüden nesil seçeneklerinden birini seçin.

   > [!TIP]
   > Seçiminizi yapmadan önce yapılacak [tüm değişiklikleri görmek için](../../ide/preview-changes.md) önizleme penceresinin altındaki Önizleme **değişiklikleri** bağlantısını kullanın.

   Alan, özellik veya yerel, kullanımından çıkarılan türle oluşturulur.

   - C#:

       ![Yöntem sonucu c oluşturma #](media/field-result-cs.png)

   - Visual Basic:

       ![Yöntem sonucu vb oluşturma](media/field-result-vb.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Kod Oluşturma](../code-generation-in-visual-studio.md)
- [Değişiklikleri Önizleme](../../ide/preview-changes.md)
