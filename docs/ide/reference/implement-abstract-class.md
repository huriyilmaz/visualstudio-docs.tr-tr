---
title: Soyut bir sınıf uygulama
description: Soyut bir sınıf uygulamak için gereken kodu hemen oluşturmak için Hızlı Eylemler ve Yeniden Düzenleme menüsünü kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- dotnet
ms.openlocfilehash: 201ebe54d84803ab0621afd5754ce507b1d32ac7
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122101316"
---
# <a name="implement-an-abstract-class-in-visual-studio"></a>Visual Studio'de soyut bir sınıf uygulama

Bu kod oluşturma aşağıdakiler için geçerlidir:

- C#

- Visual Basic

**Ne:** Soyut bir sınıf uygulamak için gereken kodu hemen oluşturmana olanak sağlar.

**Ne zaman:** Soyut bir sınıftan devralmak istediğiniz.

**Neden:** Tüm soyut üyeleri el ile tek tek uygulayabilirsiniz, ancak bu özellik tüm yöntem imzalarını otomatik olarak üretir.

## <a name="how-to"></a>Nasıl yapılır

1. İmlecinizi, soyut bir sınıftan devralınmış ancak gerekli tüm üyeleri uygulamamış olduğunu belirten kırmızı bir geçişin olduğu satıra yerleştirin.

   - C#:

       ![Vurgulanan kod C #](media/abstract-highlight-cs.png)

   - Visual Basic:

       ![Vurgulanan kod VB](media/abstract-highlight-vb.png)

2. Ardından, aşağıdakilerden birini yapın:

   - **Klavye**
      - **Ctrl tuşuna** + **basın.** hızlı eylemler **ve yeniden düzenleme menüsünü tetiklemek** için.
   - **Fare**
      - Sağ tıklayın ve Hızlı **Eylemler ve Yeniden Düzenleme menüsünü** seçin.
      - Kırmızı çizginin üzerine gelin ve ![hata ampulü](media/error-bulb.png) simgesi görüntülenir.
      - Sağ üst köşedeki ![hata ampulü](media/error-bulb.png) simgesi, metin imleci kırmızı çizgiyle çizgi üzerinde zaten varsa sol kenar boşluğunda görünür.

   ![Sınıf önizlemesini uygulama](media/abstract-preview-cs.png)

3. Açılan **menüden Soyut** Sınıfı Uygulay'ı seçin.

   > [!TIP]
   > - Seçiminizi **yapmadan** önce yapılacak tüm değişiklikleri görmek için önizleme penceresinin [altındaki](../../ide/preview-changes.md) Değişiklikleri önizle bağlantısını kullanın.
   > - Soyut **sınıftan** **devralınan** birden  çok sınıf arasında uygun yöntem imzalarını oluşturmak için önizleme penceresinin altındaki Belge , Project ve Çözüm bağlantılarını kullanın.

   Soyut yöntem imzaları oluşturulur ve uygulanmaya hazırdır.

   - C#:

       ![Sınıf sonucu uygulama C #](media/abstract-result-cs.png)

   - Visual Basic:

       ![Sınıf sonucu uygulama VB](media/abstract-result-vb.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Kod Oluşturma](../code-generation-in-visual-studio.md)
- [Değişiklikleri Önizleme](../../ide/preview-changes.md)
