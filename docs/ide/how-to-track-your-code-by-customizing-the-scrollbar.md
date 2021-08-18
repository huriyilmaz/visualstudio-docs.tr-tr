---
title: Kaydırma çubuğu harita modu ve çubuk modu
description: Kaydırma çubuğunu özelleştirme yoluyla kodundaki değişiklikleri izlemenin yanı sıra Çubuk modu ve Harita modunu kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 03/20/2020
ms.topic: how-to
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: eb56e1dfe2e5410761fc52e2c9edc5fa04095b91
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122086020"
---
# <a name="how-to-customize-the-scroll-bar"></a>Nasıl: Kaydırma çubuğunu özelleştirme

Uzun kod dosyalarıyla çalışırken, her şeyin dosyada nerede olduğunu izlemek zor olabilir. Kod düzenleyicinin kaydırma çubuğunu özelleştirebilirsiniz. Bu çubuk, kodunda neler olduğunu size genel bir şekilde anlatabilir.

## <a name="annotations"></a>Ek Açıklamalar

Kaydırma çubuğunda kod değişiklikleri, kesme noktaları, yer işaretleri, hatalar ve dikkat işareti konumu gibi ek açıklamaların gösterip gösterile olmadığını seçin.

   1. Araç Seçenekleri **Metin Düzenleyici Tüm** Diller Kaydırma **Çubukları'ni**  >    >    >  **seçerek Kaydırma Çubukları seçenekler** sayfasını  >  **açın.**

   2. Dikey **kaydırma çubuğunun üzerinde Ek Açıklamaları Göster'i** seçin ve ardından görmek istediğiniz ek açıklamaları seçin. Kullanılabilir ek açıklamalar:

      - değişiklikler
      - işaretler
      - hatalar
      - caret konumu

      > [!TIP]
      > İşaretleri **göster** seçeneği kesme noktaları ve yer işaretleri içerir.

Büyük bir kod dosyası açarak ve dosyanın çeşitli yerlerinde oluşan bazı metinleri değiştirerek bunu deneyin. Kaydırma çubuğu, değiştirmelerin etkisini gösterir. Bu nedenle, değiştirme yapmamanız gereken bir şeyi değiştirmeniz gerekirse değişikliklerinizi geri çıkarabilirsiniz.

Kaydırma çubuğunun bir dize araması sonrasında nasıl göründüğünü görmek için aşağıdakini kullanın. Dizenin tüm örneklerinin kaydırma çubuğunda görünür.

![Visual Studio bir dizeyi aratınktan sonra kaydırma çubuğunu seçin](../ide/media/enhancedscrollbarsearch.png)

Dizenin tüm örneklerini değiştirdikten sonra kaydırma çubuğu aşağıdaki gibi olur. Kaydırma çubuğundaki kırmızı işaretler, metin değiştirmenin hatalara neden olduğu yeri gösterir.

![Visual Studio bir dizeyi hatalarla değiştirdikten sonra kaydırma çubuğunu değiştirme](../ide/media/enhancedscrollbarreplace.png)

## <a name="display-modes"></a>Görüntüleme modları

Kaydırma çubuğunun iki modu vardır: çubuk modu ve harita modu.

### <a name="bar-mode"></a>Çubuk modu

*Çubuk modu,* kaydırma çubuğunda ek açıklama göstergeleri görüntüler. Kaydırma çubuğuna tıklarsanız sayfa yukarı veya aşağı kaydırılabilir ancak dosyada bu konuma atlanmaz.

### <a name="map-mode"></a>Eşleme modu

*Harita modu,* kaydırma çubuğunda kod satırlarını görüntüler. Kaynak genel bakış'ta bir değer seçerek eşleme sütununu ne kadar geniş **olduğunu seçebilirsiniz.** İşaretçiyi haritada dinleniyorken kodun daha büyük bir önizlemesini etkinleştirmek için Önizleme Araç **İpucu'nı Göster seçeneğini** belirleyin. Daraltılmış bölgeler farklı şekilde gölgeli olur ve çift tıklarken genişler.

> [!TIP]
> Kaynak genel bakış ayarını Kapalı olarak ayarerek harita modunda kod görünümünü **kapatabilirsiniz.**  Önizleme **Araç** İpucu göster seçeneği seçiliyse, işaretçinizi kaydırma çubuğuna yerleştirerek ilgili konumdaki kodun önizlemesini görmeye devam edersiniz ve imleç, tıklarsanız dosyada o konuma atlar.

Aşağıdaki görüntüde harita modu ve genişliği Orta olarak ayarlanmış arama örneği **gösterilir:**

![Visual Studio modunda kaydırma çubuğu](../ide/media/enhancedscrollbar.png)

Aşağıdaki görüntüde Önizleme **Araç İpucu göster seçeneği görüntülenir:**

![Visual Studio ipucuyla kaydırma çubuğu](../ide/media/enhancedscrollbarsearchtooltip.png)

> [!TIP]
> Harita modunda gördüğünüz renkleri değiştirmek için Araçlar Seçenekler Ortam Yazı Tipleri **ve**  >    >    >  **Renkler'i seçin.** Ardından, **Öğeleri görüntüle'de**, "Genel Bakış" ile önce gelen öğelerden herhangi birini seçin, istediğiniz renk değişikliklerini yapın ve ardından Tamam'ı **seçin.**

## <a name="see-also"></a>Ayrıca bkz.

- [Kod düzenleyicisinin özellikleri](../ide/writing-code-in-the-code-and-text-editor.md)
