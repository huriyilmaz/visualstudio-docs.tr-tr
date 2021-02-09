---
title: Yerel bir değişken tanıtma
description: Varolan bir ifadeyi değiştirmek için yerel bir değişken oluşturun. İfadeyi seçin, sağ tıklayın ve hızlı eylemler ve yeniden düzenlemeler menüsünü seçin, ' expression ' ' ın (tüm oluşumlar) için yerel Ekle ' yi seçin.
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 35850293b1ef739506fe6848e000396f6bacf1d8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99852303"
---
# <a name="introduce-a-local-variable-in-visual-studio"></a>Visual Studio 'da yerel bir değişken tanıtma

Bu kod üretimi için geçerlidir:

- C#

- Visual Basic

**Ne:** Varolan bir ifadeyi değiştirmek için hemen yerel bir değişken oluşturmanıza olanak sağlar.

**Ne zaman:** Daha sonra yerel bir değişkense, daha sonra kolayca kullanılabilecek bir kodunuz var.

**Neden:** Kodu çeşitli konumlarda kullanmak için birden çok kez kopyalayabilir ve yapıştırabilirsiniz, ancak işlemi bir kez gerçekleştirmek, sonucu yerel bir değişkende depolamak ve içinde yerel değişkeni kullanmak daha iyidir.

## <a name="how-to"></a>Nasıl yapılır

1. Yeni bir yerel değişkene atamak istediğiniz ifadeyi vurgulayın.

   - C#:

       ![Vurgulanmış kod C #](media/local-highlight-cs.png)

   - Visual Basic:

       ![Vurgulanan kod VB](media/local-highlight-vb.png)

2. Sonra, aşağıdakilerden birini yapın:

   - **Klavye**
      - **CTRL** tuşuna basın + **.** **hızlı eylemleri ve yeniden düzenlemeler** menüsünü tetiklemek için.
   - **Fare**
      - Sağ tıklayın ve **Hızlı Eylemler ve yeniden düzenlemeler** menüsünü seçin.
      - Sağ üst köşedeki ![Hızlı Eylemler ve yeniden düzenlemeler menüsünün sol kenar boşluğunda görünen screwdriver simgesinin ekran görüntüsü.](media/screwdriver.png) Sol kenar boşluğunda görüntülenen simge, metin imleç zaten vurgulanan ifade ile satırda varsa görüntülenir.

   ![Yerel Önizlemeyi göster](media/local-preview-cs.png)

3. Açılan menüden **' expression ' için yerel (tüm oluşumlar) Ekle '** yi seçin.

   > [!TIP]
   > Seçiminizi yapmadan önce yapılacak [tüm değişiklikleri görmek için](../../ide/preview-changes.md) Önizleme penceresinin altındaki **Değişiklikleri Önizle** bağlantısını kullanın.

   Yerel değişken, kullanımından çıkarılan türle oluşturulur. Yeni yerel değişkene yeni bir ad verin.

   - C#:

       ![Arabirim sonucu C Uygula #](media/local-result-cs.png)

   - Visual Basic:

       ![Arabirim sonucunu Uygula VB](media/local-result-vb.png)

   > [!NOTE]
   > Kullanabilirsiniz... **tüm oluşumları..** . yalnızca özel olarak vurguladığınız bir ifadeyi değil, seçili ifadenin her örneğini değiştirmek için menü seçeneği.

## <a name="see-also"></a>Ayrıca bkz.

- [Kod oluşturma](../code-generation-in-visual-studio.md)
- [Değişiklikleri Önizle](../../ide/preview-changes.md)
