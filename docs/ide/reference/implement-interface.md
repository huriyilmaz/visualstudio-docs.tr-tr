---
title: Arabirim uygulama
description: Hızlı Eylemler ve yeniden düzenlemeler menüsünü kullanarak bir arabirim uygulamak için gereken kodu hemen oluşturma hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- dotnet
ms.openlocfilehash: 9f5e067021e13f0a59c3b45882b204de04167559e39977446aeb779f6b4bf7e8
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121447719"
---
# <a name="implement-an-interface-in-visual-studio"></a>Visual Studio bir arabirim uygulama

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
   > - arabirimi uygulayan birden çok sınıfta doğru yöntem imzalarını oluşturmak için önizleme penceresinin altındaki **belge**, **Project** ve **çözüm** bağlantılarını kullanın.

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
