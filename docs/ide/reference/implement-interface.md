---
title: Arabirim uygulama
description: Hızlı Eylemler ve yeniden düzenlemeler menüsünü kullanarak bir arabirim uygulamak için gereken kodu hemen oluşturma hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 0484ed5f63cd4651669a8e3c1f94f5aad96fcc03
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2020
ms.locfileid: "96617116"
---
# <a name="implement-an-interface-in-visual-studio"></a>Visual Studio 'da arabirim uygulama

Bu kod üretimi için geçerlidir:

- C#

- Visual Basic

**Ne:** Bir arabirim uygulamak için gereken kodu hemen üretmenizi sağlar.

**Ne zaman:** Bir arabirimden devralması istiyorsunuz.

**Neden:** Tüm arabirimi tek tek el ile uygulayabilirsiniz, ancak bu özellik tüm yöntem imzalarını otomatik olarak oluşturur.

## <a name="how-to"></a>Nasıl yapılır

1. İmlecinizi, bir arabirime başvurduğunu ancak gerekli tüm üyeleri uygulamadığını belirten kırmızı renkli bir dalgalı çizgi olan çizgiye yerleştirin.

   - C#:

       ![Vurgulanmış kod C #](media/interface-highlight-cs.png)

   - Visual Basic:

       ![Vurgulanan kod VB](media/interface-highlight-vb.png)

2. Sonra, aşağıdakilerden birini yapın:

   - **Klavye**
      - **CTRL** tuşuna basın + **.** **hızlı eylemleri ve yeniden düzenlemeler** menüsünü tetiklemek için.
   - **Fare**
      - Sağ tıklayın ve **Hızlı Eylemler ve yeniden düzenlemeler** menüsünü seçin.
      - Kırmızı dalgalı çizgi üzerine gelin ve ![ampul hatası](media/error-bulb.png) görüntülenen simge.
      - Sağ üst köşedeki ![ampul hatası](media/error-bulb.png) Sol kenar boşluğunda, metin imleci kırmızı dalgalı çizgi ile zaten varsa görüntülenen simge.

3. Açılan menüden **arabirimi Uygula** ' yı seçin.

   ![Arabirim önizlemeyi Uygula](media/interface-preview-cs.png)

   > [!TIP]
   > - Seçiminizi yapmadan önce yapılacak [tüm değişiklikleri görmek için](../../ide/preview-changes.md) Önizleme penceresinin altındaki **Değişiklikleri Önizle** bağlantısını kullanın.
   > - Arabirimi uygulayan birden çok sınıfta doğru yöntem imzalarını oluşturmak için Önizleme penceresinin altındaki **belge**, **Proje** ve **çözüm** bağlantılarını kullanın.

   Arabirimin yöntem imzaları oluşturulur ve uygulanmaya hazırlanın.

   - C#:

       ![Arabirim sonucu C Uygula #](media/interface-result-cs.png)

   - Visual Basic:

       ![Arabirim sonucunu Uygula VB](media/interface-result-vb.png)

   > [!TIP]
   > (Yalnızca C#) Ad çakışmalarını önlemek için arabirim adına sahip her bir yöntemi ön yüz olarak **Uygula** seçeneğini kullanın.
   >
   > ![Arabirime açıkça sonuç uygulama](media/interface-explicitresult-cs.png);

## <a name="see-also"></a>Ayrıca bkz.

- [Kod oluşturma](../code-generation-in-visual-studio.md)
- [Değişiklikleri Önizleme](../../ide/preview-changes.md)
