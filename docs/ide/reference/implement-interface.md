---
title: Arabirim uygulama
ms.date: 01/26/2018
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 45265c10677b8d3eadc27eb3b6e22c69bb5299be
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658911"
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

       ![Vurgulanan kodC#](media/interface-highlight-cs.png)

   - Visual Basic:

       ![Vurgulanan kod VB](media/interface-highlight-vb.png)

2. Sonra, aşağıdakilerden birini yapın:

   - **Klavyenizdeki**
      - **Ctrl** + tuşuna basın **.** **hızlı eylemleri ve yeniden düzenlemeler** menüsünü tetiklemek için.
   - **Tığında**
      - Sağ tıklayın ve **Hızlı Eylemler ve yeniden düzenlemeler** menüsünü seçin.
      - Kırmızı dalgalı çizgi üzerine gelin ve ![ampul hatası](media/error-bulb.png) görüntülenen simge.
      - &nbsp; ![ampul hatası](media/error-bulb.png) Sol kenar boşluğunda, metin imleci kırmızı dalgalı çizgi ile zaten varsa görüntülenen simge.

3. Açılan menüden **arabirimi Uygula** ' yı seçin.

   ![Arabirim önizlemeyi Uygula](media/interface-preview-cs.png)

   > [!TIP]
   > - Seçiminizi yapmadan önce yapılacak [tüm değişiklikleri görmek için](../../ide/preview-changes.md) Önizleme penceresinin altındaki **Değişiklikleri Önizle** bağlantısını kullanın.
   > - Arabirimi uygulayan birden çok sınıfta doğru yöntem imzalarını oluşturmak için Önizleme penceresinin altındaki **belge**, **Proje**ve **çözüm** bağlantılarını kullanın.

   Arabirimin yöntem imzaları oluşturulur ve uygulanmaya hazırlanın.

   - C#:

       ![Arabirim sonucunu UygulaC#](media/interface-result-cs.png)

   - Visual Basic:

       ![Arabirim sonucunu Uygula VB](media/interface-result-vb.png)

   > [!TIP]
   > (C# yalnızca) Ad çakışmalarını önlemek için arabirim adına sahip her bir yöntemi ön yüz olarak **Uygula** seçeneğini kullanın.
   >
   > ![Arabirime açıkça sonuç uygulama](media/interface-explicitresult-cs.png);

## <a name="see-also"></a>Ayrıca bkz.

- [Kod Oluşturma](../code-generation-in-visual-studio.md)
- [Değişiklikleri Önizleme](../../ide/preview-changes.md)