---
title: Yük Testi Çözümleyicisinin Grafikler görünümünde yük testi sonuçlarını analiz edin
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
manager: jillfra
ms.openlocfilehash: dac639b8513e8ef675c6246476791b9351241130
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591274"
---
# <a name="analyze-load-test-results-in-the-graphs-view-of-the-load-test-analyzer"></a>Yük Testi Çözümleyicisinin Grafikler görünümünde yük testi sonuçlarını analiz edin

Bir yük testinin sonuçları birkaç farklı bölmede veri olarak görüntülenir.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Test sonuçlarını grafik olarak görüntülemek **için, yük testi** araç çubuğundaki **Grafikler'i** seçin. Her grafik, açılan listede üstte grafik adı bulunan bir panelde görüntülenir. Panelde farklı bir grafik görüntülemek için listeden farklı bir grafik adı seçin.

Aynı anda en fazla dört grafik paneli görüntülenebilir. **Panel düzeni** araç çubuğu düğmesini kullanarak farklı panel düzenleri arasında geçiş yapabilirsiniz.

Birkaç yerleşik grafik sağlanır. Yerleşik grafikleri olduğu gibi kullanabilir veya özelleştirebilirsiniz. Ayrıca, kendi grafiklerinizi oluşturabilirsiniz. Daha fazla bilgi için [bkz: Grafiklere sayaç ekleme ve silme](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md) ve nasıl [sildiği: Özel grafikler oluşturun.](../test/how-to-create-custom-graphs-in-load-test-results.md)

## <a name="built-in-graphs"></a>Yerleşik grafikler

Aşağıdaki tablo, yük testi sonuçlarını çözümlemek için kullanılabilen yerleşik grafikleri listeler.

|Grafik Adı|Açıklama|
|-|-|
|Temel Göstergeler|Kullanıcı yükü, iş bölümü ve yanıt süresi gibi test performansının temel yönlerini açıklayan sayaçlar.|
|Test Yanıt Süresi|Testlerin çalışması için gereken süreye ilişkin veriler.|
|Sayfa Yanıt Süresi|Yükleme testi sırasında erişilen web sayfaları için ortalama yanıt süresi.|
|Test Altında Sistem|Uygulamanın çalıştığı bilgisayarlar hakkında bilgi. Bu bellek kullanımı, işlemci, fiziksel disk, işlemler hakkında veri içerir.<br /><br /> Varsayılan olarak, yalnızca Kullanılabilir Mbyte'ler ve İşlemci Zaman sayaçları toplanır.|
|Denetleyici ve Aracılar|Yük testlerinin çalıştırıldığı bilgisayarlar hakkında bilgi. Bu bellek kullanımı, işlemci, fiziksel disk, işlemler hakkında veri içerir.<br /><br /> Varsayılan olarak yalnızca Kullanılabilir Mbyte'ler ve İşlemci Zaman sayaçları toplanır.|
|İşlem Yanıt Süresi|Yük testi sırasında gerçekleşen hareketler için ortalama yanıt süresi.|

Grafikte hem çalışma zamanında hem de test çalıştırıladıktan sonra farklı sayaçlar görüntüleyebilirsiniz.

> [!NOTE]
> Otomatik olarak oluşturulan yanıt zaman grafiğine yalnızca yanıt süresi performans sayaçları eklenebilir.

Sayaç bilgileri hem grafikte hem de grafiklerin altındaki göstergede görüntülenir. Grafiğin bir bölümünü de yakınlaştırabilirsiniz. Daha fazla bilgi için [bkz: Grafiğin bir bölgesini yakınlaştırın.](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md)

## <a name="counters-displayed-in-graphs"></a>Grafiklerde görüntülenen sayaçlar

Grafikler *sayaçları*görüntüler. Sayaçlar, saniye başına testler veya ortalama test süresi gibi bir yük testi sırasında toplanan verilere başvurur. Sayaçlar hakkında daha fazla bilgi için [bkz.](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)

Grafiklerde görüntülenen sayaçlar için gösterge, yük testi çalışması yla ilgili birkaç yararlı veri sütunu gösterir. Grafikteki herhangi bir verinin ekranını kapatmak için göstergedeki satırdaki onay kutusunu temizleyin.

Gösterge aşağıdaki sütunları içerir:

|Sayaç|Sayacın adı|
|-|-|
|Örnek|Karşı örneğin adı.|
|Kategori|Sayaç kategorisinin adı.|
|Bilgisayar|Sayacın toplandığı bilgisayarın adı.|
|Renk|Grafikteki çizginin rengi.|
|Aralık|O sayaç için grafikte 100 ile temsil edilen sayıyı gösterir. Örneğin, üst değeri 10.000 olan bir aralık için, grafiğin üst kısmındaki 100 etiket 10.000'i temsil eder.|
|Min|Sayacın minimum değerini milisaniye cinsinden gösterir.|
|Maks|Sayacın maksimum değerini milisaniye cinsinden gösterir.|
|Ort.|Sayacın ortalama değerini milisaniye cinsinden gösterir.|
|Son|En son örnekleme aralığındaki sayacın değerini milisaniye cinsinden gösterir.|

## <a name="tasks"></a>Görevler

|Görevler|İlişkili konular|
|-|-|
|**Göstergeyi kullanarak grafikleri özelleştirin:** Grafikler görünümü gösterge grafiği ile ilişkili her performans sayacı için bilgileri görüntüler. Göstergeyi performans sayaçlarını kaldırmak, grafikteki performans sayaçlarını vurgulamak ve çizim seçeneklerini özelleştirmek için kullanabilirsiniz.|-   [Yük testlerini analiz etmek için Grafikler görünümü göstergesini kullanma](../test/use-the-graphs-view-legend-to-analyze-load-tests.md)|
|**Grafiklerde sayaçları görüntüleyin:** Grafiğe sayaçlar yerleştirerek yük testi sonuçları grafiğine farklı türde veriler ekleyebilirsiniz.|-   [Nasıl yapılır: Grafiklerdeki sayaçları ekleme ve silme](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md)|
|**Grafikleri yakınlaştırın:** Yükleme testi tamamlandıktan sonra, yakınlaştırma ve grafiğin bir bölgesine kaydırmak için yakınlaştırma çubuklarını kullanabilirsiniz. Yakınlaştırarak, bir yük testi sırasında oluşturulan verileri daha ince ayrıntılarla inceleyebilirsiniz.|-   [Nasıl yapilir: Grafiğin bir bölgesini yakınlaştırın](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md)|
|**Döşeme grafikleri:** Yükleme testi sonuçları grafiklerini herhangi bir desenin içinde düzenleyebilirsiniz. En fazla dört grafiği ayarlayabilirsiniz.||
|**Özel grafikler oluşturun:** Yük testi sonuçları hakkında belirli bilgileri görüntüleyen grafikler tasarlayabilirsiniz. Grafiğin göstereceği yük testi sayaçlarını belirterek özel bir grafik tasarlarsınız.|-   [Nasıl yapılsın: Özel grafikler oluşturma](../test/how-to-create-custom-graphs-in-load-test-results.md)|
|**Grafikteki performans sayaçları verilerini dışa aktarma:** **Grafik** görünümündeyken **Yük Testi Çözümleyiciaraç** çubuğundaki **Excel'e Dışa Aktar Grafik Verilerini** kullanarak grafik verilerini Microsoft Excel'e dışa aktarabilirsiniz.||

## <a name="related-tasks"></a>İlişkili görevler

[Tablo görünümündeki yük testi sonuçlarını ve hatalarını analiz etme](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)

[Nasıl yapılı: Analiz için yük testi sonuçlarına erişin](../test/how-to-access-load-test-results-for-analysis.md)

[Yük testi sonuçlarını analiz edin](../test/analyze-load-test-results-using-the-load-test-analyzer.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Grafiklerdeki sayaçları ekleme ve silme](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md)
- [Nasıl yapılsın: Özel grafikler oluşturma](../test/how-to-create-custom-graphs-in-load-test-results.md)
- [Nasıl yapilir: Grafiğin bir bölgesini yakınlaştırın](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md)
