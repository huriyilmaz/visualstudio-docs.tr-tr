---
title: 'adım adım kılavuz: Gölgelendirme Hataları Nedeniyle Hata Ayıklama | Microsoft Docs'
description: Gölgelendirici hatası bulan bir araştırmayı izleyin. Grafik Piksel Geçmişi ve HLSL Visual Studio Grafik Tanılama dahil olmak üzere uygulamanın kullanımını gösterir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 01875b05-cc7b-4add-afba-f2b776f86974
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 6f359715bebdab4323bba21637f8a3f4be0f98f1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122133919"
---
# <a name="walkthrough-debugging-rendering-errors-due-to-shading"></a>İzlenecek yol: Gölgeleme Nedeniyle Çıkan Oluşturma Hatalarını Ayıklama
Bu kılavuzda gölgelendirici hatası Grafik Tanılama yanlış renklendirilmiş bir nesneyi araştırmak için [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Grafik Tanılama'nin nasıl kullanıldığı açıklandı.

 Bu izlenecek yol şunların nasıl olduğunu gösteriyor:

- Sorunu gösterecek pikselleri belirlemek için grafik günlüğü belgesini inceleme.

- Piksel durumunu **daha yakından incelemek** için Grafik Piksel Geçmişi penceresini kullanın.

- Piksel ve **köşe gölgelendiricilerini incelemek için HLSL** Hata Ayıklayıcısını kullanın.

## <a name="scenario"></a>Senaryo
 Bir köşe gölgelendiricisi piksel gölgelendiricisi yanlış veya tamamlanmamış bilgileri geçtiğinde, nesnelerde yanlış renklendirme yaygın olarak oluşur.

 Bu senaryoda, yakın zamanda uygulamanıza bir nesnesi eklediniz. Ayrıca nesneyi dönüştürmek ve benzersiz bir görünüm vermek için yeni bir köşe ve piksel gölgelendiricileri ekledik. Bir test sırasında uygulamayı çalıştırsanız, nesne düz siyah olarak işlenir. Bu Grafik Tanılama kullanarak, uygulamanın hata ayıklaması için sorunu bir grafik günlüğüne yakalarsanız. Sorun uygulamada şu görüntüye benzer:

 ![Nesnesi yanlış renklerle işlenir.](media/gfx_diag_demo_render_error_shader_problem.png "gfx_diag_demo_render_error_shader_problem")

## <a name="investigation"></a>Araştırma
 Test Grafik Tanılama kullanarak, test sırasında yakalanan kareleri incelemek için grafik günlüğü belgesini yükleyebilirsiniz.

#### <a name="to-examine-a-frame-in-a-graphics-log"></a>Grafik günlüğünde bir çerçeveyi incelemek için

1. içinde, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] eksik modeli gösteren bir çerçeveye sahip bir grafik günlüğü yükleme. içinde yeni bir grafik günlüğü belge penceresi [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] görüntülenir. Bu pencerenin üst kısmında, seçilen çerçevenin işleme hedefi çıkışı yer atır. Alt kısım, yakalanan her **kareyi küçük** resim görüntüsü olarak görüntüleyen Çerçeve Listesi'dir.

2. Çerçeve **Listesi'nin** içinde nesnenin doğru görünüme sahip olmadığını bir çerçeve seçin. İşleme hedefi, seçilen çerçeveyi yansıtacak şekilde güncelleştirilir. Bu senaryoda grafik günlüğü belge penceresi şu görüntüye benzer:

    ![Grafik günlüğü belgesi Visual Studio.](media/gfx_diag_demo_render_error_shader_step_1.png "gfx_diag_demo_render_error_shader_step_1")

   Sorunu gösteren bir çerçeveyi seçdikten sonra, tanılamak için **Grafik Piksel Geçmişi** penceresini kullanabilirsiniz. Grafik **Piksel Geçmişi penceresi** belirli bir pikseli, gölgelendiricilerini ve işleme hedefi üzerindeki etkilerini kronolojik olarak etkilemiş olan temelleri gösterir.

#### <a name="to-examine-a-pixel"></a>Pikseli incelemek için

1. Grafik Piksel **Geçmişi penceresini** açın. Yeni araç **Grafik Tanılama** Piksel **Geçmişi'ne tıklayın.**

2. İncelenecek pikseli seçin. Grafik günlüğü belge penceresinde, nesnesinde yanlış renklendirilmiş piksellerden birini seçin:

    ![Piksel seçiminde geçmişiyle ilgili bilgiler görüntülenir.](media/gfx_diag_demo_render_error_shader_step_2.png "gfx_diag_demo_render_error_shader_step_2")

    Grafik **Piksel Geçmişi penceresi,** seçilen pikseli yansıtacak şekilde güncelleştirilir. Bu senaryoda Grafik Piksel **Geçmişi penceresi** şu şekilde görünür:

    ![Piksel geçmişinde bir DrawIndexed olayı görünür.](media/gfx_diag_demo_render_error_shader_step_3.png "gfx_diag_demo_render_error_shader_step_3")

    Piksel gölgelendiricinin sonucu tamamen siyah (0, 0, 0, 0, 1) opak ve **Output Merger'ın** bu piksel gölgelendiriciyi  Pikselin Önceki rengiyle birleştirmiş olduğunu ve Sonuç'un tamamen opak siyah olduğunu fark eder. 

   Yanlış renklendirilmiş bir pikseli inceledikten ve piksel gölgelendiricisi çıktısını beklenen renk olmadığını fark ettikten sonra, piksel gölgelendiriciyi incelemek ve nesnenin rengine ne olduğunu bulmak için HLSL Hata Ayıklayıcı'sını kullanabilirsiniz. Yürütme sırasında HLSL değişkenlerinin durumunu incelemek, HLSL kodunda adım adım incelemek ve sorunu tanılamanıza yardımcı olacak kesme noktaları ayarlamak için HLSL Hata Ayıklayıcı'sını kullanabilirsiniz.

#### <a name="to-examine-the-pixel-shader"></a>Piksel gölgelendiriciyi incelemek için

1. Piksel gölgelendiricisinde hata ayıklamaya başlama. Grafik Piksel **Geçmişi penceresinde,** nesnenin temel öğenin altında, **Piksel Gölgelendiricisi'nin yanındaki** Hata **Ayıklamayı Başlat düğmesini** seçin.

2. Bu senaryoda, piksel gölgelendiricisi yalnızca köşe gölgelendiricisi üzerinden rengi geçtiğinden, piksel gölgelendiricinin sorunun kaynağı olmadığını gözlemlemek kolaydır.

3. İşaretçiyi üzerinde geri `input.color` kalanı. Değerinin tamamen opak siyah (0, 0, 0, 1) olduğunu farkedin.

    !["input" girişinin "color" üyesi siyahtır.](media/gfx_diag_demo_render_error_shader_step_5.png "gfx_diag_demo_render_error_shader_step_5")

    Bu senaryoda inceleme, yanlış rengin büyük olasılıkla piksel gölgelendiricisi üzerinde çalışacak doğru renk bilgilerini sağlamadan köşe gölgelendiricisi sonucu olduğunu ortaya koyacaktır.

   Köşe gölgelendiricisi büyük olasılıkla piksel gölgelendiricisi için doğru bilgileri sağlamadı belirledikten sonra, sonraki adım köşe gölgelendiriciyi incelemektir.

#### <a name="to-examine-the-vertex-shader"></a>Köşe gölgelendiriciyi incelemek için

1. Köşe gölgelendiricisinde hata ayıklamaya başlama. Grafik Piksel **Geçmişi penceresinde,** nesnenin temel öğenin altında, Köşe Gölgelendiricisi'nin yanındaki Hata  **Ayıklamayı Başlat düğmesini** seçin.

2. Köşe gölgelendiricinin çıkış yapısını bulun; bu piksel gölgelendiricisi girişidir. Bu senaryoda bu yapının adı `output` olur. Köşe gölgelendiricisi kodunu inceler ve yapı üyesinin açıkça tamamen opak siyah olarak ayarlanmış olduğunu farkedin( belki de birinin hata ayıklama `color` `output` çalışmaları sonucunda).

3. Renk üyesinin giriş yapısından hiçbir zaman kopyalanmaz. değeri yapı döndürülmeden hemen önce tamamen opak siyah olarak ayarlansa da değerinin önceki satırda doğru şekilde başlatılmamış olduğundan emin olmak iyi bir `output.color` `output` `output` fikirdir. değerini izlerken siyah olarak ayar alan satıra ulaşana kadar köşe `output.color` gölgelendiricisi kodunda adım adım `output.color` inin. değerinin siyah `output.color` olarak ayarlanıncaya kadar başlatılmamış olduğunu fark etmek. Bu, siyah olarak ayarlayan kod satırı `output.color` silinmek yerine değiştirilmeleri gerektiğini onaylar.

    !["output.color" değeri siyahtır.](media/gfx_diag_demo_render_error_shader_step_7.png "gfx_diag_demo_render_error_shader_step_7")

   İşleme sorununun nedeninin köşe gölgelendiricisi piksel gölgelendiricisi için doğru renk değerini sağlamama olduğunu belirleydikten sonra, sorunu çözmek için bu bilgileri kullanabilirsiniz. Bu senaryoda, köşe gölgelendiricisinde aşağıdaki kodu değiştirerek bunu düzeltebilirsiniz

```hlsl
output.color = float3(0.0f, 0.0f, 0.0f);
```

 kullanıcısı

```hlsl
output.color = input.color;
```

 Bu kod, köşe rengini nesnenin değiştirilmeden köşelerinden geçer; daha karmaşık köşe gölgelendiricileri, geçirmeden önce rengi değiştirebilir. Düzeltilmiş köşe gölgelendiricisi kodu şu şekildedir:

 ![Düzeltilmiş köşe gölgelendiricisi kodu.](media/gfx_diag_demo_render_error_shader_step_8.png "gfx_diag_demo_render_error_shader_step_8")

 Kodu düzeltdikten sonra yeniden yapılandırarak uygulamayı yeniden çalıştırarak işleme sorununun çözüldüğünü keşfedin.

 ![Nesnesi doğru renklerle işlenir.](media/gfx_diag_demo_render_error_shader_resolution.png "gfx_diag_demo_render_error_shader_resolution")
