---
title: Kaydırma çubuğu eşleme modu ve çubuk modu
ms.date: 09/25/2018
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 22436c221813ec4c3701d208fc74a96b403fff9c
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591404"
---
# <a name="how-to-customize-the-scroll-bar"></a>Nasıl yapılır: kaydırma çubuğunu özelleştirme

Uzun kod dosyalarıyla çalışırken her şeyin dosyada nerede olduğunu izlemek zor olabilir. Kodunuzda neler olduğunu bir genel bakış için kod düzenleyicisinin kaydırma çubuğunu özelleştirebilirsiniz.

## <a name="annotations"></a>Ek Açıklamalar

Kaydırma çubuğunun kod değişiklikleri, kesme noktaları, yer işaretleri, hatalar ve giriş işareti konumu gibi ek açıklamaları gösterilip gösterilmeyeceğini belirleyebilirsiniz.

   1. **Tüm diller** > **kaydırma çubukları** > **Araçlar** > **Seçenekler** > **metin Düzenleyicisi** ' ni seçerek **kaydırma çubukları** seçenekleri sayfasını açın.

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

*Harita modunda*, kaydırma çubuğundaki bir konuma tıkladığınızda, imleç yalnızca bir sayfada yukarı veya aşağı kaydırmak yerine dosyada bu konuma atlar. Kod satırları, kaydırma çubuğunda küçük olarak gösterilir. Eşleme sütununun ne kadar geniş olduğunu seçerek **kaynak genel bakış**' da bir değer seçebilirsiniz. İşaretçiyi haritada tuttuğunuz zaman kodun daha büyük bir önizlemesini etkinleştirmek için **Önizleme araç Ipucunu göster** seçeneğini belirleyin. Daraltılmış bölgeler farklı şekilde genişleyebilir ve çift tıkladığınızda genişletilir.

> [!TIP]
> **Kaynak genel bakışını** **kapalı**olarak ayarlayarak, eşleme modunda küçük kod görünümünü kapatabilirsiniz. **Önizleme araç Ipucunu göster** seçiliyse, işaretçinizi kaydırma çubuğunun üzerine getirdiğinizde bu konumdaki kodun önizlemesini görmeye devam edersiniz ve imleç, tıkladığınızda dosyada bu konuma atlar.

Aşağıdaki görüntüde, harita modu açık olduğunda ve Genişlik **Orta**olarak ayarlandığında arama örneği gösterilmektedir:

![Harita modunda Visual Studio kaydırma çubuğu](../ide/media/enhancedscrollbar.png)

Aşağıdaki görüntüde **Önizleme araç Ipucunu göster** seçeneği gösterilmektedir:

![Araç ipucuyla Visual Studio kaydırma çubuğu](../ide/media/enhancedscrollbarsearchtooltip.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Kod Düzenleyicisi özellikleri](../ide/writing-code-in-the-code-and-text-editor.md)
