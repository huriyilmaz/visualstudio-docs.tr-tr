---
title: Soyut sınıf uygulama
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 6fcfdc06a055df28159f9d1ddc440aaf113f3264
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75568912"
---
# <a name="implement-an-abstract-class-in-visual-studio"></a>Visual Studio 'da bir soyut sınıf uygulama

Bu kod üretimi için geçerlidir:

- C#

- Visual Basic

**Ne:** Soyut bir sınıf uygulamak için gereken kodu hemen oluşturmanıza olanak sağlar.

**Ne zaman:** Bir soyut sınıftan devralması istiyorsunuz.

**Neden:** Tüm soyut üyeleri tek tek el ile uygulayabilirsiniz, ancak bu özellik tüm yöntem imzalarını otomatik olarak oluşturur.

## <a name="how-to"></a>Nasıl yapılır

1. İmlecinizi, soyut bir sınıftan devralındığını, ancak gerekli tüm üyeleri uygulamadığını belirten kırmızı bir dalgalı çizgi olan çizgiye yerleştirin.

   - C#:

       ![Vurgulanmış kod C #](media/abstract-highlight-cs.png)

   - Visual Basic:

       ![Vurgulanan kod VB](media/abstract-highlight-vb.png)

2. Sonra, aşağıdakilerden birini yapın:

   - **Klavye**
      - **CTRL**tuşuna basın + **.** **hızlı eylemleri ve yeniden düzenlemeler** menüsünü tetiklemek için.
   - **Fare**
      - Sağ tıklayın ve **Hızlı Eylemler ve yeniden düzenlemeler** menüsünü seçin.
      - Kırmızı dalgalı çizgi üzerine gelin ve ![ampul hatası](media/error-bulb.png) görüntülenen simge.
      - Sağ üst köşedeki ![ampul hatası](media/error-bulb.png) Sol kenar boşluğunda, metin imleci kırmızı dalgalı çizgi ile zaten varsa görüntülenen simge.

   ![Sınıf önizlemesini Uygula](media/abstract-preview-cs.png)

3. Açılan menüden **soyut sınıf Uygula** ' yı seçin.

   > [!TIP]
   > - Seçiminizi yapmadan önce yapılacak [tüm değişiklikleri görmek için](../../ide/preview-changes.md) Önizleme penceresinin altındaki **Değişiklikleri Önizle** bağlantısını kullanın.
   > - Özet sınıftan devraldığı birden çok sınıfta doğru yöntem imzalarını oluşturmak için Önizleme penceresinin altındaki **belge**, **Proje**ve **çözüm** bağlantılarını kullanın.

   Soyut yöntem imzaları oluşturulur ve uygulanmaya hazırlanın.

   - C#:

       ![Sınıf sonucu C 'yi Uygula #](media/abstract-result-cs.png)

   - Visual Basic:

       ![Sınıf sonucunu Uygula VB](media/abstract-result-vb.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Kod oluşturma](../code-generation-in-visual-studio.md)
- [Değişiklikleri Önizleme](../../ide/preview-changes.md)
