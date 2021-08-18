---
title: Grafik Piksel Geçmişi | Microsoft Docs
description: Belirli bir pikselin geçmişini görerek işleme sorunlarını giderme. Grafik Piksel Geçmişi, Direct3D olaylarının etkilerini gösterir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.graphics.pixelhistory
ms.assetid: 0a2cbde5-1ad9-487e-857c-a3664158c268
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: ed00f0616cc18ce9f2bc73ebbae0927e0c79e990
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122058574"
---
# <a name="graphics-pixel-history"></a>Grafik Piksel Geçmişi
Visual Studio Graphics Analyzer'daki Grafik Piksel Geçmişi penceresi, belirli bir pikselin, oyun veya uygulamanın bir çerçevesi sırasında oluşan Direct3D olaylarının nasıl etkilendiğini anlamanıza yardımcı olur.

 Bu, Piksel Geçmişi penceresidir:

 ![Geçmişinde üç Direct3D olay olan bir piksel.](media/gfx_diag_demo_pixel_history_orientation.png "gfx_diag_demo_pixel_history_orientation")

## <a name="understanding-the-pixel-history-window"></a>Piksel Geçmişi penceresini anlama
 Piksel Geçmişi'ne bakarak, işleme hedefinin belirli bir pikselini bir çerçeve sırasında Direct3D olaylarının nasıl etkilendiğini analiz edersiniz. Sonraki olaylar (veya aynı olayda sonraki temel öğeler) pikselin son renk değerini değiştirmeye devam ediyor olsa bile, belirli bir Direct3D olayına işleme sorununu tespit edersiniz. Örneğin, bir piksel yanlış işlenecek ve ardından renkleri framebuffer içinde bir araya getirilecek şekilde başka bir yarı saydam piksel tarafından obscured olabilir. İşleme hedefinin size rehberlik etmek için yalnızca son içeriğine sahip olsaydık bu tür bir sorunu tanılamak zor olurdu.

 Piksel Geçmişi penceresi, seçilen çerçevenin üzerinde bir pikselin tam geçmişini görüntüler. Pencerenin **üst kısmında** yer alan Son Çerçeve Arabelleği, çerçevenin sonundaki framebuffer'a yazılan rengi ve gelen çerçeve ve ekran koordinatları gibi piksel hakkında ek bilgiler görüntüler. Bu alan ayrıca İşleme **Alfası onay** kutusunu da içerir. Bu onay kutusu seçildiğinde, Son **Çerçeve** AraBelleği rengi ve ara renk değerleri, denetleyici panosu deseni üzerinde saydamlık ile görüntülenir. Onay kutusu temizse renk değerlerinin alfa kanalı yoksayılır.

 Pencerenin alt kısmında pikselin rengini etkileme şansına sahip olan olaylar, framebuffer  içinde pikselin ilk ve son renk değerlerini temsil eden Başlangıç ve Son sahte olaylar ile birlikte görüntülenir.  İlk renk değeri, pikselin rengini değiştiren ilk olay (genellikle bir olay) tarafından `Clear` belirlenir. Bir pikselin geçmişinde bu iki sahte olay vardır ve bundan etkilenecek başka bir olay yoktur. Pikseli etkileme şansı olan diğer olaylar, İlk ve Son **olayları arasında** **görüntülenir.** Olaylar ayrıntılarını gösterecek şekilde genişletilebilir. İşleme hedefini temizleyeneler gibi basit olaylar için olayın etkisi yalnızca bir renk değeridir. Draw çağrıları gibi daha karmaşık olaylar pikselin rengine katkıda bulunarak bir veya daha fazla temel öğe üretir.

 Olay tarafından çizilen ilkeller, nesne için toplam ilkel sayısıyla birlikte ilkel tür ve dizinleriyle tanımlanır. Örneğin, **(6214) Üçgen (1456)** gibi bir tanımlayıcı, ilkelin 6214 üçgenden oluşan bir nesnede 1456. üçgene karşılık geldiğini gösterir. Her ilkel tanımlayıcının sol tarafta, ilkelin piksel üzerindeki etkisini özetleyen bir simge yer almaktadır. Piksel rengini etkileyen temel öğeler, sonuç rengiyle doldurulmuş yuvarlanmış bir dikdörtgenle temsil eder. Piksel renginin etkisinden dışlanan temel öğeler, pikselin dışlama nedenini belirten simgelerle temsil eder. Bu simgeler, bu makalenin sonraki [kısımlarında temel dışlama](#exclusion) bölümünde açıklanmıştır.

 Piksel gölgelendiricisi çıktısını mevcut piksel rengiyle birleştirmiş ve sonuç rengini nasıl üreteceklerini incelemek için her bir temele genişletebilirsiniz. Buradan temel öğeyle ilişkili piksel gölgelendiricisi kodunu inceler veya hata ayıklar ve köşe gölgelendiricisi girişini incelemek için köşe gölgelendirici düğümünü daha da genişletebilirsiniz.

### <a name="primitive-exclusion"></a><a name="exclusion"></a> İlkel dışlama
 Bir temel öğe piksel rengini etkilemeden dışlanmışsa, dışlama çeşitli nedenlerle oluşabilir. Her neden, bu tabloda açıklanan bir simgeyle gösterilir:

|Simge|Dışlama nedeni|
|----------|--------------------------|
|![Derinlik testi hatası simgesi.](media/vsg_hist_icon_failed_depth.png "vsg_hist_icon_failed_depth")|Piksel, derinlik testinde başarısız olduğu için dışlandı.|
|![Scissor test hatası simgesi.](media/vsg_hist_icon_failed_scissor.png "vsg_hist_icon_failed_scissor")|Piksel, scissor testinde başarısız olduğu için dışlandı.|
|![Kalıp testi hatası simgesi.](media/vsg_hist_icon_failed_stencil.png "vsg_hist_icon_failed_stencil")|Piksel, şablon testinde başarısız olduğu için dışlandı.|

### <a name="draw-call-exclusion"></a>Draw Çağrı Dışlama
 Bir çizim çağrısında yer alan temel öğeler, bir testte başarısız olduğu için işleme hedefini etkilemeden hariç tutulacaksa, çizim çağrısı genişletilamaz ve dışlamanın nedenini karşılık gelen bir simge yanında görüntülenir. Draw-call dışlama nedenleri ilkel dışlama nedenlerine benzer ve simgeleri benzerdir.

### <a name="viewing-and-debugging-shader-code"></a>Gölgelendirici kodunu görüntüleme ve hata ayıklama
 Gölgelendiriciyle ilişkili temel öğenin altındaki denetimleri kullanarak köşe, köşe, etki alanı, geometri ve piksel gölgelendiricileri için kodu inceleyebilirsiniz ve kodda hata ayıkabilirsiniz.

##### <a name="to-view-a-shaders-source-code"></a>Gölgelendiricinin kaynak kodunu görüntülemek için

1. Grafik **Piksel Geçmişi penceresinde,** incelemek ve genişletmek istediğiniz gölgelendiriciye karşılık gelen çizim çağrısını bulun.

2. Az önce genişletmiş olduğunuz draw çağrısının altında ilgilendiğimiz sorunu gösteren bir temel öğe seçin ve genişletin.

3. İlgilenilen temel öğenin altında gölgelendirici başlığı bağlantısını izleyin; örneğin köşe gölgelendiricisi kaynak kodunu görüntülemek için **Köşe Gölgelendiricisi obj:30** bağlantısını izleyin.

    > [!TIP]
    > **obj:30** nesne numarası, nesne tablosu ve işlem hattı aşamaları penceresinde olduğu gibi Grafik Çözümleyicisi arabiriminde bu gölgelendiriciyi tanımlar.

##### <a name="to-debug-a-shader"></a>Gölgelendiricide hata ayıklamak için

1. Grafik **Piksel Geçmişi penceresinde,** incelemek ve genişletmek istediğiniz gölgelendiriciye karşılık gelen çizim çağrısını bulun.

2. Ardından, az önce genişletmiş olduğunuz draw çağrısının altında ilgilendiğimiz sorunu gösteren bir temel öğe seçin ve genişletin.

3. İlgilenin temel öğenin altında Hata Ayıklamayı **Başlat'ı seçin.** HLSL hata ayıklayıcısına bu giriş noktası, karşılık gelen ilkel için gölgelendiricinin ilk çağrılarak varsayılan olarak gölgelendirici tarafından işlenen ilk pikseli veya köşeyi kullanır. Temel öğeyle ilişkilendirilmiş yalnızca bir piksel vardır, ancak çizgiler ve üçgenler için birden fazla köşe gölgelendiricisi çağrıları vardır.

     Belirli bir köşe için köşe gölgelendiricisi çağırmada hata ayıklamak için, VertexShader başlık bağlantısını genişletin ve  ilgilendiğiniz köşeyi bulun ve yanındaki Hata Ayıklamayı Başlat'ı seçin.

### <a name="links-to-graphics-objects"></a>Grafik nesnelerine bağlantılar
 Piksel geçmişinde grafik olaylarını anlamak için, olay sırasında cihaz durumu veya olay tarafından başvurulan Direct3D nesneleri hakkında bilgilere ihtiyacınız olabilir. Piksel geçmişinde yer alan her olay için Grafik **Piksel Geçmişi,** o zaman geçerli olan cihaz durumuna ve ilgili nesnelere bağlantılar sağlar.

## <a name="see-also"></a>Ayrıca bkz.
- [İzlenecek yol: Cihaz Durumu Nedeniyle Eksik Nesneler](walkthrough-missing-objects-due-to-device-state.md)
- [İzlenecek yol: Gölgeleme Nedeniyle Çıkan Oluşturma Hatalarını Ayıklama](walkthrough-debugging-rendering-errors-due-to-shading.md)