---
title: Arabirim uygulama
description: Bir arabirimi uygulamak için gereken kodu hemen oluşturmak için Hızlı Eylemler ve Yeniden Düzenleme menüsünü kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- dotnet
ms.openlocfilehash: ef769394bafd1727ac16f4dbaadf6e6ca27c7e77
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122101329"
---
# <a name="implement-an-interface-in-visual-studio"></a>Visual Studio'da arabirim uygulama

Bu kod oluşturma aşağıdakiler için geçerlidir:

- C#

- Visual Basic

**Ne:** Bir arabirimi uygulamak için gereken kodu hemen oluşturmana olanak sağlar.

**Ne zaman:** Bir arabirimden devralmak istediğiniz.

**Neden:** Tüm arabirimi tek tek el ile uygulayabilirsiniz, ancak bu özellik tüm yöntem imzalarını otomatik olarak üretir.

## <a name="how-to"></a>Nasıl yapılır

1. İmlecinizi bir arabirime başvurarak tüm gerekli üyeleri uygulamamış olduğunu belirten kırmızı bir geçişin bulunduğu satıra yerleştirebilirsiniz.

   - C#:

       ![Vurgulanan kod C #](media/interface-highlight-cs.png)

   - Visual Basic:

       ![Vurgulanan kod VB](media/interface-highlight-vb.png)

2. Ardından, aşağıdakilerden birini yapın:

   - **Klavye**
      - **Ctrl tuşuna** + **basın.** Hızlı Eylemler **ve Yeniden Düzenleme menüsünü tetiklemek** için.
   - **Fare**
      - Sağ tıklayın ve Hızlı **Eylemler ve Yeniden Düzenleme menüsünü** seçin.
      - Kırmızı çizginin üzerine gelin ve ![hata ampulü](media/error-bulb.png) simgesi görüntülenir.
      - Sağ üst köşedeki ![hata ampulü](media/error-bulb.png) simgesi, metin imleci kırmızı çizgiyle çizgi üzerinde zaten varsa sol kenar boşluğunda görünür.

3. Açılan **menüden** Arabirimi uygulay'ı seçin.

   ![Arabirim önizlemesini uygulama](media/interface-preview-cs.png)

   > [!TIP]
   > - Seçiminizi **yapmadan** önce yapılacak tüm değişiklikleri görmek için önizleme penceresinin [altındaki](../../ide/preview-changes.md) Değişiklikleri önizle bağlantısını kullanın.
   > - Arabirimi **uygulayan** **birden çok** sınıfta  uygun yöntem imzalarını oluşturmak için önizleme penceresinin altındaki Belge , Project ve Çözüm bağlantılarını kullanın.

   Arabirimin yöntem imzaları oluşturulur ve uygulanmaya hazırdır.

   - C#:

       ![Arabirim sonucu uygulama C #](media/interface-result-cs.png)

   - Visual Basic:

       ![Arabirim sonucu uygulama VB](media/interface-result-vb.png)

   > [!TIP]
   > (yalnızca C# ) Oluşturulan **her yöntemin önüne** ad çakışmalarını önlemek için Arabirimi açıkça uygulama seçeneğini kullanın.
   >
   > ![Arabirimi açıkça uygulama sonucu](media/interface-explicitresult-cs.png);

## <a name="see-also"></a>Ayrıca bkz.

- [Kod Oluşturma](../code-generation-in-visual-studio.md)
- [Değişiklikleri Önizleme](../../ide/preview-changes.md)
