---
title: Grafik Çerçeve Çözümlemesi | Microsoft Docs
ms.date: 02/09/2017
ms.topic: conceptual
f1_keywords:
- vs.graphics.frameanalysis
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 943436a64f50523905a03ed2a87e91508d1b7471
ms.sourcegitcommit: 257fc60eb01fefafa9185fca28727ded81b8bca9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72911476"
---
# <a name="graphics-frame-analysis"></a>Grafik Çerçeve Analizi
Direct3D oyununuzun veya uygulamanızın işleme performansını çözümlemek ve iyileştirmek için Visual Studio Grafik Çözümleyicisi Grafik Çerçeve Çözümlemesi kullanın.

## <a name="frame-analysis"></a>Çerçeve Analizi
 Çerçeve Analizi, tanılama amaçları doğrultusunda bir grafik günlük dosyasında yakalanan bilgilerin aynısını kullanır, ancak bunun yerine işleme performansını özetlemek için kullanır. Performans bilgileri yakalama sırasında günlüğe kaydedilmez; Bunun yerine, performans bilgileri daha sonra çerçeve analizi sırasında, zamanlama olayları ve çerçeve oynatılırken istatistikler toplanarak oluşturulur. Bu yaklaşımda, yakalama sırasında performans bilgilerinin kaydedilmesinin çeşitli avantajları vardır:

- Çerçeve Analizi, performans özetinin istatistiksel olarak ses düzeyine sahip olduğundan emin olmak için aynı karenin birden çok playmasına ait sonuçları Ortalama alabilir.

- Çerçeve Analizi, bilgilerin yakalandığı yer dışında donanım yapılandırmalarına ve cihazlara yönelik performans bilgileri oluşturabilir.

- Çerçeve Analizi, daha önce yakalanan bilgilerden yeni performans özetleri üretebilir — Örneğin, GPU sürücüleri iyileştirildiğinde veya ek hata ayıklama özellikleri ortaya çıkarır.

  Bu avantajlara ek olarak, Çerçeve Analizi, bu değişikliklerin bir uygulamanın işleme performansını nasıl etkileyebileceği hakkında bilgi sunabilmesi için çerçevenin kayıttan yürütme sırasında nasıl işlendiğine ilişkin değişiklikler de yapabilir. Bu bilgileri, tümünü uygulamak zorunda kalmadan potansiyel en iyi duruma getirme stratejilerine karar vermek ve sonra sonuçları kendiniz yakalayıp karşılaştırmak için kullanabilirsiniz.

  Çerçeve Analizi öncelikle daha hızlı işleme performansı elde etmenize yardımcı olmaya yönelik olsa da, belirli bir performans hedefi için daha iyi görsel kalite elde etmenize veya GPU güç tüketimini azaltmanıza benzer bir şekilde yardımcı olabilir.

  Uygulamanız için çerçeve analizinin neler yapabileceğini görmek için, Channel 9 ' da [Visual Studio grafik çerçeve çözümlemesi](https://channel9.msdn.com/Shows/C9-GoingNative/GoingNative-25-Offline-Analysis-Graphics-Tool) videosunu izleyebilirsiniz.

## <a name="using-frame-analysis"></a>Çerçeve analizini kullanma
 Çerçeve analizini kullanabilmeniz için, diğer grafik Çözümleyicisi araçlarından birini kullandığınızda yaptığınız gibi, uygulamanızdaki grafik bilgilerini yakalamanız gerekir. Ardından, grafik günlüğü belgesi (. vsglog) penceresinde, **Çerçeve Analizi** sekmesini seçin.

 ![Çerçeve Analizi sekmesini seçin.](media/pix_frame_analysis_select_tab.png "pix_frame_analysis_select_tab")

 Analiz tamamlandıktan sonra sonuçlar görüntülenir. Çerçeve Analizi sekmesinin en üst bölümünde zaman çizelgesi ve Özet tablosu görüntülenir. Alt bölümde Ayrıntılar tabloları görüntülenir. Kayıttan yürütme sırasında hatalar veya uyarılar oluşturulduysa, bunlar zaman çizelgesinin üstünde özetlenir; Buradan, hatalar ve uyarılar hakkında daha fazla bilgi edinmek için bağlantıları izleyebilirsiniz.

### <a name="interpreting-results"></a>Sonuçları yorumlama
 Her bir varyantın sonucunu yorumlayarak, uygulamanızın işleme performansı ve davranışı hakkında faydalı bilgiler çıkarsyükleyebilirsiniz. İşleme çeşitleri hakkında daha fazla bilgi için bu makalenin ilerleyen bölümlerindeki [çeşitler](#Variants) bölümüne bakın.

 Bazı sonuçlar, VARIANT 'ın işleme performansını nasıl etkilediğini doğrudan gösterir:

- Bilinear dokusu filtreleme varyantı performans artışı içeriyorsa, uygulamanızda Bilinear doku filtrelemesi kullanılması benzer performans kazançlarını gösterir.

- 1x1 görünüm penceresinin performans artışı gösterilmesinin ardından uygulamanızdaki işleme hedeflerinin boyutunu azaltmak, kendi işleme performansını iyileştirir.

- BC doku sıkıştırma varyantı performans artışı gösterirse, uygulamanızda BC doku sıkıştırması kullanılması benzer performans kazançlarını gösterir.

- 2xMSAA çeşidinde, 0xMSAA varyantı ile neredeyse aynı performans varsa, kuruluşunuzda, işleme kalitesini performansı olmadan geliştirmek için 2xMSAA 'yı etkinleştirebilirsiniz.

  Diğer sonuçlar, uygulamanızın performansına yönelik daha derin, daha hafif etkileri önerebilir:

- 1x1 görünüm penceresinin çok büyük performans kazancı gösteriyorsa, uygulamanız büyük olasılıkla kullanılabilir olandan daha fazla fillrate tüketiyor. Bu çeşit bir performans kazancı gösteriyorsa, uygulama çok fazla sayıda köşe işliyor.

- 16bpp Işleme hedefi biçim değişkeni önemli performans kazançlarını gösteriyorsa, uygulamanız çok fazla bellek bant genişliğine sahip olabilir.

- Yarı/çeyrek doku boyutları varyantı önemli performans kazançlarını gösteriyorsa, dokularınız muhtemelen çok fazla bellek kaplar, çok fazla bant genişliği tüketir veya doku önbelleğini kullanamaz. Bu çeşit performans değişikliğini gösteriyorsa, büyük olasılıkla performans maliyeti ödemeksizin daha büyük, daha ayrıntılı dokular kullanabilirsiniz.

  Donanım sayaçları kullanılabilir olduğunda, uygulamanızın işleme performansının neden yeterli olabileceğini öğrenmek için bunları kullanabilirsiniz. Tüm özellik düzeyi 9,2 ve üzeri cihazlar, derinlik occluson sorgularını (**piksel** özellikli sayaç) ve zaman damgalarını destekler. GPU üreticisinin donanım sayaçlarını yapıp uygulamadığına ve bu dosyaları kendi sürücüsünde kullanıma sunuldığına bağlı olarak, diğer donanım sayaçları kullanılabilir olabilir. Özet tablosunda gösterilen sonuçların kesin nedenini onaylamak için bu sayaçları kullanabilirsiniz — Örneğin, derinlik testi tarafından occlukaynaklanan piksellerin yüzdesini inceleyerek, fazla beraberlik 'nin bir faktör olup olmadığını belirleyebilirsiniz.

### <a name="timeline-and-summary-table"></a>Zaman çizelgesi ve Özet tablosu
 Varsayılan olarak, zaman çizelgesi ve Özet tablosu görüntülenir ve diğer bölümler daraltılmıştır.

#### <a name="timeline"></a>'Ndeki
 Zaman çizelgesi, birbirine göre çizilen çağrı zamanlamalarıyla ilgili genel bakışı gösterir. Daha büyük çubuklar uzun çizimli saatlere karşılık geldiğinden, çerçeveye en pahalı çizim çağrılarını hızlı bir şekilde bulmak için bunu kullanabilirsiniz. Yakalanan çerçeve çok fazla sayıda çizim çağrısı içerdiğinde, birden çok çizim çağrısı, uzunluğu bu çizim çağrılarının toplamı olan bir çubukta birleştirilir.

 ![Zaman çizelgesi, çizilen&#45;çağrı maliyetlerini gösterir.](media/pix_frame_analysis_timeline.png "pix_frame_analysis_timeline")

 Çubuğa karşılık gelen çizim çağrısı olayını görmek için işaretçiyi bir çubuğa taşıyabilirsiniz. Çubuğun seçilmesi olay listesinin bu olayla eşitlenmesine neden olur.

#### <a name="table"></a>Tablo
 Zaman çizelgesinin altındaki sayı tablosu, uygulamanızın varsayılan işleme göre her çizim çağrısının her bir işleme çeşidinin göreli performansını gösterir. Her sütunda farklı bir işleme varyantı görüntülenir ve her satır, en sol sütunda tanımlanan farklı bir çizim çağrısını temsil eder; Buradan grafik olay listesi penceresinde olay bağlantısını izleyebilirsiniz.

 ![Özet tablosunda farklı çeşitler gösterilmektedir.](media/pix_frame_analysis_summary.png "pix_frame_analysis_summary")

 Özet tablosundaki en soldaki ikinci sütun, uygulamanızın temel işleme süresini (yani, uygulamanızın varsayılan işleme için gereken süre) çizim çağrısını tamamlaması için görüntüler. Kalan sütunlar, performansın iyileştirilip geliştirilmediğini görmek daha kolay olması için her işleme çeşidinin taban çizgisi yüzdesi olarak göreli performansını gösterir. Yüzde 100 ' den büyük olan yüzdeler taban çizgisinden daha uzun sürdü — diğer bir deyişle, performans düşyordu ve yüzde 100 ' den küçük olan yüzdeleri daha az zaman aldı ve performans gerçekleşti.

 Taban çizgisinin mutlak zaman zamanlamasının ve işleme varyantlarınızın göreli zamanlaması, aslında birden çok çalıştırmanın ortalamasını alır (varsayılan olarak, 5 ' tir. Bu ortalama, zamanlama verilerinin güvenilir ve tutarlı olmasını sağlamaya yardımcı olur. Çizim araması ve işleme çeşidinin sonuçları oluşturulduğunda gözlemlendiği minimum, maksimum, ortalama ve ortanca zamanlama değerlerini incelemek için işaretçiyi tablodaki her bir hücreye taşıyabilirsiniz. Taban çizgisi zamanlaması da görüntülenir.

#### <a name="hot-draw-calls"></a>"Sık erişimli" çizim çağrıları
 Genel işleme zamanının daha büyük bir oranını kullanan veya kaçınılabilen nedenlerle alışılmadık yavaş olabilecek çizim çağrılarına dikkat çekmek için, bu "sık erişimli" çizim çağrılarını içeren satır, kendi temel zamanlaması birden fazla olduğunda kırmızıya gölgeli çerçevede bulunan tüm çizim çağrılarının ortalama temel zamanından daha uzun standart sapma.

 ![Bu DrawIndexed çağrısında sıcak ve soğuk çeşitler vardır.](media/pix_frame_analysis_hot_calls.png "pix_frame_analysis_hot_calls")

#### <a name="statistical-significance"></a>İstatistiksel anlam
 En yüksek ilgiye sahip olan çeşitlemeleri işlemeye dikkat çekmek için, Çerçeve Analizi her bir işleme çeşidinin istatistiksel önemini belirler ve önemli olanları kalın olarak görüntüler. Performansı yeşil ve kırmızı olarak azaltan olanları görüntüler. Normal tür olarak istatistiksel ölçüde önemli olmayan sonuçları görüntüler.

 ![Beraberlik çağrısı çeşidinin istatistiksel ilgisi](media/pix_frame_analysis_summary_stats.png "pix_frame_analysis_summary_stats")

 İstatistiksel uygunluğu öğrenmek için, Çerçeve Analizi [öğrencinin t-test](https://en.wikipedia.org/wiki/Student's_t-test)' i kullanır.

### <a name="details-table"></a>Ayrıntılar tablosu
 Özet tablosunun altında, varsayılan olarak daraltılan Ayrıntılar tablosu vardır. Ayrıntılar tablosunun içeriği, kayıttan yürütme makinesinin donanım platformuna bağlıdır. Desteklenen donanım platformları hakkında daha fazla bilgi için bkz. [donanım desteği](#HardwareSupport).

#### <a name="platforms-that-do-not-support-hardware-counters"></a>Donanım sayaçlarını desteklemeyen platformlar
 Çoğu platform donanım GPU sayaçlarını tam olarak desteklemez; Bunlar, şu anda Intel, AMD ve NVIDIA tarafından sunulan tüm GPU 'ları içerir. Toplanacak hiçbir donanım sayacı olmadığında, yalnızca bir ayrıntı tablosu görüntülenir ve tüm varyantlar için Ortalama mutlak zamanlamayı içerir.

 ![Ayrıntılar tablosu ve bazı kayıttan yürütme çeşitleri.](media/pix_frame_analysis_details.png "pix_frame_analysis_details")

#### <a name="platforms-that-support-hardware-counters"></a>Donanım sayaçlarını destekleyen platformlar
 Donanım GPU sayaçlarını destekleyen platformlar için — örneğin, NVIDIA T40 SOC ve tüm Qualcomm SOCs — her çeşit için bir tane olmak üzere çeşitli ayrıntılar tabloları görüntülenir. Her bir işleme değişkeni için her kullanılabilir donanım sayacı toplanır ve kendi ayrıntı tablosunda görüntülenir.

 ![Donanım sayaçları desteklenne zaman görüntülenir.](media/pix_frame.png "pix_frame")

 Donanım sayacı bilgileri, her çizim çağrısıyla ilgili belirli donanım platformu davranışının ayrıntılı bir görünümünü sağlar. Bu, performans sorunlarının nedenini tam olarak belirlemenize yardımcı olabilir.

> [!NOTE]
> Farklı donanım platformları farklı sayaçları destekler; Standart yok. Sayaçlar ve bunların gösterdiği özellikler yalnızca her bir GPU üreticisi tarafından belirlenir.

### <a name="marker-regions-and-events"></a>İşaretleyici bölgeleri ve olayları
 Çerçeve Analizi Kullanıcı tanımlı olay işaretçilerini ve olay gruplarını destekler. Özet tablosunda ve ayrıntı tablolarında görüntülenir.

 İşaretçiler ve gruplar oluşturmak için ID3DUserDefinedAnnotation API 'lerini veya eski D3DPERF_ ailesinden API 'Leri kullanabilirsiniz. D3DPERF_ API ailesini kullandığınızda, her bir işaret ve grup için, bir kare analizinin, olay işaretçisini veya olay grubu başlangıç/bitiş işaretçilerini ve bunların içeriğini içeren satırlarda renkli bir bant olarak görüntüleyeceği bir rengi atayabilirsiniz. Bu özellik önemli işleme olaylarını veya olay gruplarını hızlıca belirlemenize yardımcı olabilir.

### <a name="warnings-and-errors"></a>Uyarıları ve hatalar
 Çerçeve Analizi zaman çizelgesi üzerinde özetlenen uyarılarla veya hatalarla tamamlanır ve Çerçeve Analizi sekmesinin en altında ayrıntılı olarak açıklanmıştır.

 Genellikle, uyarılar ve hatalar yalnızca bilgilendirme amaçlıdır ve herhangi bir müdahale gerektirmez.

 Uyarılar genellikle donanım desteğinin eksik olduğunu ancak geçici olarak çalıştığını gösterir, Donanım sayaçları toplanamaz veya belirli performans verileri güvenilir olmayabilir — Örneğin, bir geçici çözüm bunu olumsuz yönde etkileiyorsa.

 Hatalar genellikle Çerçeve Analizi uygulamasında hata olduğunu, bir sürücüde hata olduğunu, donanım desteğinin eksik olduğunu ve bu dosyanın geçici olarak denenmeyeceğini ve uygulamanın kayıttan yürütme tarafından desteklenmeyen bir şeyi gerçekleştirmeye çalıştığını gösterir.

### <a name="retries"></a>Dene
 GPU, Çerçeve Analizi sırasında bir güç durumu geçişine geçtiğinde, GPU clockspeed değiştiği ve bu nedenle göreli zamanlama sonuçlarını geçersiz kıldığı için etkilenen analiz geçişinin yeniden denenmesi gerekir.

 Çerçeve Analizi, yeniden deneme sayısını 10 ' a sınırlandırır. Platformunuzun güç yönetimi veya zaman sınırlaması varsa, bu durum, yeniden deneme sınırını aştığından çerçeve analizinin başarısız olmasına ve bir hata raporlayamemesine neden olabilir. Platformun güç yönetimini sıfırlayarak ve platform bunu etkinleştirmişse daha az agresif hale getirerek bu sorunu azaltabilirsiniz.

## <a name="HardwareSupport"></a>Donanım desteği

### <a name="timestamps-and-occlusion-queries"></a>Zaman damgaları ve occlusiyon sorguları
 Zaman damgaları, çerçeve analizini destekleyen tüm platformlarda desteklenir. Desteklenen piksellerin (piksel), özellik düzeyi 9,2 veya üstünü destekleyen platformlarda desteklenmesinin derinlemesine olması için derinlik occlusiyon sorguları.

> [!NOTE]
> Çerçeve analizini destekleyen tüm platformlarda zaman damgaları desteklenmekle birlikte, zaman damgalarının doğruluğu ve tutarlılığı, platformdan platforma farklılık gösterir.

### <a name="gpu-counters"></a>GPU sayaçları
 GPU donanım sayaçları desteği donanıma bağımlıdır.

 Şu anda Intel, AMD veya NVIDIA tarafından sunulan hiçbir bilgisayar GPU 'SU GPU donanım sayaçlarını güvenilir bir şekilde desteklediğinden, Çerçeve Analizi bunlardan sayaç toplamaz. Ancak, Çerçeve Analizi aşağıdaki GPU 'dan donanım sayaçlarını toplar ve bunları güvenilir bir şekilde destekler:

- NVIDIA T40 (Tegra4)

  Çerçeve analizini destekleyen başka bir platform GPU donanım sayaçlarını toplar.

> [!NOTE]
> GPU donanım sayaçları, donanım kaynakları olduğundan, her bir işleme varyantı için tüm donanım sayaçları kümesini toplamak için birden çok geçiş gerçekleştirebilir. Sonuç olarak, GPU sayaçlarının toplandığı sıra belirtilmemiş olur.

## <a name="unsupported-scenarios"></a>Desteklenmeyen senaryolar
 Çerçeve analizini kullanmanın belirli yolları desteklenmez veya yalnızca kötü bir fikir olur.

### <a name="playback-of-high-feature-level-captures-on-down-level-devices"></a>Alt düzey cihazlarda yüksek özellik düzeyinde yakalamaları kayıttan yürütme
 Grafik Çözümleyicisi 'nde, kayıttan yürütme makinesinden daha yüksek bir özellik düzeyi kullanan bir grafik günlük dosyası oynatdığınızda, otomatik olarak ÇARPMADAN geri döner. Çerçeve analizinde, açıkça ÇARPMADAN geri dönmez ve bir hata oluşturur — WARP, Direct3D uygulamanızın doğruluğunu incelemek için yararlıdır, ancak performansını inceleme konusunda değildir.

> [!NOTE]
> Özellik düzeyi sorunları göz önünde bulundurmanız önemli olsa da, farklı donanım yapılandırmalarında ve cihazlarda grafik günlük dosyalarını yakalayabilir ve çalabilirsiniz. Günlük dosyası API 'Leri içermediği veya kayıttan yürütme makinesinde desteklenmeyen özellik düzeylerini kullandığı sürece grafik günlüğü geri çalınabilir.

### <a name="direct3d-10-and-lower"></a>Direct3D 10 ve daha düşük
 Uygulamanız Direct3D 10 API 'sini çağırırsa, Çerçeve Analizi diğer grafik Çözümleyicisi araçları tarafından tanınıp kullanılmalarına rağmen onları tanımaz veya profillendirilmez.

> [!NOTE]
> Bu yalnızca, özellik düzeylerini değil, kullanmakta olduğunuz Direct3D API çağrıları için geçerlidir.

### <a name="warp"></a>SıÇRAMA
 Çerçeve Analizi, gerçek donanımda işleme performansının profilini oluşturmak ve bu performansı geliştirmek için kullanılmak üzere tasarlanmıştır. WARP cihazlarında çerçeve analizini çalıştırmak engellenmez, ancak yüksek kaliteli bir CPU üzerinde çalışan WARP, en az özellikli modern GPU 'lara daha yavaş olduğundan ve ÇARPıTıN performansı, belirli bir CPU 'ya göre büyük ölçüde değişebildiğinden, genellikle bir adım adım değildir. üzerinde çalışıyor.

## <a name="Variants"></a>Değişken
 Çerçeve analizine ait her değişiklik, oynatma sırasında bir karenin işlenme şeklini *değişken*olarak bilinir. Çerçeve analizinin incelediği çeşitler, uygulamanızın işleme performansını veya görsel kalitesini geliştirmek için yapabileceğiniz yaygın, görece kolay değişikliklere karşılık gelir, örneğin dokuların boyutunu azaltma, doku sıkıştırması kullanma ya da etkinleştirme farklı türlerde kenar yumuşatma. Çeşitler, uygulamanızın normal işleme bağlamını ve parametrelerini geçersiz kılar. Özet:

|Varyantı|Açıklama|
|-------------|-----------------|
|**1x1 Görünüm penceresi boyutu**|Tüm işleme hedeflerindeki Görünüm penceresi boyutunu 1x1 piksele düşürür.<br /><br /> Daha fazla bilgi için bkz. [1x1 Görünüm penceresi boyut varyantı](1x1-viewport-size-variant.md)|
|**0x MSAA**|Tüm işleme hedeflerinde çok örnekli kenar yumuşatmayı (MSAA) devre dışı bırakır.<br /><br /> Daha fazla bilgi için bkz. [0x/2x/4X MSAA çeşitleri](0x-2x-4x-msaa-variants.md)|
|**2x MSAA**|Tüm işleme hedeflerinde 2x çoklu örnek kenar yumuşatma (MSAA) etkinleştirilir.<br /><br /> Daha fazla bilgi için bkz. [0x/2x/4X MSAA çeşitleri](0x-2x-4x-msaa-variants.md)|
|**4X MSAA**|Tüm işleme hedeflerinde 4X çoklu örnek kenar yumuşatma (MSAA) etkinleştirilir.<br /><br /> Daha fazla bilgi için bkz. [0x/2x/4X MSAA çeşitleri](0x-2x-4x-msaa-variants.md)|
|**Nokta dokusu filtrelemesi**|Uygun tüm doku örnekleri için filtreleme modunu `DXD11_FILTER_MIN_MAG_MIP_POINT` (işaret doku filtrelemesi) olarak ayarlar.<br /><br /> Daha fazla bilgi için bkz. [Point, Bilinear, trilinear ve Anısotropıc doku filtreleme çeşitleri](point-bilinear-trilinear-and-anisotropic-texture-filtering-variants.md).|
|**Bilinear doku filtreleme**|Uygun tüm doku örnekleri için filtreleme modunu `DXD11_FILTER_MIN_MAG_LINEAR_MIP_POINT` (Bilinear doku filtrelemesi) olarak ayarlar.<br /><br /> Daha fazla bilgi için bkz. [Point, Bilinear, trilinear ve Anısotropıc doku filtreleme çeşitleri](point-bilinear-trilinear-and-anisotropic-texture-filtering-variants.md).|
|**Trilinear doku filtrelemesi**|Uygun tüm doku örnekleri için filtreleme modunu `DXD11_FILTER_MIN_MAG_MIP_LINEAR` (trilinear doku filtrelemesi) olarak ayarlar.<br /><br /> Daha fazla bilgi için bkz. [Point, Bilinear, trilinear ve Anısotropıc doku filtreleme çeşitleri](point-bilinear-trilinear-and-anisotropic-texture-filtering-variants.md).|
|**Anısotropıc doku filtrelemesi**|Filtreleme modunu `DXD11_FILTER_ANISOTROPIC` olarak ayarlar ve uygun tüm doku örnekleri için `16` (16X anısotropıc doku filtrelemesi) `MaxAnisotropy`.<br /><br /> Daha fazla bilgi için bkz. [Point, Bilinear, trilinear ve Anısotropıc doku filtreleme çeşitleri](point-bilinear-trilinear-and-anisotropic-texture-filtering-variants.md).|
|**16bpp Işleme hedefi biçimi**|Tüm işleme hedefleri ve biriktirme arabellekleri için piksel biçimini `DXGI_FORMAT_B5G6R5_UNORM` (16bpp, 565 biçim) olarak ayarlar.<br /><br /> Daha fazla bilgi için bkz. [16bpp Işleme hedefi biçim değişkeni](16bpp-render-target-format-variant.md)|
|**MİP eşleme oluşturma**|İşleme hedefi olmayan tüm dokulerde MIP haritalarını etkinleştirebilir.<br /><br /> Daha fazla bilgi için bkz. [MİP eşleme oluşturma varyantı](mip-map-generation-variant.md).|
|**Yarım doku boyutları**|İşleme hedefi olmayan tüm dokuların doku boyutlarını her boyuttaki orijinal boyutunun yarısını azaltır. Örneğin, 256x128 dokusu 128x64 texiksel 'e indirgenir.<br /><br /> Daha fazla bilgi için bkz. [Yarı/çeyrek doku boyutları varyantı](half-quarter-texture-dimensions-variant.md).|
|**Çeyrek doku boyutları**|İşleme hedefi olmayan tüm dokuların doku boyutlarını her boyuttaki orijinal boyutunun üç ayda azaltır. Örneğin, 256x128 dokusunu 64x32 Doka 'ya düşürülemez.<br /><br /> Daha fazla bilgi için bkz. [Yarı/çeyrek doku boyutları varyantı](half-quarter-texture-dimensions-variant.md).|
|**BC doku sıkıştırması**|B8G8R8X8, B8G8R8A8 veya R8G8B8A8 piksel biçim çeşidine sahip tüm dokuların blok sıkıştırmasını izin vermez. B8G8R8X8 biçim çeşitleri BC1 kullanılarak sıkıştırılır; B8G8R8A8 ve R8G8B8A8 Format çeşitlemeleri BC3 kullanılarak sıkıştırılır.<br /><br /> Daha fazla bilgi için bkz. [BC doku sıkıştırma varyantı](bc-texture-compression-variant.md).|

 Çoğu Varyantlar için sonuç, "doku boyutunu yarıya düşürmek için yüzde 25 daha hızlıdır" veya "2x MSAA 'nın yalnızca yüzde 2 ' si daha yavaştır. Diğer çeşitler daha fazla yorum gerektirebilir — Örneğin, görünüm penceresinin boyutunu 1x1 olarak değiştiren bir değişken büyük bir performans kazancı gösteriyorsa, işlemenin düşük bir doldurmada bottlenecked olduğunu belirtebilir; Alternatif olarak, performans açısından önemli bir değişiklik yoksa, işleme köşe işleme tarafından bottlenecked olduğunu gösterebilir.