---
title: Yöntem oluşturma
ms.date: 01/26/2018
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: c85e3f849d7d74f326c1cf330b0e2c338d78fc6a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668340"
---
# <a name="generate-a-method-in-visual-studio"></a>Visual Studio 'da bir yöntem oluşturma

Bu kod üretimi için geçerlidir:

- C#

- Visual Basic

**Ne:** Bir sınıfa hemen bir yöntem eklemenizi sağlar.

**Ne zaman:** Yeni bir yöntem ortaya çıkarabilir ve bunu otomatik olarak doğru bir şekilde bildirmek istiyorsunuz.

**Neden:** Yöntemi ve parametreleri kullanmadan önce bildirebilirsiniz, ancak bu özellik bildirimi otomatik olarak oluşturacaktır.

## <a name="how-to"></a>Nasıl yapılır

1. İmlecinizi kırmızı dalgalı çizgi olan çizgiye yerleştirin. Kırmızı dalgalı çizgi henüz mevcut olmayan bir yöntemi gösterir.

   - C#:

       ![Vurgulanan kodC#](media/method-highlight-cs.png)

   - Visual Basic:

       ![Vurgulanan kod VB](media/method-highlight-vb.png)

2. Sonra, aşağıdakilerden birini yapın:

   - **Klavyenizdeki**
      - **Ctrl** + tuşuna basın **.** **hızlı eylemleri ve yeniden düzenlemeler** menüsünü tetiklemek için.
   - **Tığında**
      - Sağ tıklayın ve **Hızlı Eylemler ve yeniden düzenlemeler** menüsünü seçin.
      - Kırmızı dalgalı çizgi üzerine gelin ve ![ampul hatası](media/error-bulb.png) görüntülenen simge.
      - &nbsp; ![ampul hatası](media/error-bulb.png) Sol kenar boşluğunda, metin imleci kırmızı dalgalı çizgi ile zaten varsa görüntülenen simge.

      ![Yöntem önizlemesi oluştur](media/method-preview-cs.png)

3. Açılan menüden **oluşturma yöntemi** ' ni seçin.

   > [!TIP]
   > Seçiminizi yapmadan önce yapılacak [tüm değişiklikleri görmek için](../../ide/preview-changes.md) Önizleme penceresinin altındaki **Değişiklikleri Önizle** bağlantısını kullanın.

   Yöntemi, kullanımından çıkarılan herhangi bir parametreyle oluşturulur.

   - C#:

       ![Yöntem sonucu üretC#](media/method-result-cs.png)

   - Visual Basic:

       ![Yöntem sonucu oluştur VB](media/method-result-vb.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Kod Oluşturma](../code-generation-in-visual-studio.md)
- [Değişiklikleri Önizleme](../../ide/preview-changes.md)