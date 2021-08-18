---
title: Grafik İşlem Hattı | Microsoft Docs
description: Direct3D grafik işlem hattının her aşamasında çizim çağrısının nasıl dönüştürülmesiyle ilgili sorunları giderin.
ms.custom: SEO-VS-2020
ms.date: 02/09/2017
ms.topic: conceptual
f1_keywords:
- vs.graphics.pipeline
ms.assetid: 2bf5c12e-2a00-401c-8163-4e373d08ad3f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: d7a86d93e49f92734bcccd9eefab6ed498734479
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122058559"
---
# <a name="graphics-pipeline-stages"></a>Grafik Ardışık Düzen Aşamaları
Grafik İşlem Hattı Aşamaları penceresi, direct3D grafik işlem hattının her aşaması tarafından tek bir çizim çağrısının nasıl dönüştürüleceklerini anlamanıza yardımcı olur.

 Bu, İşlem Hattı Aşamaları penceresidir:

 ![3D nesnesi işlem hattı aşamalarından geçmektedir.](media/gfx_diag_demo_pipeline_stages_orientation.png)

## <a name="understanding-the-graphics-pipeline-stages-window"></a>Grafik İşlem Hattı Aşamalarını Anlama penceresi
 İşlem Hattı Aşamaları penceresi, her çizim çağrısı için grafik işlem hattının her aşamasının sonucu ayrı olarak görselleştirilir. Normalde, işlem hattının ortasındaki aşamaların sonuçları gizlenir ve bu da işleme sorununun nereden başlat gittiğinin zor olmasıdır. İşlem Hattı Aşamaları penceresi, her aşamayı ayrı ayrı görselleştirerek sorunun nereden başladığına kolayca bakabilirsiniz. Örneğin köşe gölgelendiricisi aşamasının beklenmedik bir şekilde bir nesnenin ekrandan çekilse neden olduğunu kolayca görebilirsiniz.

 Sorunun oluştuğu aşamayı belirledikten sonra diğer Grafik Çözümleyicisi araçlarını kullanarak verilerin nasıl yorumlanması veya dönüştürülmesiyle ilgili incelemeler yapabilirsiniz. İşlem hattı aşamalarında görünen işleme sorunları genellikle yanlış köşe biçim tanımlayıcıları, buggy gölgelendirici programları veya yanlış yapılandırılmış durumla ilgilidir.

### <a name="links-to-related-graphics-objects"></a>İlgili grafik nesnelerine bağlantılar
 Bazen çizim çağrısının grafik işlem hattıyla belirli bir şekilde etkileşim kurmasını belirlemek için ek bağlam gerekir. Bu ek bağlamı daha kolay bulmak için Grafik İşlem Hattı Aşamaları penceresi, grafik işlem hattında olanlarla ilgili ek bağlam sağlayan bir veya daha fazla nesneyle bağlantı oluşturur.

- Direct3D 12'de bu nesne genellikle bir komut listesidir.

- Direct3D 11'de bu nesne genellikle bir grafik cihaz bağlamıdır.

  Bu bağlantılar, Grafik İşlem Hattı Aşamaları penceresinin sol üst köşesinde bulunan geçerli grafik olay imzasının bir parçasıdır. Nesneyle ilgili ek ayrıntıları incelemek için bu bağlantılardan herhangi birini izleyin.

### <a name="viewing-and-debugging-shader-code"></a>Gölgelendirici kodunu görüntüleme ve hata ayıklama
 İşlem Hattı Aşamaları penceresinde ilgili aşamaların altındaki denetimleri kullanarak köşe, köşe, etki alanı, geometri ve piksel gölgelendiricileri için kodu inceler ve hata ayıklarsınız.

#### <a name="to-view-a-shaders-source-code"></a>Gölgelendiricinin kaynak kodunu görüntülemek için

- Grafik **İşlem Hattı Aşamaları** penceresinde, incelemek istediğiniz gölgelendiriciye karşılık gelen gölgelendirici aşamasını bulun. Ardından önizleme görüntüsünün altında gölgelendirici aşaması başlık bağlantısını izleyin; örneğin Köşe **Gölgelendiricisi obj:30** bağlantısını takip edin ve köşe gölgelendiricisi kaynak kodunu görüntüleyebilirsiniz.

    > [!TIP]
    > **obj:30** nesne numarası, nesne tablosu ve piksel geçmişi penceresi gibi Grafik Çözümleyicisi arabiriminde bu gölgelendiriciyi tanımlar.

#### <a name="to-debug-a-shader"></a>Gölgelendiricide hata ayıklamak için

- Grafik **İşlem Hattı Aşamaları** penceresinde, hata ayıklamak istediğiniz gölgelendiriciye karşılık gelen gölgelendirici aşamasını bulun. Ardından önizleme görüntüsünün altında Hata Ayıklamayı **Başlat'ı seçin.** HLSL hata ayıklayıcısına bu giriş noktası varsayılan olarak karşılık gelen aşama için gölgelendiricinin ilk çağrısını (bu çizim çağrısı sırasında gölgelendirici tarafından işlenen ilk piksel, köşe veya temel öğe) olarak ayarlar. Belirli bir piksel veya köşe için bu gölgelendiricinin çağrılarına Grafik Piksel **Geçmişi üzerinden erişilebilir.**

### <a name="the-pipeline-stages"></a>İşlem hattı aşamaları
 İşlem Hattı Aşamaları penceresi yalnızca çizim çağrısı sırasında etkin olan işlem hattının aşamalarını görselleştirmektedir. Grafik işlem hattının her aşaması, önceki aşamadaki girişi dönüştürer ve sonucu bir sonraki aşamaya iletir. İlk aşama olan Input Assembler, giriş olarak uygulamanıza yönelik dizin ve köşe verilerini alır; en son aşama olan Output Merger, yeni işlenen pikselleri framebuffer'ın geçerli içeriğiyle birleştirir veya ekranda gördüğünüz son görüntüyü üretmek için hedefi çıkışı olarak işler.

> [!NOTE]
> grafik işlem hattı aşamaları penceresinde işlem **gölgelendiricileri** desteklenmiyor.

 **Giriş Assembler** Input Assembler, uygulamanız tarafından belirtilen dizin ve köşe verilerini okur ve grafik donanımı için bir araya okur.

 İşlem Hattı Aşamaları penceresinde, Giriş Assembler çıkışı bir tel çerçeve modeli olarak görselleştirilmiştir. Sonucu daha yakından görmek için  Grafik İşlem Hattı  Aşamaları penceresinde Giriş Birleyicisi'ni seçerek Model Düzenleyicisi'ni kullanarak derlene köşeleri tam 3D olarak görüntüebilirsiniz.

> [!NOTE]
> `POSITION`Semantik giriş assembler çıkışında yoksa, Giriş Assembler aşamasında **hiçbir şey görüntülenmez.**

 **Köşe Gölgelendiricisi** Köşe gölgelendiricisi aşaması köşeleri işler ve genellikle dönüşüm, görünüm ve aydınlatma gibi işlemler gerçekleştirerek. Köşe gölgelendiricileri, giriş olarak aynı sayıda köşe üretir.

 İşlem Hattı Aşamaları penceresinde Köşe Gölgelendiricisi çıkışı bir tel çerçeve raster görüntüsü olarak görselleştirilmiştir. Sonucu daha yakından görmek için Grafik İşlem Hattı  Aşamaları pencerelerinde Köşe Gölgelendiricisi'ni seçerek işlenen köşeleri Görüntü Düzenleyicisi'nde görüntüebilirsiniz. 

> [!NOTE]
> köşe `POSITION` `SV_POSITION` gölgelendiricisi çıkışında veya semantiği yoksa, Köşe Gölgelendiricisi aşamasında **hiçbir şey görüntülenmez.**

 **Shader** (yalnızca Direct3D 11 ve Direct3D 12) Gölge gölgelendiricisi aşaması, çizgi, üçgen veya dörtlü gibi düşük sıralı bir yüzey tanımlayan denetim noktalarını işler. Çıkış olarak sabit işlevli çoğaltma aşamasına geçirilen daha yüksek sıra geometri yaması ve düzeltme eki sabitleri üretir.

 Gölgelendirici aşaması İşlem Hattı Aşamaları penceresinde görselleştirlanmaz.

 **Llaellator Stage** (yalnızca Direct3D 11 ve Direct3D 12) Theellator stage is a fixed function (non-programmable) hardware unit that preprocesses the domain that preprocesses the output of the shader. Çıktı olarak, etki alanının bir örnekleme desenini ve bu örnekleri birbirine bağlamak için daha küçük temel öğeler (noktalar, çizgiler, üçgenler) kümesi oluşturur.

 Bu aşama İşlem Hattı Aşamaları penceresinde görselleştirilmmektedir.

 **Etki Alanı Gölgelendiricisi** (yalnızca Direct3D 11 ve Direct3D 12) Etki alanı gölgelendiricisi aşaması, Gölge gölgelendiricisi gölgelendiricisi'nde daha yüksek siparişli geometri düzeltme eklerini, gölgelendirici aşamasından gelen özel satış faktörlerini birlikte işler. Taraklama faktörleri, çıktı faktörlerinin yanı sıra bazı giriş faktörleri de içerebilir. Çıkış olarak, bir noktanın çıkış yaması üzerinde köşe konumunu,ellator faktörlerine göre hesaplar.

 Etki alanı gölgelendiricisi aşaması İşlem Hattı Aşamaları penceresinde görselleştirlanmaz.

 **Geometri Gölgelendiricisi** Geometri gölgelendiricisi aşaması, uç bitişik temel öğeler için isteğe bağlı köşe verileriyle birlikte tüm temelleri (noktalar, çizgiler veya üçgenler) işler. Köşe gölgelendiricilerinin aksine, geometri gölgelendiricileri giriş olarak alandan daha fazla veya daha az temel öğe üretebilir.

 İşlem Hattı Aşamaları penceresinde geometri gölgelendiricisi çıkışı, tel çerçeve tarama görüntüsü olarak görselleştirilmiştir. Sonucu daha yakından görmek için Grafik İşlem Hattı  Aşamaları penceresinde **Geometri Gölgelendiricisi'ni** seçerek Görüntü Düzenleyicisi'nde işlenen temelleri görüntüleniyor.

 **Akış Çıkış Aşaması** Akış çıkış aşaması, taramadan önce dönüştürülmüş ilkelleri kesiyor ve belleğe yazabilir; Buradan veriler, grafik işlem hattının önceki aşamalarına giriş olarak geri okunabilir veya CPU tarafından geri okunabilir.

 Akış çıkış aşaması İşlem Hattı Aşamaları penceresinde görselleştirlanmaz.

 **Rasterizer Aşaması** Rasterizer aşaması, vektör temellerini (noktalar, çizgiler, üçgenler) tarama çizgisi dönüştürmesi gerçekleştirerek bir tarama görüntüsüne dönüştüren sabit bir işlev (programlanabilir olmayan) donanım birimidir. Tarama sırasında köşeler homojen klibin boşluğuna dönüştürülür ve kırpılır. Çıkış olarak piksel gölgelendiricileri eşlenmiş ve köşe başına öznitelikler temel öğe arasında irdelenmiş ve piksel gölgelendiricisi için hazır hale gelir.

 Rasterizer aşaması İşlem Hattı Aşamaları penceresinde görselleştirlanmaz.

 **Piksel Gölgelendiricisi** Piksel gölgelendiricisi aşaması, renk ve derinlik gibi piksel başına değerler oluşturmak için köşe verileriyle birlikte rasterleştirilmiş temelleri işlemeye devam eder.

 İşlem Hattı Aşamaları penceresinde piksel gölgelendiricisi çıkışı tam renkli bir tarama görüntüsü olarak görselleştirildi. Sonucu daha yakından görmek için Grafik İşlem Hattı  Aşamaları penceresinde Piksel Gölgelendiricisi'ni seçerek Görüntü Düzenleyicisi'nde işlenen temelleri görüntüleniyor. 

 **Output Merger** Çıkış birleştirme aşaması, bu arabelleklerde yeni değerler üretmek için yeni işlenen piksellerin etkisini karşılık gelen arabelleklerin mevcut içeriğiyle (renk, derinlik ve kalıp) birleştirir.

 İşlem Hattı Aşamaları penceresinde çıkış birleştirme çıkışı, tam renkli bir tarama görüntüsü olarak görselleştirilmiştir. Sonuçlara daha yakından bakmak için Grafik İşlem  **Hattı** Aşamaları penceresinde Çıkış Birleştirme'yi seçerek birleştirilen çerçeveyi açın.

### <a name="vertex-and-geometry-shader-preview"></a>Köşe ve Geometri gölgelendiricisi önizlemesi
 İşlem Hattı Aşamaları penceresinde köşe veya geometri  gölgelendiricisi aşamasını seçerek aşağıdaki panelde gölgelendiriciden gelen girişleri ve çıkışları görüntüleyebilirsiniz.  Burada, giriş assembler aşaması tarafından birleştirildikten sonra gölgelendiricilere sağlanan köşelerin listesiyle ilgili ayrıntıları bulabilirsiniz.

 ![Köşe gölgelendiricisi aşama giriş arabellek görüntüleyicisi](media/gfx_diag_vertex_shader_inbuffers.png)

 Köşe gölgelendiricisi aşamasının sonucu görüntülemek için Köşe Gölgelendiricisi aşaması küçük resmini seçerek köşe gölgelendiricisi tarafından dönüştürülen meshin tam boyutlu, taramalı tel çerçevesini görüntüleyebilirsiniz.

 ![Köşe gölgelendiricisi aşaması sonuç önizlemesi](media/gfx_diag_vertex_shader_preview.png)

## <a name="see-also"></a>Ayrıca bkz.
- [İzlenecek yol: Köşe Gölgeleme Nedeniyle Eksik Nesneler](walkthrough-missing-objects-due-to-vertex-shading.md)
- [İzlenecek yol: Gölgeleme Nedeniyle Çıkan Oluşturma Hatalarını Ayıklama](walkthrough-debugging-rendering-errors-due-to-shading.md)