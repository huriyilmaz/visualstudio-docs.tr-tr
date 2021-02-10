---
title: Yük testi sonuçlarını analiz etme-Grafikler görünümü (Yük Testi Çözümleyicisi)
description: Test sonuçlarını grafik olarak görüntülemeyi öğrenin. Her bir grafik, açılan listede grafik adına sahip bir panelde görüntülenir.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.monitor.graph.view
helpviewer_keywords:
- graphs, analyzing load tests
- load tests, graphs in Load Test Viewer
- Load Test Viewer, graphs
- load tests, results graphs
- load tests, using graphs
- load test results, graphs
ms.assetid: 4a919cd8-541c-40ee-be3b-352fabc56140
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: cbd15d57090f2248cdd97eba1898e363cc2d21b3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948081"
---
# <a name="analyze-load-test-results-in-the-graphs-view-of-the-load-test-analyzer"></a>Yük Testi Çözümleyicisinin grafik görünümünde Yük testi sonuçlarını çözümleme

Bir yük testinin sonuçları, farklı bölmelerde veri olarak görüntülenir.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Test sonuçlarını grafik olarak göstermek için, **Yük testi** araç çubuğunda **grafikler** ' i seçin. Her bir grafik, açılan listede en üstte görünen grafik adı ile bir panelde görüntülenir. Panelde farklı bir grafiği göstermek için listeden farklı bir grafik adı seçin.

Tek seferde dört adede kadar grafik paneli görüntülenebilir. **Panel düzeni** araç çubuğu düğmesini kullanarak farklı panel düzenleri arasında geçiş yapabilirsiniz.

Birkaç yerleşik grafik sağlanır. Yerleşik grafikleri olduğu gibi kullanabilir veya özelleştirebilirsiniz. Ayrıca, kendi grafiklerinizi de oluşturabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: grafiklerde sayaç ekleme ve silme](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md) ve [nasıl yapılır: özel grafik oluşturma](../test/how-to-create-custom-graphs-in-load-test-results.md).

## <a name="built-in-graphs"></a>Yerleşik grafikler

Aşağıdaki tabloda, yük testi sonuçlarını çözümlemek için kullanılabilen yerleşik grafikler listelenmektedir.

|Grafik adı|Description|
|-|-|
|Anahtar göstergeleri|Kullanıcı yükü, aktarım hızı ve yanıt süresi gibi test performansının temel yönlerini tanımlayan sayaçlar.|
|Sınama yanıt süresi|Testlerin çalıştırılması için gereken süre hakkındaki veriler.|
|Sayfa yanıt süresi|Yük testi sırasında erişilen Web sayfaları için Ortalama yanıt süresi.|
|Test altındaki sistem|Sınanan uygulamanın çalıştırıldığı bilgisayarlar hakkında bilgiler. Bu, bellek kullanımı, işlemci, fiziksel disk, süreçler hakkındaki verileri içerir.<br /><br /> Varsayılan olarak, yalnızca kullanılabilir MBayt ve Işlemci zamanı sayaçları toplanır.|
|Denetleyici ve aracılar|Yük testlerinin çalıştığı bilgisayarlar hakkında bilgiler. Bu, bellek kullanımı, işlemci, fiziksel disk, süreçler hakkındaki verileri içerir.<br /><br /> Varsayılan olarak yalnızca kullanılabilir MBayt ve Işlemci zamanı sayaçları toplanır.|
|İşlem Yanıt Süresi|Yük testi sırasında oluşan işlemler için Ortalama yanıt süresi.|

Hem çalışma zamanında hem de bir test çalıştırıldıktan sonra grafikte farklı sayaçlar görüntüleyebilirsiniz.

> [!NOTE]
> Otomatik olarak oluşturulan yanıt süresi grafiğine yalnızca yanıt süresi performans sayaçları eklenebilir.

Sayaç bilgileri hem grafikte hem de grafiklerin altındaki göstergede görüntülenir. Ayrıca, grafiğin bir bölümünü de yakınlaştırabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: grafiğin bir bölgesini yakınlaştırma](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md).

## <a name="counters-displayed-in-graphs"></a>Grafiklerde görünen sayaçlar

Grafik görüntüleme *sayaçları*. Sayaçlar, saniye başına testler veya ortalama test süresi gibi yük testi sırasında toplanan verilere başvurur. Sayaçlar hakkında daha fazla bilgi için bkz. [bir yük testinde bilgisayarlar için sayaç kümelerini ve eşik kurallarını belirtme](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md).

Grafiklerde görüntülenen sayaçlara ilişkin gösterge, yük testi çalıştırması hakkında birçok yararlı veri sütununu gösterir. Grafikteki tüm verilerin görüntülenmesini devre dışı bırakmak için, göstergedeki satırdaki onay kutusunun işaretini kaldırın.

Gösterge şu sütunları içerir:

|Sayaç|Sayacın adı|
|-|-|
|Örnek|Sayaç örneğinin adı.|
|Kategori|Sayaç kategorisinin adı.|
|Bilgisayar|Sayacın toplandığı bilgisayarın adı.|
|Renk|Grafikteki çizginin rengi.|
|Aralık|Bu sayacın grafiğinde 100 ile temsil edilen sayıyı gösterir. Örneğin, üst değeri 10.000 olan bir Aralık için, grafiğin en üstündeki 100 etiketi 10.000 ' ı temsil eder.|
|Min|Sayaç için en küçük değeri milisaniye cinsinden gösterir.|
|En yüksek değer|Sayaç için milisaniye olarak en büyük değeri gösterir.|
|Ort|Sayacın ortalama değerini milisaniye cinsinden gösterir.|
|Son|En son örnekleme aralığı sırasında sayacın değerini milisaniye cinsinden gösterir.|

## <a name="tasks"></a>Görevler

|Görevler|İlişkili konular|
|-|-|
|**Göstergeyi kullanarak grafikleri özelleştirin:** Grafikler görünümü göstergesi, bir grafikle ilişkili her performans sayacı için bilgileri görüntüler. Göstergeyi, performans sayaçlarını kaldırmak, grafikteki performans sayaçlarını vurgulamak ve çizim seçeneklerini özelleştirmek için kullanabilirsiniz.|-   [Yük testlerini çözümlemek için grafik görünümü göstergesini kullanma](../test/use-the-graphs-view-legend-to-analyze-load-tests.md)|
|**Grafiklerde sayaçları görüntüle:** Grafiğe sayaç yerleştirerek, yük testi sonuçları grafiğine farklı türlerde veriler ekleyebilirsiniz.|-   [Nasıl yapılır: grafiklerde sayaç ekleme ve silme](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md)|
|**Grafikleri Yakınlaştır:** Bir yük testi tamamlandıktan sonra yakınlaştırma çubuklarını kullanarak grafiğin bir bölgesine yakınlaştırıp kaydırma yapabilirsiniz. ' İ yakınlaştırarak, yük testi sırasında oluşturulan verileri daha ayrıntılı bir şekilde inceleyebilirsiniz.|-   [Nasıl yapılır: grafiğin bir bölgesine yakınlaştırma](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md)|
|**Kutucuk grafikleri:** Yük testi sonuçları grafiklerini birkaç desenden herhangi birinde düzenleyebilirsiniz. Dört adede kadar grafik döşemesini sağlayabilirsiniz.||
|**Özel grafikler oluşturma:** Yük testi sonuçlarıyla ilgili belirli bilgileri görüntüleyen grafikler tasarlayabilirsiniz. Grafiğin görüntüleyeceği yük testi sayaçlarını belirterek özel bir grafik tasarlayacaksınız.|-   [Nasıl yapılır: özel grafikler oluşturma](../test/how-to-create-custom-graphs-in-load-test-results.md)|
|**Grafikteki performans sayaçları verilerini dışarı aktarın:** **Grafik görünümdeyken** , **Yük Testi Çözümleyicisi** araç çubuğunda grafik **verilerini Excel 'e ver** düğmesini kullanarak Microsoft Excel 'e aktarabilirsiniz.||

## <a name="related-tasks"></a>İlişkili görevler

[Tablolar görünümünde Yük testi sonuçlarını ve hatalarını çözümleme](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)

[Nasıl yapılır: analiz için yük testi sonuçlarına erişme](../test/how-to-access-load-test-results-for-analysis.md)

[Yük testi sonuçlarını çözümle](../test/analyze-load-test-results-using-the-load-test-analyzer.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: grafiklerde sayaç ekleme ve silme](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md)
- [Nasıl yapılır: özel grafikler oluşturma](../test/how-to-create-custom-graphs-in-load-test-results.md)
- [Nasıl yapılır: grafiğin bir bölgesine yakınlaştırma](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md)
