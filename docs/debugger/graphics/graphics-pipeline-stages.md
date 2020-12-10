---
title: Grafik ardışık düzen aşamaları | Microsoft Docs
description: Direct3D grafik ardışık düzeninin her aşamasında çizim çağrısının nasıl dönüştürüleceğini görerek işleme sorunlarını giderin.
ms.custom: SEO-VS-2020
ms.date: 02/09/2017
ms.topic: conceptual
f1_keywords:
- vs.graphics.pipeline
ms.assetid: 2bf5c12e-2a00-401c-8163-4e373d08ad3f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 150c61e271e7951332848a601aaddc619a1c37e5
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2020
ms.locfileid: "96993932"
---
# <a name="graphics-pipeline-stages"></a>Grafik Ardışık Düzen Aşamaları
Grafik ardışık düzen Aşamaları penceresi, tek bir çizim çağrısının Direct3D grafik işlem hattının her aşamasına göre nasıl dönüştürüleceğini anlamanıza yardımcı olur.

 Bu işlem hattı aşamaları penceresidir:

 ![3B nesne, işlem hattı aşamaları boyunca gider.](media/gfx_diag_demo_pipeline_stages_orientation.png)

## <a name="understanding-the-graphics-pipeline-stages-window"></a>Grafik ardışık düzen aşamaları penceresini anlama
 Ardışık düzen Aşamaları penceresi, her çizim çağrısıyla ilgili olarak her bir grafik ardışık düzeninin her aşamasının sonucunu görselleştirir. Normalde, işlem hattının ortasında aşamaların sonuçları gizlidir, böylece bir işleme sorununun nerede başlatıldığını söylemeniz zordur. Her aşamayı ayrı olarak görselleştirerek, ardışık düzen Aşamaları penceresi sorunun başladığı yeri görmeyi kolaylaştırır. Örneğin, köşe gölgelendirici aşamasının beklenmedik bir şekilde bir nesnenin ekran dışına çizilmesini neden olduğunu kolayca görebilirsiniz.

 Sorunun gerçekleştiği aşamayı tanımladıktan sonra, verilerin nasıl yorumlandığını veya dönüştürüleceğini incelemek için diğer grafik Çözümleyicisi araçlarını kullanabilirsiniz. Ardışık düzen aşamalarında görüntülenen işleme sorunları genellikle hatalı köşe biçimi tanımlayıcıları, önemlidir Shader programları veya yanlış yapılandırılmış durum ile ilgilidir.

### <a name="links-to-related-graphics-objects"></a>İlgili grafik nesnelerine bağlantılar
 Bazen çizim çağrısının grafik ardışık düzenine göre belirli bir şekilde etkileşim kurduğunu tespit etmek için ek bağlam gerekir. Bu ek bağlamın daha kolay bulunmasını kolaylaştırmak için grafik ardışık düzen Aşamaları penceresi, grafik ardışık düzeninde olanlar ile ilgili ek bağlam sağlayan bir veya daha fazla nesneye bağlanır.

- Direct3D 12 ' de bu nesne genellikle bir komut listesidir.

- Direct3D 11 ' de bu nesne genellikle bir grafik cihaz bağlamıdır.

  Bu bağlantılar, grafik ardışık düzen aşamaları penceresinin sol üst köşesinde bulunan geçerli grafik olay imzasının bir parçasıdır. Nesneyle ilgili ek ayrıntıları incelemek için bu bağlantılardan herhangi birini izleyin.

### <a name="viewing-and-debugging-shader-code"></a>Gölgelendirici kodunu görüntüleme ve hata ayıklama
 Ardışık düzen aşamaları penceresinde ilgili aşamaların altındaki denetimleri kullanarak köşe, Hull, etki alanı, geometri ve Piksel gölgelendiricileri için kodu inceleyebilir ve hata ayıklayabilirsiniz.

#### <a name="to-view-a-shaders-source-code"></a>Gölgelendirici kaynak kodunu görüntülemek için

- **Grafik ardışık düzen aşamaları** penceresinde, incelemek istediğiniz gölgelendiriciye karşılık gelen gölgelendirici aşamasını bulun. Ardından, önizleme görüntüsünün altında, gölgelendirici aşaması başlık bağlantısını izleyin. Örneğin, köşe gölgelendirici kaynak kodunu görüntülemek için, bkz. bağlantı **köşe gölgelendirici obj: 30** .

    > [!TIP]
    > Nesne numarası, **obj: 30**, bu gölgelendiriciyi nesne tablosu ve piksel geçmişi penceresinde olduğu gibi grafik Çözümleyicisi arabirimi boyunca tanımlar.

#### <a name="to-debug-a-shader"></a>Gölgelendiricide hata ayıklamak için

- **Grafik ardışık düzen aşamaları** penceresinde, hata ayıklamak istediğiniz gölgelendiriciye karşılık gelen gölgelendirici aşamasını bulun. Ardından, önizleme görüntüsünün altında, **hata ayıklamayı Başlat**' ı seçin. Bu giriş noktası, HLSL hata ayıklayıcısına karşılık gelen aşama için gölgelendiriciye ait ilk çağrıya (yani, bu çizim çağrısı sırasında gölgelendirici tarafından işlenen ilk piksel, köşe veya ilkel) göre varsayılan olarak ayarlanır. Belirli bir piksel veya köşe için bu gölgelendirici çağırmaları **Grafik piksel geçmişi** aracılığıyla erişilebilir.

### <a name="the-pipeline-stages"></a>İşlem hattı aşamaları
 Ardışık düzen Aşamaları penceresi, yalnızca çizim çağrısı sırasında etkin olan işlem hattının aşamalarını görselleştirir. Grafik işlem hattının her aşaması, bir önceki aşamadaki girişi dönüştürür ve sonucu sonraki aşamaya geçirir. İlk aşamada, giriş derleyicisi, giriş olarak uygulamanızdan dizin ve köşe verileri alır; Son aşama — çıktı Merger —, ekranınızda gördüğünüz son görüntüyü oluşturmak için, yeni işlenmiş pikselleri, kendi çıktısı olarak framebuffer veya render Target ile birlikte birleştirir.

> [!NOTE]
> İşlem gölgelendiricileri **grafik ardışık düzen aşamaları** penceresinde desteklenmez.

 **Giriş assembler** Giriş derleyicisi, uygulamanız tarafından belirtilen dizin ve köşe verilerini okur ve bunu grafik donanımı için birleştirir.

 Ardışık düzen aşamaları penceresinde, giriş derleyici çıkışı bir tel çerçeve modeli olarak görselleştirilir. Sonuca daha yakından bakmak için **grafik ardışık düzen aşamaları** penceresinde **giriş assembler** ' yı seçin. böylece, Model Düzenleyicisi 'ni kullanarak tam 3B olarak birleştirilmiş köşeleri görüntüleyin.

> [!NOTE]
> Eğer `POSITION` Input assembler çıktısında anlam yoksa, **giriş assembler** aşamasında hiçbir şey görüntülenmez.

 **Köşe gölgelendiricisi** Köşe gölgelendirici aşaması, genellikle dönüşüm, kaplama ve aydınlatma gibi işlemleri gerçekleştirerek köşeleri işler. Köşe gölgelendiriciler, giriş olarak aldıkları köşeleri aynı sayıda oluşturur.

 Ardışık düzen aşamaları penceresinde, köşe gölgelendirici çıkışı bir tel çerçeve tarama görüntüsü olarak görselleştirilir. Sonuca daha yakından bakmak için **grafik ardışık düzen aşamaları** penceresinde **köşe gölgelendiricisi** ' ni seçerek görüntü düzenleyicisinde işlenen köşeleri görüntüleyin.

> [!NOTE]
> Ya da `POSITION` `SV_POSITION` semantiği köşe gölgelendirici çıktısında yoksa, **köşe gölgelendirici** aşamasında hiçbir şey görüntülenmez.

 **Kabuk gölgelendirici** (yalnızca Direct3D 11 ve Direct3D 12) kabuk gölgelendirici aşaması, çizgi, üçgen veya dörtlü gibi düşük sıralı bir yüzeyi tanımlayan denetim noktalarını işler. Çıktı olarak, sabit işlev mozaik döşeme aşamasına geçirilen daha yüksek sıralı bir geometri düzeltme eki ve düzeltme eki sabitleri üretir.

 Kabuk gölgelendirici aşaması, ardışık düzen aşamaları penceresinde görselleştirilmemiş.

 **Tessellatör aşaması** (yalnızca Direct3D 11 ve Direct3D 12) tessellatör aşaması, kabuk gölgelendiricisinin çıkışıyla temsil edilen etki alanını önceden işleyen sabit bir işlev (programlanabilir olmayan) donanım birimidir. Çıktı olarak, etki alanının bir örnekleme modelini ve bu örnekleri bağlayan daha küçük temel elemanlar (noktaları, çizgiler, üçgenler) oluşturur.

 Tessellatör aşaması, ardışık düzen aşamaları penceresinde görselleştirilmemiş.

 **Etki alanı gölgelendirici** (yalnızca Direct3D 11 ve Direct3D 12) etki alanı gölgelendirici aşaması, ıull gölgelendiriciden daha yüksek sıralı geometri düzeltme eklerini, mozaik döşeme aşamasından mozaik döşeme çarpanlarına birlikte işler. Mozaik döşeme faktörleri, tessellatör giriş faktörleri ve çıkış faktörleri dahil olabilir. Çıkış olarak, çıkış yaması üzerindeki bir noktanın köşe konumunu tessellatör faktörlerine göre hesaplar.

 Etki alanı gölgelendirici aşaması, ardışık düzen aşamaları penceresinde görselleştirilmemiş.

 **Geometri gölgelendiricisi** Geometri gölgelendirici aşaması, kenar bitişik temel elemanlar için isteğe bağlı köşe verileriyle birlikte, tüm temelleri (punto, çizgi veya üçgen) işler. Köşe gölgelendiricilerinin aksine, geometri gölgelendiriciler girdi olarak aldıkları daha fazla veya daha az temel üretebilir.

 Ardışık düzen aşamaları penceresinde, geometri gölgelendirici çıkışı bir tel çerçeve tarama görüntüsü olarak görselleştirilir. Sonuca daha yakından bakmak için **grafik ardışık düzen aşamaları** penceresinde **geometri gölgelendirici** ' ni seçerek görüntü düzenleyicisinde işlenen temelleri görüntüleyin.

 **Akış çıkış aşaması** Akış çıkış aşaması, Rasterleştirmeye ve bunları belleğe yazmaya başlamadan önce dönüştürülmüş temel elemanlara müdahale edebilir; verilerin buradan grafik işlem hattının önceki aşamalarına giriş olarak yeniden gezilecek veya CPU tarafından geri okunmuş olabilir.

 Akış çıkış aşaması, ardışık düzen aşamaları penceresinde görselleştirilmemiş.

 **Tarama aşaması** Tarayıcı aşaması, tarama satırı dönüştürmesi gerçekleştirerek vektör temel çizgilerini, noktaları, çizgileri ve üçgenler bir raster görüntüsüne dönüştüren sabit bir işlev (programlanabilir olmayan) donanım birimidir. Rasterleştirme köşeler sırasında hogenou klip-alanına dönüştürülüp kırpıldı. Çıktı olarak, Piksel gölgelendiricileri eşlenir ve köşe başına öznitelikler temel öğe genelinde enterpoladır ve piksel gölgelendiricide kullanıma sunulur.

 Tarama aşaması, ardışık düzen aşamaları penceresinde görselleştirilmemiş.

 **Piksel gölgelendiricisi** Pixel gölgelendirici aşaması, renk ve derinlik gibi piksel başına değerler oluşturmak için, enterpolasyonlu köşe verileriyle birlikte bulunan temel verileri birlikte oluşturur.

 Ardışık düzen aşamaları penceresinde, piksel gölgelendirici çıkışı tam renkli bir raster görüntüsü olarak görselleştirilir. Sonuca daha yakından bakmak için **grafik ardışık düzen aşamaları** penceresinde **piksel gölgelendiricisi** ' ni seçerek görüntü düzenleyicisinde işlenen temelleri görüntüleyin.

 **Çıktı Merger** Çıktı birleşme aşaması, yeni oluşturulan piksellerin, bu arabelleklerde yeni değerler oluşturmak için karşılık gelen arabelleklerinin (renk, derinlik ve kalıp) var olan içeriğiyle birlikte etkisini birleştirir.

 Ardışık düzen aşamaları penceresinde, çıktı birleşme çıkışı tam renkli bir raster görüntüsü olarak görselleştirilir. Sonuçlara daha yakından bakmak için **grafik ardışık düzen aşamaları** penceresinde **çıktı Merger** ' yi seçerek birleştirilmiş framebuffer 'ı görüntüleyin.

### <a name="vertex-and-geometry-shader-preview"></a>Köşe ve geometri gölgelendirici önizlemesi
 **Ardışık düzen aşamaları** penceresinde köşe veya geometri gölgelendirici aşamasını seçtiğinizde, aşağıdaki panelde yer alarak gölgelendiriciye yönelik giriş ve çıkış işlemleri görüntüleyebilirsiniz.  Burada, giriş assembler aşaması tarafından derlendikten sonra gölgelendiriciler için sağlanan köşelerin listesi hakkındaki ayrıntıları bulacaksınız.

 ![Köşe gölgelendirici aşaması giriş arabelleği Görüntüleyicisi](media/gfx_diag_vertex_shader_inbuffers.png)

 Köşe gölgelendirici aşamasının sonucunu görüntülemek için, köşe gölgelendiricisi tarafından dönüştürüldükten sonra, kafesin tam boyutlu, rasterleştirilmiş bir tel kafes değerini görüntülemek için köşe gölgelendirici aşaması küçük resmini seçin.

 ![Köşe gölgelendirici aşaması sonuç önizleme](media/gfx_diag_vertex_shader_preview.png)

## <a name="see-also"></a>Ayrıca bkz.
- [İzlenecek yol: Köşe Gölgeleme Nedeniyle Eksik Nesneler](walkthrough-missing-objects-due-to-vertex-shading.md)
- [İzlenecek yol: Gölgeleme Nedeniyle Çıkan Oluşturma Hatalarını Ayıklama](walkthrough-debugging-rendering-errors-due-to-shading.md)