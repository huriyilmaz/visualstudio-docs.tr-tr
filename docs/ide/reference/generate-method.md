---
title: Yöntem oluşturma
description: Bir sınıfa hemen bir yöntemi eklemek için hızlı eylemler ve yeniden düzenlemeler menüsünü nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: c6f4a25e3cda10e74c344cb7eef879b78f60a1de
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99903909"
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

       ![Vurgulanmış kod C #](media/method-highlight-cs.png)

   - Visual Basic:

       ![Vurgulanan kod VB](media/method-highlight-vb.png)

2. Sonra, aşağıdakilerden birini yapın:

   - **Klavye**
      - **CTRL** tuşuna basın + **.** **hızlı eylemleri ve yeniden düzenlemeler** menüsünü tetiklemek için.
   - **Fare**
      - Sağ tıklayın ve **Hızlı Eylemler ve yeniden düzenlemeler** menüsünü seçin.
      - Kırmızı dalgalı çizgi üzerine gelin ve ![ampul hatası](media/error-bulb.png) görüntülenen simge.
      - Sağ üst köşedeki ![ampul hatası](media/error-bulb.png) Sol kenar boşluğunda, metin imleci kırmızı dalgalı çizgi ile zaten varsa görüntülenen simge.

      ![Yöntem önizlemesi oluştur](media/method-preview-cs.png)

3. Açılan menüden **oluşturma yöntemi** ' ni seçin.

   > [!TIP]
   > Seçiminizi yapmadan önce yapılacak [tüm değişiklikleri görmek için](../../ide/preview-changes.md) Önizleme penceresinin altındaki **Değişiklikleri Önizle** bağlantısını kullanın.

   Yöntemi, kullanımından çıkarılan herhangi bir parametreyle oluşturulur.

   - C#:

       ![Yöntem sonuç C oluştur #](media/method-result-cs.png)

   - Visual Basic:

       ![Yöntem sonucu oluştur VB](media/method-result-vb.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Kod oluşturma](../code-generation-in-visual-studio.md)
- [Değişiklikleri Önizleme](../../ide/preview-changes.md)
