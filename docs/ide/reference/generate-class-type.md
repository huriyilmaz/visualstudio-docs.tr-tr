---
title: Sınıf veya tür oluştur
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
f1_keywords:
- vsl.GenerateFromUsage
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 94786ef10e427a0deb4f80471305509124f1638b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75595637"
---
# <a name="generate-a-class-or-type-in-visual-studio"></a>Visual Studio 'da bir sınıf veya tür oluşturma

Bu kod üretimi için geçerlidir:

- C#

- Visual Basic

**Ne:** Bir sınıf veya tür için kodu hemen üretmenizi sağlar.

**Ne zaman:** Yeni bir sınıf veya tür tanıtmanız ve bunu otomatik olarak doğru bir şekilde bildirmek istemeniz gerekir.

**Neden:** Sınıfı veya türü kullanmadan önce bildirebilirsiniz, ancak bu özellik sınıfı veya türü otomatik olarak oluşturacaktır.

## <a name="how-to"></a>Nasıl yapılır

1. İmlecinizi kırmızı dalgalı çizgi olan çizgiye yerleştirin. Kırmızı dalgalı çizgi, henüz mevcut olmayan bir sınıfı gösterir.

   - C#:

       ![Vurgulanmış kod C #](media/class-highlight-cs.png)

   - Visual Basic:

       ![Vurgulanan kod VB](media/class-highlight-vb.png)

2. Sonra, aşağıdakilerden birini yapın:

   - **Klavye**
      - **CTRL**tuşuna basın + **.** **hızlı eylemleri ve yeniden düzenlemeler** menüsünü tetiklemek için.
   - **Fare**
      - Sağ tıklayın ve **Hızlı Eylemler ve yeniden düzenlemeler** menüsünü seçin.
      - Kırmızı dalgalı çizgi üzerine gelin ve ![ampul hatası](media/error-bulb.png) görüntülenen simge.
      - Sağ üst köşedeki ![ampul hatası](media/error-bulb.png) Sol kenar boşluğunda, metin imleci kırmızı dalgalı çizgi ile zaten varsa görüntülenen simge.

      ![Sınıf önizlemesi oluştur](media/class-preview-cs.png)

3. Açılan menüdeki seçeneklerden birini seçin:

   - Yeni dosyada '*TypeName*' sınıfını oluştur &mdash; *TypeName*. cs/. vb adlı dosyada *TypeName* adlı bir sınıf oluşturur
   - '*TypeName*' sınıfı oluşturma &mdash; geçerli dosyada *TypeName* adlı bir sınıf oluşturur.
   - '*TypeName*' iç içe sınıfını oluşturma &mdash; , geçerli sınıfın içinde Iç içe yerleştirilmiş *TypeName* adlı bir sınıf oluşturur.
   - Yeni tür üret... &mdash; Belirttiğiniz tüm özelliklerle yeni bir sınıf veya yapı oluşturur.

   > [!TIP]
   > Seçiminizi yapmadan önce yapılacak [tüm değişiklikleri görmek için](../../ide/preview-changes.md) Önizleme penceresinin altındaki **Değişiklikleri Önizle** bağlantısını kullanın.

4. **Yeni tür öğesi oluştur** ' u seçtiyseniz **tür oluştur** iletişim kutusu açılır. Yeni türün erişilebilirliğini, türünü ve konumunu yapılandırın.

   ![Tür oluştur](media/class-newtype-cs.png)

   Seçim | Açıklama
   --- | ---
   Access | Türü *varsayılan*, *iç* veya *genel* erişime sahip olacak şekilde ayarlayın.
   Tip | Bu, *sınıf* veya *Yapı*olarak ayarlanabilir.
   Name | Bu değiştirilemez ve zaten yazdığınız ad olur.
   Project | Çözümünüzde birden fazla proje varsa, sınıfın/yapının nerede canlı olmasını istediğinizi seçebilirsiniz.
   Dosya Adı | Yeni bir dosya oluşturabilir veya türü mevcut bir dosyaya ekleyebilirsiniz.

Sınıf veya yapı oluşturulur. C# için bir Oluşturucu da oluşturulur.

- C#

   ![Sınıf sonucu oluştur C #](media/class-result-cs.png)

- Visual Basic

   ![Sınıf sonucu oluştur VB](media/class-result-vb.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Kod oluşturma](../code-generation-in-visual-studio.md)
- [Değişiklikleri Önizleme](../../ide/preview-changes.md)
