---
title: Grafik piksel geçmişi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.graphics.pixelhistory
ms.assetid: 0a2cbde5-1ad9-487e-857c-a3664158c268
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8cb1b7a869915eebc561e1baf47082dd5dbc00df
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72735483"
---
# <a name="graphics-pixel-history"></a>Grafik Piksel Geçmişi
Visual Studio Grafik Çözümleyicisi grafik piksel geçmişi penceresi, belirli bir pikselin, oyununuzun veya uygulamanızın bir çerçevesinde gerçekleşen Direct3D olaylarından nasıl etkilendiğini anlamanıza yardımcı olur.

 Bu, piksel geçmişi penceresidir:

 ![Geçmişinde üç Direct3D olayına sahip bir piksel.](media/gfx_diag_demo_pixel_history_orientation.png "gfx_diag_demo_pixel_history_orientation")

## <a name="understanding-the-pixel-history-window"></a>Piksel Geçmişi penceresini anlama
 Piksel geçmişi 'ni kullanarak, oluşturma hedefinin belirli bir pikselin bir çerçeve sırasında Direct3D olaylarından nasıl etkileneceği analiz edebilirsiniz. Bir işleme sorununu, sonraki olaylar veya aynı olaydaki sonraki temel öğeler gibi belirli bir Direct3D olayına, pikselin son renk değerini değiştirmeye devam edebilirsiniz. Örneğin, bir piksel yanlış bir şekilde oluşturulabilir ve sonra renkleri framebuffer içinde karışarak başka bir yarı saydam piksel tarafından görünmeyebilir. Bu tür bir sorun, size rehberlik etmek için yalnızca oluşturma hedefinin son içeriğine sahip olup olmadığını tanılamak zor olabilir.

 Piksel geçmişi penceresi, seçilen karenin kursu boyunca bir pikselin tamamlanma geçmişini görüntüler. Pencerenin üst kısmındaki **son çerçeve arabelleği** , çerçevenin sonundaki framebuffer ile birlikte gelen ve ekran koordinatları gibi piksel hakkındaki ek bilgilerle yazılmış olan rengi görüntüler. bu Bu alan ayrıca **Alfa Oluştur** onay kutusunu da içerir. Bu onay kutusu seçildiğinde, **son kare arabelleği** rengi ve ara renk değerleri bir dama tahtası deseninin üzerinde saydamlıkla görüntülenir. Onay kutusu silinirse, renk değerlerinin alfa kanalı yok sayılır.

 Pencerenin alt kısmında, framebuffer 'ın başlangıçtaki ve nihai renk değerlerini temsil eden **ilk** ve **son** sözde etkinliklerle birlikte piksel rengini etkileyen bir şansınız olan olaylar görüntülenir. İlk renk değeri, pikselin rengini değiştiren ilk olay tarafından belirlenir (genellikle bir `Clear` olay). Başka hiçbir olay etkilenmedikleri zaman bile, bir piksel geçmişinde bu iki sözde olaya her zaman sahiptir. Diğer olayların pikseli etkileme şansı varsa, bunlar **ilk** ve **son** olaylar arasında görüntülenir. Olayları, ayrıntılarını göstermek için genişletilebilir. Bir işleme hedefini temizleyecek olanlar gibi basit olaylar için, etkinliğin etkisi yalnızca bir renk değeridir. Çizim çağrıları gibi daha karmaşık olaylar, pikselin rengine katkıda bulunan bir veya daha fazla temel oluşturur.

 Olay tarafından çizilen temel elemanlar, nesne için toplam temel sayı ile birlikte temel tür ve dizinleriyle tanımlanır. Örneğin, **üçgen (1456)/(6214)** gibi bir tanımlayıcı, ilkel öğenin, 6214 üçgenden oluşan bir nesne içindeki 1456th üçgene karşılık geldiği anlamına gelir. Her ilkel tanımlayıcının solunda, ilkel öğenin piksel üzerinde sahip olduğu etkiyi özetleyen bir simge bulunur. Piksel rengini etkileyen temel elemanlar, sonuç rengiyle doldurulmuş bir yuvarlatılmış dikdörtgen tarafından temsil edilir. Piksel rengi üzerinde bir etkiye sahip olmanın dışında bırakılan temel elemanlar, pikselin dışlanmasının neden olduğunu belirten simgelerle temsil edilir. Bu simgeler, bu makalenin ilerleyen kısımlarında bölüm [temel dışlama](#exclusion) bölümünde açıklanmaktadır.

 Her bir temel genişleterek, piksel gölgelendirici çıkışının, sonuç rengini oluşturmak için mevcut piksel rengi ile nasıl birleştirildiğini inceleyebilirsiniz. Buradan, temel ile ilişkili piksel gölgelendirici kodunu inceleyebilir veya hata ayıklayın ve köşe gölgelendirici girişini incelemek için köşe gölgelendirici düğümünü daha da genişletebilirsiniz.

### <a name="primitive-exclusion"></a><a name="exclusion"></a> Temel dışlama
 Bir temel değer piksel rengini etkilemeden dışlanmazsa, dışlama çeşitli nedenlerle meydana gelebilir. Her neden, bu tabloda açıklanan bir simgeyle temsil edilir:

|Simge|Dışlama nedeni|
|----------|--------------------------|
|![Derinlik testi hatası simgesi.](media/vsg_hist_icon_failed_depth.png "vsg_hist_icon_failed_depth")|Derinlik testinde başarısız olduğu için piksel dışarıda bırakıldı.|
|![Makas test hatası simgesi.](media/vsg_hist_icon_failed_scissor.png "vsg_hist_icon_failed_scissor")|Makas testinde başarısız olduğu için piksel dışarıda bırakıldı.|
|![Kalıp test hatası simgesi.](media/vsg_hist_icon_failed_stencil.png "vsg_hist_icon_failed_stencil")|Kalıp testinde başarısız olduğu için piksel dışarıda bırakıldı.|

### <a name="draw-call-exclusion"></a>Çağrı dışlamasını çiz
 Bir çizim çağrısındaki tüm temel elemanlar, test başarısız olduğu için işleme hedefini etkilediğinden dışlanmazsa, çizim çağrısı genişletilemiyor ve öğenin yanında dışlama nedenine karşılık gelen bir simge gösterilir. Beraberlik-Call dışlamanın nedenleri, temel dışlamanın nedenlerini ve bunların simgeleri benzerdir.

### <a name="viewing-and-debugging-shader-code"></a>Gölgelendirici kodunu görüntüleme ve hata ayıklama
 Gölgelendirici ile ilişkili temel öğe altındaki denetimleri kullanarak köşe, Hull, etki alanı, geometri ve Piksel gölgelendiricileri için kodu inceleyebilir ve hata ayıklama yapabilirsiniz.

##### <a name="to-view-a-shaders-source-code"></a>Gölgelendirici kaynak kodunu görüntülemek için

1. **Grafik piksel geçmişi** penceresinde, incelemek istediğiniz gölgelendiriciye karşılık gelen çizim çağrısını bulun ve genişletin.

2. Yeni genişleteceğiniz çizim çağrısının altında ilgilendiğiniz sorunu gösteren bir temel seçin ve genişletin.

3. İlgilendiğiniz temel öğe altında, gölgelendirici başlığı bağlantısını izleyin. Örneğin, köşe gölgelendirici kaynak kodunu görüntülemek için, bkz **: 30 bağlantı köşe** gölgelendiricisi.

    > [!TIP]
    > Nesne numarası, **obj: 30**, bu gölgelendiriciyi nesne tablosu ve ardışık düzen aşamaları penceresinde olduğu gibi grafik Çözümleyicisi arabirimi boyunca tanımlar.

##### <a name="to-debug-a-shader"></a>Gölgelendiricide hata ayıklamak için

1. **Grafik piksel geçmişi** penceresinde, incelemek istediğiniz gölgelendiriciye karşılık gelen çizim çağrısını bulun ve genişletin.

2. Ardından, az önce genişleteceğiniz çizim çağrısının altında ilgilendiğiniz sorunu gösteren bir temel seçin ve genişletin.

3. İlgilendiğiniz temel öğe altında, **hata ayıklamayı Başlat**' ı seçin. Bu giriş noktası, HLSL hata ayıklayıcısına karşılık gelen temel için gölgelendirici ilk çağrılma (yani, gölgelendirici tarafından işlenen ilk piksel veya köşe) için varsayılan olarak kullanılır. İlkel ile ilişkili yalnızca bir piksel vardır, ancak çizgiler ve üçgenler için birden fazla köşe gölgelendirici çağırmaları vardır.

     Belirli bir köşe için köşe gölgelendirici çağrısında hata ayıklamak için VertexShader title bağlantısını genişletin ve ilgilendiğiniz köşeyi bulun, sonra da bunun yanındaki **hata ayıklamayı Başlat** ' ı seçin.

### <a name="links-to-graphics-objects"></a>Grafik nesnelerine bağlantılar
 Piksel geçmişindeki grafik olaylarını anlamak için, olay sırasında veya olay tarafından başvurulan Direct3D nesneleri hakkında, cihaz durumu hakkında bilgilere ihtiyacınız bulunabilir. Piksel geçmişindeki her bir olay için **Grafik piksel geçmişi** , daha sonra geçerli cihaz durumuna ve ilgili nesnelere bağlantılar sağlar.

## <a name="see-also"></a>Ayrıca bkz.
- [İzlenecek yol: Cihaz Durumu Nedeniyle Eksik Nesneler](walkthrough-missing-objects-due-to-device-state.md)
- [İzlenecek yol: Gölgeleme Nedeniyle Çıkan Oluşturma Hatalarını Ayıklama](walkthrough-debugging-rendering-errors-due-to-shading.md)