---
title: Çubuk harita modunu ve çubuk modunu kaydırma
ms.date: 03/20/2020
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c66cda1b90d11a44f744faf0012a3e41212d33dd
ms.sourcegitcommit: f8e3715c64255b476520bfa9267ceaf766bde3b0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/21/2020
ms.locfileid: "79988571"
---
# <a name="how-to-customize-the-scroll-bar"></a>Nasıl yapılsın: Kaydırma çubuğunu özelleştirin

Uzun kod dosyalarıyla çalışırken, her şeyin dosyada nerede olduğunu izlemek zor olabilir. Kod düzenleyicinin kaydırma çubuğunu özelleştirebileceğiniz şekilde kodunuzda neler olup bittiğine genel bir resim verebilirsiniz.

## <a name="annotations"></a>Ek Açıklamalar

Kaydırma çubuğunun kod değişiklikleri, kesme noktaları, yer imleri, hatalar ve bakım konumu gibi ek açıklamaları gösterip göstermediğini seçebilirsiniz.

   1. **Araçlar** > **Text Editor** > **All Languages** >  **Scroll Bars**  > **Seçenekleri**Metin Düzenleyici tüm Diller**kaydırma Çubukları**seçerek Kaydırma Çubukları seçenekleri sayfasını açın.

   2. **Dikey kaydırma çubuğunda Ek Açıklamaları Göster'i**seçin ve ardından görmek istediğiniz ek açıklamaları seçin. Kullanılabilir ek açıklamalar şunlardır:

      - değişiklikler
      - işaretler
      - hatalar
      - caret pozisyonu

      > [!TIP]
      > **İşaretleri Göster** seçeneği kesme noktalarını ve yer imlerini içerir.

Büyük bir kod dosyasını açarak ve dosyanın çeşitli yerlerinde oluşan bazı metinleri değiştirerek deneyin. Kaydırma çubuğu değiştirmelerin etkisini gösterir, böylece değiştirmemeniz gereken bir şeyi değiştirirseniz değişikliklerinizi geri çekebilirsiniz.

Bir dize için yapılan aramadan sonra kaydırma çubuğu şu şekilde görünür. Dize deki tüm örneklerin kaydırma çubuğunda göründüğüne dikkat edin.

![Bir dize aradıktan sonra Visual Studio kaydırma çubuğu](../ide/media/enhancedscrollbarsearch.png)

Dizedeki tüm örnekleri değiştirdikten sonra kaydırma çubuğu nu burada bulabilirsiniz. Kaydırma çubuğundaki kırmızı işaretler, metin değiştirmenin hataları tanıttığını gösterir.

![Bir dizeyi hatalarla değiştirdikten sonra Visual Studio kaydırma çubuğu](../ide/media/enhancedscrollbarreplace.png)

## <a name="display-modes"></a>Görüntü modları

Kaydırma çubuğunun iki modu vardır: çubuk modu ve harita modu.

### <a name="bar-mode"></a>Çubuk modu

*Çubuk modu* kaydırma çubuğunda ek açıklama göstergelerini görüntüler. Kaydırma çubuğuna tıkladığınızda sayfa yukarı veya aşağı kaydırılır, ancak dosyadaki o konuma atlamaz.

### <a name="map-mode"></a>Harita modu

*Harita modu,* kaydırma çubuğunda kod satırlarını minyatür olarak görüntüler. **Kaynak'a genel bakış'ta**bir değer seçerek harita sütununne ne kadar geniş olduğunu seçebilirsiniz. İşaretçiyi haritada dinlendirdiğinizde kodun daha büyük bir önizlemesini etkinleştirmek için **Önizleme Araç İpucu** seçeneğini belirleyin. Daraltılmış bölgeler farklı şekilde gölgelenir ve çift tıklattığınızda genişletilir.

> [!TIP]
> **Kaynak genel görünümünü** **Kapalı**olarak ayarlayarak harita modunda minyatür kod görünümünü kapatabilirsiniz. **Önizleme Araç İpucunu Göster** seçilirse, işaretçinizin kaydırma çubuğunda gezinmesini yaptığınızda o konumda kodun önizlemesini görmeye devam edeyim ve bunu tıklattığınızda imleç yine de dosyadaki o konuma atlar.

Aşağıdaki resim, harita modu açılırken ve genişlik **Orta**olarak ayarlandığında arama örneğini gösterir:

![Harita modunda Visual Studio kaydırma çubuğu](../ide/media/enhancedscrollbar.png)

Aşağıdaki resimde **Önizleme Araç İpucu** göster seçeneği gösterilmektedir:

![Araç ucu yla Visual Studio kaydırma çubuğu](../ide/media/enhancedscrollbarsearchtooltip.png)

> [!TIP]
> Harita modunda gördüğünüz renkleri değiştirmek **için, Araçlar** > **Seçenekleri** > **Ortamı** > **Yazı Tipleri ve Renkleri'ni**seçin. Ardından, **Görüntü öğelerinde**, "Genel Bakış" ile önce gelen öğelerden herhangi birini seçin, istediğiniz renk değişikliklerini yapın ve ardından **Tamam'ı**seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [Kod düzenleyicisinin özellikleri](../ide/writing-code-in-the-code-and-text-editor.md)
