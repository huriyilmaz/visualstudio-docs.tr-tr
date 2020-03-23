---
title: Sınıf veya tür oluşturma
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595637"
---
# <a name="generate-a-class-or-type-in-visual-studio"></a>Visual Studio'da bir sınıf veya tür oluşturma

Bu kod oluşturma için geçerlidir:

- C#

- Visual Basic

**Ne:** Bir sınıf veya tür için kodu hemen oluşturmanıza olanak tanır.

**Ne zaman:** Yeni bir sınıf veya tür tanıtın ve düzgün, otomatik olarak bildirmek istiyorum.

**Neden:** Sınıfı kullanmadan önce sınıfveya türü bildirebilirsiniz, ancak bu özellik sınıfı veya türü otomatik olarak oluşturur.

## <a name="how-to"></a>Nasıl yapılır

1. İmlecinizi kırmızı bir dalganın olduğu çizgiye yerleştirin. Kırmızı dalgalı henüz var olmayan bir sınıfı gösterir.

   - C#:

       ![Vurgulanan kod C #](media/class-highlight-cs.png)

   - Visual Basic:

       ![Vurgulanan kod VB](media/class-highlight-vb.png)

2. Ardından, aşağıdakilerden birini yapın:

   - **Klavye**
      - **Ctrl**+tuşuna**basın.** **Hızlı Eylemler ve Refactorings** menüsünü tetiklemek için.
   - **Fare**
      - Hızlı Eylemler ve **Yeniden Faktörler** menüsünü sağ tıklatın ve seçin.
      - Kırmızı dalgalı üzerinde hover ve tıklayın ![hata ampul](media/error-bulb.png) görünen simge.
      - &nbsp; ![hata ampul](media/error-bulb.png) metin imleci kırmızı dalgalı çizgide yse sol kenar boşluğunda görünen simge.

      ![Sınıf önizlemesi oluşturma](media/class-preview-cs.png)

3. Açılan menüden seçeneklerden birini seçin:

   - &mdash;Yeni dosyada '*TypeName*' oluşturma Türü Adı .cs/.vb adlı bir dosyada *TypeName* adlı bir sınıf oluşturur *TypeName*
   - 'TypeName '&mdash;oluştur' Geçerli dosyada*TypeName*adlı bir sınıf oluşturur. *TypeName*
   - İç içe geçen sınıf&mdash;'*TypeName*' oluşturun, geçerli sınıfın içinde yer alan *TypeName* adlı bir sınıf oluşturur.
   - Yeni tür oluşturun... &mdash;Belirttiğiniz tüm özelliklerle yeni bir sınıf veya yapı oluşturur.

   > [!TIP]
   > Seçiminizi yapmadan önce yapılacak [tüm değişiklikleri görmek için](../../ide/preview-changes.md) önizleme penceresinin altındaki Önizleme **değişiklikleri** bağlantısını kullanın.

4. Yeni tür öğesi **oluştur'u** seçtiyseniz, **Türü Oluştur** iletişim kutusu açılır. Yeni türün erişilebilirliğini, türünü ve konumunu yapılandırın.

   ![Tür oluşturma](media/class-newtype-cs.png)

   Seçim | Açıklama
   --- | ---
   Erişim | Varsayılan, *İç* *Default*veya *Genel* erişime sahip türü ayarlayın.
   Tip | Bu *sınıf* veya *yapı*olarak ayarlanabilir.
   Adı | Bu değiştirilemez ve zaten yazdığınız ad olacaktır.
   Project | Çözümünüzde birden çok proje varsa, sınıfın/yapının nerede yaşamasını istediğinizi seçebilirsiniz.
   Dosya Adı | Yeni bir dosya oluşturabilir veya türü varolan bir dosyaya ekleyebilirsiniz.

Sınıf veya yapı oluşturulur. C# için bir oluşturucu da oluşturulur.

- C#

   ![C sınıfı sonucu oluşturma #](media/class-result-cs.png)

- Visual Basic

   ![Sınıf sonucu vb oluşturma](media/class-result-vb.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Kod Oluşturma](../code-generation-in-visual-studio.md)
- [Değişiklikleri Önizleme](../../ide/preview-changes.md)
