---
title: Yerel değişkeni tanıtın
description: Varolan bir ifadenin yerine yerel bir değişken oluşturun. İfadeyi seçin, sağ tıklayın ve Hızlı Eylemler ve Yeniden Faktörler menüsünü seçin, 'ifade' için yerel tanıt'ı seçin.
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 0fbd5ed752b28cc3f8c0dd734ed2b3ce09e80b78
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75568821"
---
# <a name="introduce-a-local-variable-in-visual-studio"></a>Visual Studio'da yerel bir değişkeni tanıtın

Bu kod oluşturma için geçerlidir:

- C#

- Visual Basic

**Ne:** Varolan bir ifadeyi değiştirmek için hemen yerel bir değişken oluşturmanıza olanak tanır.

**Ne zaman:** Yerel bir değişkende olsaydı daha sonra kolayca yeniden kullanılabilecek bir kodunuz vardır.

**Neden:** Kodu çeşitli konumlarda kullanmak için birden çok kez kopyalayıp yapıştırabilirsiniz, ancak işlemi bir kez gerçekleştirmek, sonucu yerel bir değişkende depolamak ve yerel değişkeni kullanmak daha iyi olacaktır.

## <a name="how-to"></a>Nasıl yapılır

1. Yeni bir yerel değişkene atamak istediğiniz ifadeyi vurgulayın.

   - C#:

       ![Vurgulanan kod C #](media/local-highlight-cs.png)

   - Visual Basic:

       ![Vurgulanan kod VB](media/local-highlight-vb.png)

2. Ardından, aşağıdakilerden birini yapın:

   - **Klavye**
      - **Ctrl**+tuşuna**basın.** **Hızlı Eylemler ve Refactorings** menüsünü tetiklemek için.
   - **Fare**
      - Hızlı Eylemler ve **Yeniden Faktörler** menüsünü sağ tıklatın ve seçin.
      - &nbsp; ![Tornavida](media/screwdriver.png) metin imleci vurgulanan ifadeyle zaten çizgideyse sol kenar boşluğunda görünen simge.

   ![Yerel önizlemeyi tanıtın](media/local-preview-cs.png)

3. Açılan menüden **'ifade' için yerel tanıt 'ı seçin.**

   > [!TIP]
   > Seçiminizi yapmadan önce yapılacak [tüm değişiklikleri görmek için](../../ide/preview-changes.md) önizleme penceresinin altındaki Önizleme **değişiklikleri** bağlantısını kullanın.

   Yerel değişken, kullanımından çıkarılan türle oluşturulur. Yeni yerel değişkene yeni bir ad verin.

   - C#:

       ![Arabirim sonucunu C uygulayın #](media/local-result-cs.png)

   - Visual Basic:

       ![Arayüz sonucunu vb uygulayın](media/local-result-vb.png)

   > [!NOTE]
   > Kullanabilirsiniz **... tüm oluşumları ...** yalnızca özellikle vurgulamış olduğunuz ifadeyi değil, seçili ifadenin her örneğini değiştirmek için menü seçeneği.

## <a name="see-also"></a>Ayrıca bkz.

- [Kod oluşturma](../code-generation-in-visual-studio.md)
- [Değişiklikleri önizleme](../../ide/preview-changes.md)
