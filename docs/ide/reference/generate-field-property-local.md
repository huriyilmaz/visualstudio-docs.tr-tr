---
title: Alan, özellik, yerel değişken oluşturma
description: Önceden belirlenemeyen bir alan, özellik veya yerel kod oluşturmak için Hızlı Eylemler ve Yeniden Düzenleme menüsünü kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- dotnet
ms.openlocfilehash: e9ffbf7e58478bcbee7ce7b5ac86aa5dfb272c05
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122143930"
---
# <a name="generate-a-field-property-or-local-variable-in-visual-studio"></a>Bir alan, özellik veya yerel değişken oluşturma Visual Studio

Bu kod oluşturma aşağıdakiler için geçerlidir:

- C#

- Visual Basic

**Ne:** Önceden belirlenemeyen bir alan, özellik veya yerel kod için kodu hemen oluşturmana olanak sağlar.

**Ne zaman:** Yazarken yeni bir alan, özellik veya yerel olarak tanıtılır ve otomatik olarak düzgün bir şekilde bildirilir.

**Neden:** Alanı, özelliği veya yerel alanı kullanmadan önce bildirebilirsiniz, ancak bu özellik bildirimi ve türü otomatik olarak üretir.

## <a name="how-to"></a>Nasıl yapılır

1. İmlecinizi kırmızı bir geçişin bulunduğu satıra yerleştirebilirsiniz. Kırmızı geçiş henüz mevcut olmayan bir alanı, yerel veya özelliği gösterir.

   - C#:

       ![Vurgulanan kod C #](media/field-highlight-cs.png)

   - Visual Basic:

       ![Vurgulanan kod VB](media/field-highlight-vb.png)

2. Ardından, aşağıdakilerden birini yapın:

   - **Klavye**
      - **Ctrl tuşuna** + **basın.** hızlı eylemler **ve yeniden düzenleme menüsünü tetiklemek** için.
   - **Fare**
      - Sağ tıklayın ve Hızlı **Eylemler ve Yeniden Düzenleme menüsünü** seçin.
      - Kırmızı çizginin üzerine gelin ve ![hata ampulü](media/error-bulb.png) simgesi görüntülenir.
      - Sağ üst köşedeki ![hata ampulü](media/error-bulb.png) simgesi, metin imleci kırmızı çizgiyle çizgi üzerinde zaten varsa sol kenar boşluğunda görünür.

      ![Alan/özellik/yerel önizleme oluşturma](media/field-preview-cs.png)

3. Açılan menüden oluşturma seçeneklerinden birini belirleyin.

   > [!TIP]
   > Seçiminizi **yapmadan** önce yapılacak tüm değişiklikleri görmek için önizleme penceresinin [altındaki](../../ide/preview-changes.md) Değişiklikleri önizle bağlantısını kullanın.

   alan, özellik veya yerel oluşturulur ve türü kullanımından itibaren bu türe göre oluşturulur.

   - C#:

       ![Yöntem sonucu oluşturma C #](media/field-result-cs.png)

   - Visual Basic:

       ![Yöntem sonucu oluşturma VB](media/field-result-vb.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Kod Oluşturma](../code-generation-in-visual-studio.md)
- [Değişiklikleri Önizleme](../../ide/preview-changes.md)
