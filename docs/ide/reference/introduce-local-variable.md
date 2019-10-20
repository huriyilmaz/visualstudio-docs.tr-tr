---
title: Yerel bir değişken tanıtma
description: Varolan bir ifadeyi değiştirmek için yerel bir değişken oluşturun. İfadeyi seçin, sağ tıklayın ve hızlı eylemler ve yeniden düzenlemeler menüsünü seçin, ' expression ' ' ın (tüm oluşumlar) için yerel Ekle ' yi seçin.
ms.date: 01/26/2018
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 6407810b4143d5edacecf42990ae5b6d63497be2
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668749"
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

       ![Vurgulanan kodC#](media/local-highlight-cs.png)

   - Visual Basic:

       ![Vurgulanan kod VB](media/local-highlight-vb.png)

2. Sonra, aşağıdakilerden birini yapın:

   - **Klavyenizdeki**
      - **Ctrl** + tuşuna basın **.** **hızlı eylemleri ve yeniden düzenlemeler** menüsünü tetiklemek için.
   - **Tığında**
      - Sağ tıklayın ve **Hızlı Eylemler ve yeniden düzenlemeler** menüsünü seçin.
      - &nbsp; ![Screwdriver](media/screwdriver.png) Sol kenar boşluğunda görüntülenen simge, metin imleç zaten vurgulanan ifade ile satırda varsa görüntülenir.

   ![Yerel Önizlemeyi göster](media/local-preview-cs.png)

3. Açılan menüden **' expression ' için yerel (tüm oluşumlar) Ekle '** yi seçin.

   > [!TIP]
   > Seçiminizi yapmadan önce yapılacak [tüm değişiklikleri görmek için](../../ide/preview-changes.md) Önizleme penceresinin altındaki **Değişiklikleri Önizle** bağlantısını kullanın.

   Yerel değişken, kullanımından çıkarılan türle oluşturulur. Yeni yerel değişkene yeni bir ad verin.

   - C#:

       ![Arabirim sonucunu UygulaC#](media/local-result-cs.png)

   - Visual Basic:

       ![Arabirim sonucunu Uygula VB](media/local-result-vb.png)

   > [!NOTE]
   > Kullanabilirsiniz...  **tüm oluşumları..** . yalnızca özel olarak vurguladığınız bir ifadeyi değil, seçili ifadenin her örneğini değiştirmek için menü seçeneği.

## <a name="see-also"></a>Ayrıca bkz.

- [Kod oluşturma](../code-generation-in-visual-studio.md)
- [Değişiklikleri Önizle](../../ide/preview-changes.md)