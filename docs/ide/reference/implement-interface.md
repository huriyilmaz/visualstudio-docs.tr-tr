---
title: Arabirim uygulama
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 7d420bd0d42e89476696966f7eda94a19893fc23
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595559"
---
# <a name="implement-an-interface-in-visual-studio"></a>Visual Studio'da bir arayüz uygulayın

Bu kod oluşturma için geçerlidir:

- C#

- Visual Basic

**Ne:** Bir arabirim uygulamak için gereken kodu hemen oluşturmanıza olanak tanır.

**Ne zaman:** Bir arabirimden devralmak istiyorsunuz.

**Neden:** Tüm arabirimi tek tek elle uygulayabilirsiniz, ancak bu özellik tüm yöntem imzalarını otomatik olarak oluşturur.

## <a name="how-to"></a>Nasıl yapılır

1. İmlecinizi, bir arabirime başvuruyaptığınızı, ancak gerekli tüm üyeleri uygulamadığınızı gösteren kırmızı bir dalgalı çizginin bulunduğu satıra yerleştirin.

   - C#:

       ![Vurgulanan kod C #](media/interface-highlight-cs.png)

   - Visual Basic:

       ![Vurgulanan kod VB](media/interface-highlight-vb.png)

2. Ardından, aşağıdakilerden birini yapın:

   - **Klavye**
      - **Ctrl**+tuşuna**basın.** **Hızlı Eylemler ve Refactorings** menüsünü tetiklemek için.
   - **Fare**
      - Hızlı Eylemler ve **Yeniden Faktörler** menüsünü sağ tıklatın ve seçin.
      - Kırmızı dalgalı üzerinde hover ve tıklayın ![hata ampul](media/error-bulb.png) görünen simge.
      - &nbsp; ![hata ampul](media/error-bulb.png) metin imleci kırmızı dalgalı çizgide yse sol kenar boşluğunda görünen simge.

3. Açılan menüden **Arabirimi Uygula'yı** seçin.

   ![Arayüz önizlemesini uygulayın](media/interface-preview-cs.png)

   > [!TIP]
   > - Seçiminizi yapmadan önce yapılacak [tüm değişiklikleri görmek için](../../ide/preview-changes.md) önizleme penceresinin altındaki Önizleme **değişiklikleri** bağlantısını kullanın.
   > - Arabirimi uygulayan birden çok sınıf arasında uygun yöntem imzaları oluşturmak için önizleme penceresinin altındaki **Belge,** **Proje**ve **Çözüm** bağlantılarını kullanın.

   Arabirimin yöntem imzaları oluşturulur ve uygulanmaya hazırdır.

   - C#:

       ![Arabirim sonucunu C uygulayın #](media/interface-result-cs.png)

   - Visual Basic:

       ![Arayüz sonucunu vb uygulayın](media/interface-result-vb.png)

   > [!TIP]
   > (Yalnızca C# ) Ad çakışmalarını önlemek için oluşturulan her yöntemi arabirim adı ile önsöze getirmek için **Açık Arabirimi Uygula** seçeneğini kullanın.
   >
   > ![Arayüzü açıkça uygulama sonucu](media/interface-explicitresult-cs.png);

## <a name="see-also"></a>Ayrıca bkz.

- [Kod Oluşturma](../code-generation-in-visual-studio.md)
- [Değişiklikleri Önizleme](../../ide/preview-changes.md)
