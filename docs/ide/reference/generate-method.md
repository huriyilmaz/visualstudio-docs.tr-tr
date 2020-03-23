---
title: Bir yöntem oluşturma
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: f166c31a1615c951170367223a5b19ab93811b5d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595598"
---
# <a name="generate-a-method-in-visual-studio"></a>Visual Studio'da bir yöntem oluşturun

Bu kod oluşturma için geçerlidir:

- C#

- Visual Basic

**Ne:** Bir sınıfa hemen bir yöntem eklemenizi sağlar.

**Ne zaman:** Yeni bir yöntem tanıyın ve otomatik olarak düzgün bir şekilde bildirmek istiyorsunuz.

**Neden:** Yöntem ve parametreleri kullanmadan önce bildirebilirsiniz, ancak bu özellik bildirimi otomatik olarak oluşturur.

## <a name="how-to"></a>Nasıl yapılır

1. İmlecinizi kırmızı bir dalganın olduğu çizgiye yerleştirin. Kırmızı dalgalı henüz var olmayan bir yöntemi gösterir.

   - C#:

       ![Vurgulanan kod C #](media/method-highlight-cs.png)

   - Visual Basic:

       ![Vurgulanan kod VB](media/method-highlight-vb.png)

2. Ardından, aşağıdakilerden birini yapın:

   - **Klavye**
      - **Ctrl**+tuşuna**basın.** **Hızlı Eylemler ve Refactorings** menüsünü tetiklemek için.
   - **Fare**
      - Hızlı Eylemler ve **Yeniden Faktörler** menüsünü sağ tıklatın ve seçin.
      - Kırmızı dalgalı üzerinde hover ve tıklayın ![hata ampul](media/error-bulb.png) görünen simge.
      - &nbsp; ![hata ampul](media/error-bulb.png) metin imleci kırmızı dalgalı çizgide yse sol kenar boşluğunda görünen simge.

      ![Yöntem önizlemesi oluşturma](media/method-preview-cs.png)

3. Açılan menüden **Üret yöntemini** seçin.

   > [!TIP]
   > Seçiminizi yapmadan önce yapılacak [tüm değişiklikleri görmek için](../../ide/preview-changes.md) önizleme penceresinin altındaki Önizleme **değişiklikleri** bağlantısını kullanın.

   Yöntem, kullanımından kaynaklanan parametrelerle oluşturulur.

   - C#:

       ![Yöntem sonucu c oluşturma #](media/method-result-cs.png)

   - Visual Basic:

       ![Yöntem sonucu vb oluşturma](media/method-result-vb.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Kod Oluşturma](../code-generation-in-visual-studio.md)
- [Değişiklikleri Önizleme](../../ide/preview-changes.md)
