---
title: Soyut bir sınıf uygulama
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 6fcfdc06a055df28159f9d1ddc440aaf113f3264
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75568912"
---
# <a name="implement-an-abstract-class-in-visual-studio"></a>Visual Studio'da soyut bir sınıf uygulayın

Bu kod oluşturma için geçerlidir:

- C#

- Visual Basic

**Ne:** Soyut bir sınıf uygulamak için gereken kodu hemen oluşturmanıza olanak tanır.

**Ne zaman:** Soyut bir sınıftan miras almak istiyorsunuz.

**Neden:** Tüm soyut üyeleri tek tek el ile uygulayabilirsiniz, ancak bu özellik tüm yöntem imzalarını otomatik olarak oluşturur.

## <a name="how-to"></a>Nasıl yapılır

1. İmlecinizi, soyut bir sınıftan devraldığınızı ancak gerekli tüm üyeleri uygulamadığınızı gösteren kırmızı bir dalgalı ğın olduğu çizgiye yerleştirin.

   - C#:

       ![Vurgulanan kod C #](media/abstract-highlight-cs.png)

   - Visual Basic:

       ![Vurgulanan kod VB](media/abstract-highlight-vb.png)

2. Ardından, aşağıdakilerden birini yapın:

   - **Klavye**
      - **Ctrl**+tuşuna**basın.** **Hızlı Eylemler ve Refactorings** menüsünü tetiklemek için.
   - **Fare**
      - Hızlı Eylemler ve **Yeniden Faktörler** menüsünü sağ tıklatın ve seçin.
      - Kırmızı dalgalı üzerinde hover ve tıklayın ![hata ampul](media/error-bulb.png) görünen simge.
      - &nbsp; ![hata ampul](media/error-bulb.png) metin imleci kırmızı dalgalı çizgide yse sol kenar boşluğunda görünen simge.

   ![Sınıf önizlemesini uygulama](media/abstract-preview-cs.png)

3. Açılan menüden **Soyut Sınıfı Uygula'yı** seçin.

   > [!TIP]
   > - Seçiminizi yapmadan önce yapılacak [tüm değişiklikleri görmek için](../../ide/preview-changes.md) önizleme penceresinin altındaki Önizleme **değişiklikleri** bağlantısını kullanın.
   > - Özet sınıftan devralan birden çok sınıf arasında uygun yöntem imzaları oluşturmak için önizleme penceresinin altındaki **Belge,** **Proje**ve **Çözüm** bağlantılarını kullanın.

   Soyut yöntem imzaları oluşturulur ve uygulanmaya hazırdır.

   - C#:

       ![C sınıfı sonucunu uygulama #](media/abstract-result-cs.png)

   - Visual Basic:

       ![Sınıf sonucunu vb uygulayın](media/abstract-result-vb.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Kod Oluşturma](../code-generation-in-visual-studio.md)
- [Değişiklikleri Önizleme](../../ide/preview-changes.md)
