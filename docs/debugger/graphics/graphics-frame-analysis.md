---
title: Grafik Çerçeve Çözümlemesi | Microsoft Docs
description: Direct3D Grafik Çerçeve Çözümlemesi veya Visual Studio işleme performansını analiz etmek ve iyileştirmek için Visual Studio Graphics Analyzer'da Grafik Çerçeve Çözümlemesi'yi kullanın.
ms.custom: SEO-VS-2020
ms.date: 02/09/2017
ms.topic: conceptual
f1_keywords:
- vs.graphics.frameanalysis
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 07d6a29ea43798377dd69ae9151d11e8f390f855
ms.sourcegitcommit: fc874be3fe4637a23997b4ef2d99a2ee9a499581
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2021
ms.locfileid: "135517664"
---
# <a name="graphics-frame-analysis"></a>Grafik Çerçeve Analizi
Direct3D Grafik Çerçeve Çözümlemesi veya Visual Studio işleme performansını analiz etmek ve iyileştirmek için Visual Studio Graphics Analyzer'da Grafik Çerçeve Çözümlemesi'yi kullanın.

## <a name="frame-analysis"></a>Çerçeve analizi
 Çerçeve analizi, tanılama amacıyla grafik günlük dosyasında yakalanan bilgileri kullanır, ancak bunun yerine işleme performansını özetlemek için bu bilgileri kullanır. Performans bilgileri yakalama sırasında günlüğe kaydedlanmaz; bunun yerine performans bilgileri daha sonra, çerçeve analizi sırasında, zamanlama olayları tarafından ve çerçeve geri oynanmış olarak istatistiklerin toplanmasıyla oluşturulur. Bu yaklaşımın yakalama sırasında performans bilgilerini kaydetmeye göre çeşitli avantajları vardır:

- Performans özetinin istatistiksel olarak doğru olduğundan emin olmak için kare analizi aynı karenin birden çok kayıttan yürütme sonucunda eldeki sonuçların ortalamasını oluşturabilir.

- Çerçeve analizi, donanım yapılandırmaları ve bilgilerin yakalanır olduğu dışında cihazlar için performans bilgileri üretebilir.

- Çerçeve analizi, daha önce yakalanan bilgilerden yeni performans özetleri (örneğin, GPU sürücüleri iyileştirilmiş olduğunda veya ek hata ayıklama özelliklerini açığa çıkarırken) oluşturabiliyor.

  Bu avantajlara ek olarak, çerçeve analizi de kayıttan yürütme sırasında çerçevenin nasıl işlenecekleri konusunda değişiklik yapabilirsiniz. Böylece, bu değişikliklerin bir uygulamanın işleme performansını nasıl etkiley olabileceği hakkında bilgi sunabilirsiniz. Bu bilgileri kullanarak, hepsini uygulamak zorunda kalmadan olası iyileştirme stratejileri arasında seçim yapmak ve ardından tüm sonuçları kendiniz yakalayıp karşılaştırmak için kullanabilirsiniz.

  Çerçeve analizi öncelikli olarak daha hızlı işleme performansı elde etmeye yardımcı olmak için tasarlanmış olsa da, verilen bir performans hedefi için daha iyi görsel kalite elde etmeye veya GPU güç tüketimini azaltmanıza da yardımcı olabilir.

## <a name="using-frame-analysis"></a>Çerçeve Analizini Kullanma
 Çerçeve Analizi'yi kullanamadan önce, tıpkı diğer Grafik Çözümleyicisi araçlarından herhangi birini kullanırken olduğu gibi, çalışan uygulamanıza ait grafik bilgilerini yakalamanız gerekir. Ardından grafik günlüğü belgesi (.vsglog) penceresinde Çerçeve Analizi **sekmesini** seçin.

 ![Çerçeve Analizi sekmesini seçin.](media/pix_frame_analysis_select_tab.png "pix_frame_analysis_select_tab")

 Analiz tamamlandıktan sonra sonuçlar görüntülenir. Çerçeve analizi sekmesinin üst kısmında zaman çizelgesi ve özet tablosu görüntülenir. Alt kısım, ayrıntılar tablolarını görüntüler. Kayıttan yürütme sırasında hatalar veya uyarılar oluşturulursa bunlar zaman çizelgesinin üzerinde özetlenmiştir; Buradan, hatalar ve uyarılar hakkında daha fazla bilgi edinmek için bağlantıları takip edin.

### <a name="interpreting-results"></a>Sonuçları yorumlama
 Her varyantın sonuçlarını yorumarak, uygulamanın işleme performansı ve davranışı hakkında yararlı bilgiler çıkarabilirsiniz. Varyantları işleme hakkında daha fazla bilgi için bu [makalenin devamlarında](#Variants) yer alan Varyantlar makalesine bakın.

 Bazı sonuçlar, varyantın işleme performansını nasıl etkilediğini doğrudan belirtmektedir:

- Bilinear Doku Filtreleme varyantı performans kazancı gösteriyorsa, uygulamanızda çift doku filtrelemeyi kullanmak da benzer performans kazançları gösterir.

- 1x1 GörünümPort varyantı performans kazancı gösterdi ise, uygulamanıza işleme hedeflerinin boyutunun azaltılması, işleme performansını artırır.

- BC Doku Sıkıştırma varyantı performans kazancı gösteriyorsa, uygulamanıza BC doku sıkıştırması kullanmak da benzer performans kazançları gösterir.

- 2xMSAA varyantı 0xMSAA varyantı ile neredeyse aynı performansa sahipse, performans maliyeti olmadan işleme kalitesini geliştirmek için uygulamanıza 2xMSAA'yı etkinleştirebilirsiniz.

  Diğer sonuçlar, uygulamanın performansı üzerinde daha derin ve daha ince etkileri olabilir:

- 1x1 Görünüm Alanı varyantı çok büyük performans kazançları gösteriyorsa, uygulamanız büyük olasılıkla kullanılabilir olandan daha fazla dolgu tüketıyor olabilir. Bu değişkende performans kazancı yoksa, uygulama büyük olasılıkla çok fazla köşe işlemektedir.

- 16bpp İşleme Hedefi Biçimi varyantı önemli performans kazancı gösteriyorsa, uygulamanız büyük olasılıkla çok fazla bellek bant genişliği kullanıyordur.

- Yarı/Çeyrek Doku Boyutları varyantı önemli performans kazancı gösteriyorsa dokular büyük olasılıkla çok fazla bellek kaplar, çok fazla bant genişliği tüketir veya doku önbelleğini verimsiz bir şekilde kullanır. Bu değişken performansta değişiklik göstermezse, performans maliyeti ödemeden büyük olasılıkla daha büyük ve daha ayrıntılı dokular kullanabilirsiniz.

  Donanım sayaçları kullanılabilir olduğunda, uygulama işleme performansının neden sorun olabileceği hakkında çok ayrıntılı bilgi toplamak için bunları kullanabilirsiniz. Tüm özellik düzeyi 9.2 ve daha yüksek cihazlar, derinlik dolum sorgularını **(gizli** piksel sayacı) ve zaman damgasını destekler. GPU üreticisinin donanım sayaçları uygulayıp sürücüde ortaya çıkarıp ortaya çıkardığını bağlı olarak başka donanım sayaçları kullanılabilir. Özet tablosunda gösterilen sonuçların kesin nedenini doğrulamak için bu sayaçları kullanabilirsiniz; örneğin, derinlik testi tarafından at edilen piksellerin yüzdesini incelerken aşırıdranın bir faktör olup olmadığını tespit edersiniz.

### <a name="timeline-and-summary-table"></a>Zaman Çizelgesi ve Özet Tablosu
 Varsayılan olarak Zaman Çizelgesi ve Özet Tablosu görüntülenir ve diğer bölümler daraltılmış olur.

#### <a name="timeline"></a>Zaman çizelgesi
 Zaman çizelgesinde, çizim çağrısı zamanlamalarının bir diğerini gösteren genel bakış yer almaktadır. Daha büyük çubuklar daha uzun çizim sürelerini karşılık gelen, çerçevede en pahalı çizim çağrılarını hızla bulmak için kullanabilirsiniz. Yakalanan kare çok fazla sayıda çizim çağrısı içerdiğinde, uzunluğu bu çekme çağrılarının toplamı olan birden çok çizim çağrısı bir çubukta bir araya toplanır.

 ![Zaman çizelgesi, çekme&#45;gösterir.](media/pix_frame_analysis_timeline.png "pix_frame_analysis_timeline")

 Çubuğun karşılık gelen draw-call olaylarını görmek için işaretçiyi bir çubuğun üzerine layabilirsiniz. Çubuğun seçerek olay listesinin bu olayla eşitlenmesine neden olur.

#### <a name="table"></a>Tablo
 Zaman çizelgesinin altındaki sayı tablosu, her çizim çağrısı için her işleme varyantının göreli performansını, uygulamanın varsayılan işlemesi ile gösterir. Her sütun farklı bir işleme varyantı görüntüler ve her satır en sol sütunda tanımlanan farklı bir çizim çağrısını temsil eder; Buradan Grafik Olay Listesi penceresinde olayın bağlantısını takip edin.

 ![Özet tablosu farklı varyantları gösterir.](media/pix_frame_analysis_summary.png "pix_frame_analysis_summary")

 Özet Tablosu'nun en sol ikinci sütunu, uygulamanın temel işleme süresini (yani, çizim çağrısını tamamlamak için uygulamanın varsayılan işleme süresinin uzunluğu) görüntüler. Kalan sütunlarda her işleme çeşidinin göreli performansı, performansın geliştirip geliştiril olmadığını daha kolay görmek için Temel'in yüzdesi olarak gösterir. Yüzde 100'den büyük yüzdeler Temel'den daha uzun sürer; diğer bir ifadeyle performans düşüktür ve yüzde 100'den küçük yüzdeler daha kısa sürede performans artmış olur.

 Temel'in mutlak zamanlaması ve işleme varyantlarının göreli zamanlaması değerleri aslında birden çok çalıştırmanın ortalama ortalamalarıdır (varsayılan olarak 5). Bu ortalama, zamanlama verilerini güvenilir ve tutarlı bir şekilde sağlamaya yardımcı olur. Bu çizim çağrısı ve işleme varyantı için sonuçlar oluşturulurken gözlemlenen minimum, maksimum, ortalama ve ortadaki zamanlama değerlerini incelemek için işaretçiyi tablodaki her bir hücreye geri koyabilirsiniz. Temel zamanlama da görüntülenir.

#### <a name="hot-draw-calls"></a>"Hot" draw çağrıları
 Genel işleme süresinden daha büyük bir oran tüketen veya kaçınılması mümkün olan nedenlerle olağan dışı yavaş olan çağrılara dikkat çekmek için, kendi Temel zamanlaması çerçevede tüm çizim çağrılarının ortalama Temel zamanlamasına göre birden fazla standart sapmadan daha uzun olduğunda bu "sık" çekme çağrılarını içeren satır kırmızı renkle gölgeli olur.

 ![Bu DrawIndexed çağrısının sıcak ve soğuk varyantları vardır.](media/pix_frame_analysis_hot_calls.png "pix_frame_analysis_hot_calls")

#### <a name="statistical-significance"></a>İstatistiksel önem
 Kare Analizi, en yüksek ilgi düzeyine sahip olan işleme varyasyonlarını işlemeye dikkat çekmek için her işleme varyantının istatistiksel önemini belirler ve önemli olanları kalın yazı tipi olarak görüntüler. Performansı geliştirenleri yeşil, performansı düşürenleri kırmızı olarak görüntüler. Normal tür kadar istatistiksel olarak önemli olan sonuçları görüntüler.

 ![Çizim çağrısı varyantının istatistiksel ilgi düzeyi](media/pix_frame_analysis_summary_stats.png "pix_frame_analysis_summary_stats")

 Çerçeve Analizi, istatistiksel ilgi düzeyini belirlemek için [Öğrencinin t testini kullanır.](https://en.wikipedia.org/wiki/Student's_t-test)

### <a name="details-table"></a>Ayrıntılar tablosu
 Özet tablosu altında, varsayılan olarak daraltılmış Details tablosu yer alır. Details tablosu içeriği, kayıttan yürütme makinesinin donanım platformuna bağlıdır. Desteklenen donanım platformları hakkında bilgi için bkz. [Donanım desteği.](#HardwareSupport)

#### <a name="platforms-that-do-not-support-hardware-counters"></a>Donanım sayaçlarını desteklemeen platformlar
 Çoğu platform donanım GPU sayaçlarını tam olarak desteklemez; bunlar şu anda Intel, AMD ve nVidia tarafından sunulan tüm GPU'ları içerir. Toplayan donanım sayaçları yoktur, yalnızca bir Details tablosu görüntülenir ve tüm çeşitlemelerin ortalama mutlak zamanlamasını içerir.

 ![Ayrıntılar tablosu ve bazı kayıttan yürütme çeşitlemeleri.](media/pix_frame_analysis_details.png "pix_frame_analysis_details")

#### <a name="platforms-that-support-hardware-counters"></a>Donanım sayaçlarını destekleyen platformlar
 Donanım GPU sayaçlarını destekleyen platformlar için (örneğin, nVidia T40 SOC ve tüm Qualcomm SOC'ler) her çeşit için bir tane olacak şekilde birkaç Details tablosu görüntülenir. Kullanılabilir her donanım sayacı, her işleme çeşidi için toplanır ve kendi Details tablosunda görüntülenir.

 ![Donanım sayaçları desteklendiğinde görüntülenir.](media/pix_frame.png "pix_frame")

 Donanım sayacı bilgileri, her bir çekme çağrısı için belirli donanım platformu davranışlarının çok ayrıntılı bir görünümünü sağlar ve bu da performans sorunlarının nedenini tam olarak tanımlamanıza yardımcı olabilir.

> [!NOTE]
> Farklı donanım platformları farklı sayaçları destekler; standart yoktur. Sayaçlar ve temsil edilenler yalnızca her GPU üreticisi tarafından belirlenir.

### <a name="marker-regions-and-events"></a>İşaretçi bölgeleri ve olayları
 Çerçeve Analizi, kullanıcı tanımlı olay işaretçilerini ve olay gruplarını destekler. Bunlar Özet tablosunda ve Ayrıntı tablolarında görüntülenir.

 İşaretçiler ve gruplar oluşturmak için ID3DUserDefinedAnnotation API'lerini veya eski D3DPERF_ API ailesini kullanabilirsiniz. D3DPERF_ API ailesini kullanarak her bir işaretçiyi atayabilirsiniz ve Kare Analizi'nin olay işaretçisini veya olay grubu başlangıç/bitiş işaretlerini ve içeriklerini içeren satırlarda renkli bir bant olarak görüntüleye bir renk gruplayabilirsiniz. Bu özellik, önemli işleme olaylarını veya olay gruplarını hızlıca tanımlamanıza yardımcı olabilir.

### <a name="warnings-and-errors"></a>Uyarıları ve hatalar
 Çerçeve Analizi zaman zaman Zaman Çizelgesinin üzerinde özetlenen ve Çerçeve Analizi sekmesinin en altında ayrıntılı olarak belirtilen uyarı veya hatalarla tamamlanır.

 Uyarılar ve hatalar genellikle bilgilendirme amaçlıdır ve müdahale gerektirmez.

 Uyarılar genellikle donanım desteğinin eksik olduğunu ama geçici olarak çalışılagelebilir, donanım sayaçlarının tolere olmadığını veya belirli performans verileri güvenilir olmadığını (örneğin, bir geçici çözümün onu olumsuz etkilediği durumlarda) olduğunu gösteriyor.

 Hatalar genellikle çerçeve analizi uygulamasında hatalar olduğunu, bir sürücünün hatalara sahip olduğunu, donanım desteğinin eksik olduğunu ve çalışılamaysa da uygulamanın kayıttan yürütme tarafından desteklenmiyor bir şeyi denemesini gösterir.

### <a name="retries"></a>Yeniden deneme sayısı
 GPU, çerçeve analizi sırasında güç durumu geçiş sürecinden geçerse GPU saatler değiştirildi ve göreli zamanlama sonuçları geçersiz kılınarak etkilenen analiz geçişinin yeniden denenmiş olması gerekir.

 Çerçeve Analizi, yeniden deneme sayısını 10 ile sınırlar. Platformda agresif güç yönetimi veya saat gating varsa, Çerçeve Analizi'nin başarısız olması ve yeniden deneme sınırını aşmış olması nedeniyle bir hata bildirmesi olabilir. Platformumuz bunu sağlarsa platformunun güç yönetimi ve saat hızı azaltması daha az agresif olacak şekilde sıfırlayarak bu sorunu hafifletabilirsiniz.

## <a name="hardware-support"></a><a name="HardwareSupport"></a> Donanım desteği

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
 Çerçeve Analizi, gerçek donanımda işleme performansının profilini oluşturmak ve bu performansı geliştirmek için kullanılmak üzere tasarlanmıştır. WARP cihazlarında çerçeve analizini çalıştırmak engellenmez, ancak yüksek kaliteli bir CPU üzerinde çalışan WARP, en az özellikli modern GPU 'lara eşit olduğundan ve bu genellikle bir adım adım daha yavaş olduğundan, bu genellikle bir adım daha düşüktür.

## <a name="variants"></a><a name="Variants"></a> Değişken
 Çerçeve analizine ait her değişiklik, oynatma sırasında bir karenin işlenme şeklini *değişken* olarak bilinir. Çerçeve analizinin incelediği çeşitler, uygulamanızın işleme performansını veya görsel kalitesini geliştirmek için yapabileceğiniz yaygın, oldukça kolay değişikliklere karşılık gelir. Örneğin, dokuların boyutunu azaltarak, doku sıkıştırmayı kullanarak veya farklı türlerde kenar yumuşatma sağlayabilirsiniz. Çeşitler, uygulamanızın normal işleme bağlamını ve parametrelerini geçersiz kılar. Özet:

|Değişken|Description|
|-------------|-----------------|
|**1x1 Görünüm penceresi boyutu**|Tüm işleme hedeflerindeki Görünüm penceresi boyutunu 1x1 piksele düşürür.<br /><br /> Daha fazla bilgi için bkz. [1x1 Görünüm penceresi boyut varyantı](1x1-viewport-size-variant.md)|
|**0x MSAA**|Tüm işleme hedeflerinde çok örnekli kenar yumuşatmayı (MSAA) devre dışı bırakır.<br /><br /> Daha fazla bilgi için bkz. [0x/2x/4X MSAA çeşitleri](0x-2x-4x-msaa-variants.md)|
|**2x MSAA**|Tüm işleme hedeflerinde 2x çoklu örnek kenar yumuşatma (MSAA) etkinleştirilir.<br /><br /> Daha fazla bilgi için bkz. [0x/2x/4X MSAA çeşitleri](0x-2x-4x-msaa-variants.md)|
|**4X MSAA**|Tüm işleme hedeflerinde 4X çoklu örnek kenar yumuşatma (MSAA) etkinleştirilir.<br /><br /> Daha fazla bilgi için bkz. [0x/2x/4X MSAA çeşitleri](0x-2x-4x-msaa-variants.md)|
|**Nokta dokusu filtrelemesi**|`DXD11_FILTER_MIN_MAG_MIP_POINT`Uygun tüm doku örnekleri için filtreleme modunu (işaret dokusu filtrelemesi) olarak ayarlar.<br /><br /> Daha fazla bilgi için bkz. [Point, Bilinear, trilinear ve Anısotropıc doku filtreleme çeşitleri](point-bilinear-trilinear-and-anisotropic-texture-filtering-variants.md).|
|**Bilinear doku filtreleme**|`DXD11_FILTER_MIN_MAG_LINEAR_MIP_POINT`Uygun tüm doku örnekleri için filtreleme modunu (Bilinear doku filtrelemesi) olarak ayarlar.<br /><br /> Daha fazla bilgi için bkz. [Point, Bilinear, trilinear ve Anısotropıc doku filtreleme çeşitleri](point-bilinear-trilinear-and-anisotropic-texture-filtering-variants.md).|
|**Trilinear doku filtrelemesi**|`DXD11_FILTER_MIN_MAG_MIP_LINEAR`Uygun tüm doku örnekleri için filtreleme modunu (trınear doku filtrelemesi) olarak ayarlar.<br /><br /> Daha fazla bilgi için bkz. [Point, Bilinear, trilinear ve Anısotropıc doku filtreleme çeşitleri](point-bilinear-trilinear-and-anisotropic-texture-filtering-variants.md).|
|**Anısotropıc doku filtrelemesi**|`DXD11_FILTER_ANISOTROPIC` `MaxAnisotropy` `16` Uygun tüm doku örnekleri için filtreleme modunu ve (16X anısotropıc doku filtrelemesi) olarak ayarlar.<br /><br /> Daha fazla bilgi için bkz. [Point, Bilinear, trilinear ve Anısotropıc doku filtreleme çeşitleri](point-bilinear-trilinear-and-anisotropic-texture-filtering-variants.md).|
|**16bpp Işleme hedefi biçimi**|`DXGI_FORMAT_B5G6R5_UNORM`Tüm işleme hedefleri ve biriktirme arabellekleri için piksel biçimini (16bpp, 565 biçim) olarak ayarlar.<br /><br /> Daha fazla bilgi için bkz. [16bpp Işleme hedefi biçim değişkeni](16bpp-render-target-format-variant.md)|
|**MİP eşleme oluşturma**|İşleme hedefi olmayan tüm dokulerde MIP haritalarını etkinleştirebilir.<br /><br /> Daha fazla bilgi için bkz. [MİP eşleme oluşturma varyantı](mip-map-generation-variant.md).|
|**Yarım doku boyutları**|İşleme hedefi olmayan tüm dokuların doku boyutlarını her boyuttaki orijinal boyutunun yarısını azaltır. Örneğin, 256x128 dokusu 128x64 texiksel 'e indirgenir.<br /><br /> Daha fazla bilgi için bkz. [Yarı/çeyrek doku boyutları varyantı](half-quarter-texture-dimensions-variant.md).|
|**Çeyrek doku boyutları**|İşleme hedefi olmayan tüm dokuların doku boyutlarını her boyuttaki orijinal boyutunun üç ayda azaltır. Örneğin, 256x128 dokusunu 64x32 Doka 'ya düşürülemez.<br /><br /> Daha fazla bilgi için bkz. [Yarı/çeyrek doku boyutları varyantı](half-quarter-texture-dimensions-variant.md).|
|**BC doku sıkıştırması**|B8G8R8X8, B8G8R8A8 veya R8G8B8A8 piksel biçim çeşidine sahip tüm dokuların blok sıkıştırmasını izin vermez. B8G8R8X8 biçim çeşitleri BC1 kullanılarak sıkıştırılır; B8G8R8A8 ve R8G8B8A8 Format çeşitlemeleri BC3 kullanılarak sıkıştırılır.<br /><br /> Daha fazla bilgi için bkz. [BC doku sıkıştırma varyantı](bc-texture-compression-variant.md).|

 Çoğu Varyantlar için sonuç, "doku boyutunu yarıya düşürmek için yüzde 25 daha hızlıdır" veya "2x MSAA 'nın yalnızca yüzde 2 ' si daha yavaştır. Diğer çeşitler daha fazla yorum gerektirebilir — Örneğin, görünüm penceresinin boyutunu 1x1 olarak değiştiren bir değişken büyük bir performans kazancı gösteriyorsa, işlemenin düşük bir doldurmada bottlenecked olduğunu belirtebilir; Alternatif olarak, performans açısından önemli bir değişiklik yoksa, işleme köşe işleme tarafından bottlenecked olduğunu gösterebilir.