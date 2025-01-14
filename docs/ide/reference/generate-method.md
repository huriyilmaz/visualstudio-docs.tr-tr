---
title: Yöntem oluşturma
description: Bir sınıfa hemen yöntem eklemek için Hızlı Eylemler ve Yeniden Düzenleme menüsünü kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- dotnet
ms.openlocfilehash: 21d77611c621eca9a20f467a012395d5d509aa9f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122123911"
---
# <a name="generate-a-method-in-visual-studio"></a>Visual Studio'de yöntem oluşturma

Bu kod oluşturma aşağıdakiler için geçerlidir:

- C#

- Visual Basic

**Ne:** Hemen bir sınıfa yöntem eklemenize olanak sağlar.

**Ne zaman:** Yeni bir yöntem tanıtmış ve bunu otomatik olarak düzgün bir şekilde bildirmiş oluruz.

**Neden:** Yöntemi ve parametreleri kullanmadan önce bildirebilirsiniz, ancak bu özellik bildirimi otomatik olarak üretir.

## <a name="how-to"></a>Nasıl yapılır

1. İmlecinizi kırmızı bir geçişin bulunduğu satıra yerleştirebilirsiniz. Kırmızı geçiş, henüz mevcut olmayan bir yöntemi gösterir.

   - C#:

       ![Vurgulanan kod C #](media/method-highlight-cs.png)

   - Visual Basic:

       ![Vurgulanan kod VB](media/method-highlight-vb.png)

2. Ardından, aşağıdakilerden birini yapın:

   - **Klavye**
      - **Ctrl tuşuna** + **basın.** hızlı eylemler **ve yeniden düzenleme menüsünü tetiklemek** için.
   - **Fare**
      - Sağ tıklayın ve Hızlı **Eylemler ve Yeniden Düzenleme menüsünü** seçin.
      - Kırmızı çizginin üzerine gelin ve ![hata ampulü](media/error-bulb.png) simgesi görüntülenir.
      - Sağ üst köşedeki ![hata ampulü](media/error-bulb.png) simgesi, metin imleci kırmızı çizgiyle çizgi üzerinde zaten varsa sol kenar boşluğunda görünür.

      ![Yöntem önizlemesi oluşturma](media/method-preview-cs.png)

3. Açılan **menüden** Yöntemi oluştur'a tıklayın.

   > [!TIP]
   > Seçiminizi **yapmadan** önce yapılacak tüm değişiklikleri görmek için önizleme penceresinin [altındaki](../../ide/preview-changes.md) Değişiklikleri önizle bağlantısını kullanın.

   yöntemi, kullanımından alınan parametrelerle oluşturulur.

   - C#:

       ![Yöntem sonucu oluşturma C #](media/method-result-cs.png)

   - Visual Basic:

       ![Yöntem sonucu oluşturma VB](media/method-result-vb.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Kod Oluşturma](../code-generation-in-visual-studio.md)
- [Değişiklikleri Önizleme](../../ide/preview-changes.md)
