---
title: Sınıf veya tür oluşturma
description: Bir sınıf veya tür için kodu hemen oluşturmak üzere Hızlı Eylemler ve Yeniden Düzenlemeler menüsünü kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
f1_keywords:
- vsl.GenerateFromUsage
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 3af7bb3f8a52029c0b9e11df802b8f4788711af0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122034311"
---
# <a name="generate-a-class-or-type-in-visual-studio"></a>Sınıf veya tür oluşturma Visual Studio

Bu kod oluşturma aşağıdakiler için geçerlidir:

- C#

- Visual Basic

**Ne:** Bir sınıf veya tür için kodu hemen oluşturmana olanak sağlar.

**Ne zaman:** Yeni bir sınıf veya tür tanıtılır ve otomatik olarak düzgün bir şekilde bildirilir.

**Neden:** Sınıf veya türü, kullanmadan önce bildirebilirsiniz, ancak bu özellik sınıf veya türü otomatik olarak üretir.

## <a name="how-to"></a>Nasıl yapılır

1. İmlecinizi kırmızı bir geçişin bulunduğu satıra yerleştirebilirsiniz. Kırmızı geçiş, henüz mevcut olmayan bir sınıfı gösterir.

   - C#:

       ![Vurgulanan kod C #](media/class-highlight-cs.png)

   - Visual Basic:

       ![Vurgulanan kod VB](media/class-highlight-vb.png)

2. Ardından, aşağıdakilerden birini yapın:

   - **Klavye**
      - **Ctrl tuşuna** + **basın.** Hızlı Eylemler **ve Yeniden Düzenleme menüsünü tetiklemek** için.
   - **Fare**
      - Sağ tıklayın ve Hızlı **Eylemler ve Yeniden Düzenleme menüsünü** seçin.
      - Kırmızı çizginin üzerine gelin ve ![hata ampulü](media/error-bulb.png) simgesi görüntülenir.
      - Sağ üst köşedeki ![hata ampulü](media/error-bulb.png) simgesi, metin imleci kırmızı çizgiyle çizgi üzerinde zaten varsa sol kenar boşluğunda görünür.

      ![Sınıf önizlemesi oluşturma](media/class-preview-cs.png)

3. Açılan menüden seçeneklerden birini belirleyin:

   - Yeni dosyada '*TypeName*' sınıfı oluşturma &mdash; TypeName .cs/.vb adlı bir dosyada *TypeName* adlı bir sınıf oluşturur 
   - Generate class '*TypeName*' &mdash; Geçerli dosyada *TypeName adlı* bir sınıf oluşturur.
   - İç içe geçmiş '*TypeName*' sınıfı &mdash; oluştur Geçerli sınıfın içinde iç içe geçmiş *TypeName* adlı bir sınıf oluşturur.
   - Yeni tür oluştur... &mdash; Belirttiğiniz tüm özelliklerle birlikte yeni bir sınıf veya yapı oluşturur.

   > [!TIP]
   > Seçiminizi **yapmadan** önce yapılacak tüm değişiklikleri görmek için önizleme penceresinin [altındaki](../../ide/preview-changes.md) Değişiklikleri önizle bağlantısını kullanın.

4. Yeni tür öğesi **oluştur'ı seçtiysanız** Tür **Oluştur** iletişim kutusu açılır. Yeni türün erişilebilirliğini, türünü ve konumunu yapılandırma.

   ![Tür oluşturma](media/class-newtype-cs.png)

   Seçim | Açıklama
   --- | ---
   Access | Türü Varsayılan , İç *veya Genel* *erişime* *sahip olacak şekilde* ayarlayın.
   Tip | Bu, sınıf veya *yapı* olarak *ayarlanmış olabilir.*
   Name | Bu değiştirilemez ve önceden yazmış olduğunuz ad olur.
   Project | Çözümünüzde birden çok proje varsa, sınıfın/yapının yaşamalarını istediğiniz yeri seçebilirsiniz.
   Dosya Adı | Yeni bir dosya oluşturabilir veya türü var olan bir dosyaya eklemek için kullanabilirsiniz.

Sınıf veya yapı oluşturulur. C# için bir oluşturucu da oluşturulur.

- C#

   ![Sınıf sonucu oluşturma C #](media/class-result-cs.png)

- Visual Basic

   ![Sınıf sonucu oluşturma VB](media/class-result-vb.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Kod Oluşturma](../code-generation-in-visual-studio.md)
- [Değişiklikleri Önizleme](../../ide/preview-changes.md)
