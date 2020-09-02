---
title: Kaydırma çubuğu eşleme modu ve çubuk modu
ms.date: 03/20/2020
ms.topic: how-to
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5d1b659dabed2337013ffb84ff48277f0edacb09
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85283989"
---
# <a name="how-to-customize-the-scroll-bar"></a>Nasıl yapılır: kaydırma çubuğunu özelleştirme

Uzun kod dosyalarıyla çalışırken her şeyin dosyada nerede olduğunu izlemek zor olabilir. Kodunuzda neler olduğunu bir genel bakış için kod düzenleyicisinin kaydırma çubuğunu özelleştirebilirsiniz.

## <a name="annotations"></a>Ek Açıklamalar

Kaydırma çubuğunun kod değişiklikleri, kesme noktaları, yer işaretleri, hatalar ve giriş işareti konumu gibi ek açıklamaları gösterilip gösterilmeyeceğini belirleyebilirsiniz.

   1. **Scroll Bars** **Araçlar**  >  **Seçenekler**  >  **metin düzenleyici**  >  **tüm diller**  >  **kaydırma çubukları**' nı seçerek kaydırma çubukları Seçenekler sayfasını açın.

   2. **Dikey kaydırma çubuğu üzerinde ek açıklamaları göster**' i seçin ve ardından görmek istediğiniz ek açıklamaları seçin. Kullanılabilir ek açıklamalar şunlardır:

      - değişiklikler
      - işaretler
      - hatalar
      - şapka işareti konumu

      > [!TIP]
      > **Işaretleri göster** seçeneği kesme noktaları ve yer işaretleri içerir.

Büyük bir kod dosyası açarak ve dosyadaki birkaç yerde oluşan bazı metinleri değiştirerek deneyin. Kaydırma çubuğu, değişikliklerinizin etkisini gösterir. bu sayede, sahip olmayan bir şeyi değiştirdiyseniz değişikliklerinizi geri alabilirsiniz.

Bu, bir dize aramadan sonra kaydırma çubuğunun nasıl göründüğünü aşağıda bulabilirsiniz. Dizenin tüm örneklerinin kaydırma çubuğunda göründüğünü unutmayın.

![Dize aramadan sonra Visual Studio kaydırma çubuğu](../ide/media/enhancedscrollbarsearch.png)

Dizenin tüm örnekleri değiştirildikten sonra kaydırma çubuğu. Kaydırma çubuğundaki kırmızı işaretler metin değiştirme hatalarının nerede olduğunu gösterir.

![Bir dizeyi hatalar ile değiştirdikten sonra Visual Studio kaydırma çubuğu](../ide/media/enhancedscrollbarreplace.png)

## <a name="display-modes"></a>Görüntüleme modları

Kaydırma çubuğunun iki modu vardır: çubuk modu ve eşleme modu.

### <a name="bar-mode"></a>Çubuk modu

*Çubuk modu* , kaydırma çubuğundaki ek açıklama göstergelerini görüntüler. Kaydırma çubuğuna tıkladığınızda sayfa yukarı veya aşağı kaydırılır, ancak dosyadaki bu konuma atlamaz.

### <a name="map-mode"></a>Eşleme modu

*Harita modu* , kod satırlarını, kaydırma çubuğunda küçük olarak görüntüler. Eşleme sütununun ne kadar geniş olduğunu seçerek **kaynak genel bakış**' da bir değer seçebilirsiniz. İşaretçiyi haritada tuttuğunuz zaman kodun daha büyük bir önizlemesini etkinleştirmek için **Önizleme araç Ipucunu göster** seçeneğini belirleyin. Daraltılmış bölgeler farklı şekilde genişleyebilir ve çift tıkladığınızda genişletilir.

> [!TIP]
> **Kaynak genel bakışını** **kapalı**olarak ayarlayarak, eşleme modunda küçük kod görünümünü kapatabilirsiniz. **Önizleme araç Ipucunu göster** seçiliyse, işaretçinizi kaydırma çubuğunun üzerine getirdiğinizde bu konumdaki kodun önizlemesini görmeye devam edersiniz ve imleç, tıkladığınızda dosyada bu konuma atlar.

Aşağıdaki görüntüde, harita modu açık olduğunda ve Genişlik **Orta**olarak ayarlandığında arama örneği gösterilmektedir:

![Harita modunda Visual Studio kaydırma çubuğu](../ide/media/enhancedscrollbar.png)

Aşağıdaki görüntüde **Önizleme araç Ipucunu göster** seçeneği gösterilmektedir:

![Araç ipucuyla Visual Studio kaydırma çubuğu](../ide/media/enhancedscrollbarsearchtooltip.png)

> [!TIP]
> Harita modunda gördüğünüz renkleri değiştirmek için **Araçlar**  >  **Seçenekler**  >  **ortam**  >  **yazı tipleri ve renkler**' i seçin. Daha sonra, **görüntüleme öğeleri**' nde, "genel bakış" ile başlayan öğelerden herhangi birini seçin, istediğiniz renk değişikliğini yapın ve ardından **Tamam**' ı seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [Kod düzenleyicisinin özellikleri](../ide/writing-code-in-the-code-and-text-editor.md)
