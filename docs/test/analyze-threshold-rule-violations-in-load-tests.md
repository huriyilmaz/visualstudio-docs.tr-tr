---
title: Yük Testlerinde Eşik Kural İhlallerinin Analizi
ms.date: 10/19/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.monitor.threshholdresult
helpviewer_keywords:
- load tests, thresholds
- threshold violations
- threshold counts
- load tests, threshold violations
- load test results, analyzing threshold violations
- thresholds in load tests
ms.assetid: 969ed346-cf2e-4d48-82b3-edb3e075e1c0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0a20c5e3f30a6d006175e78fc70dab79d0b9bf8a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591287"
---
# <a name="analyzing-threshold-rule-violations-in-load-tests-using-the-load-test-analyzer"></a>Yük Testi Çözümleyicisini Kullanarak Yük testlerinde eşik kuralı ihlallerini analiz etme

Eşik kuralları belirli performans sayaçlarıyla ilişkilidir ve ihlaller bir performans sayacının belirlenen değerin aşıldığı veya altına düştüğünü gösterir. Bir yük testi çalıştırdığınızda, daha önce ayarladığınız eşik kuralları için oluşan ihlalleri çözümleyebilirsiniz.

Herhangi bir ihlal oluştuysa, **Yük Testi Çözümleyicisi** durum çubuğunda bir **eşik ihlalleri** köprü görünür ve oluşan ihlallerin sayısını belirtir. Eşik ihlalleri tablosunu görüntülemek için köprüseçin. Eşik ihlallerini **Sayaçlar** penceresinde ve grafikte de görüntüleyebilirsiniz.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="view-threshold-violations-in-the-table"></a>Tabloda eşik ihlallerini görüntüleme

Eşik ihlalleri tablosu ilk 1.000 ihlali görüntüler. Aşağıdaki tablo şu sütunları içerir:

|Sütun|Açıklama|Varsayılan olarak görünür|
|-|-|-|
|Zaman|İhlalinin gerçekleştiği yük testi sırasındaki süre.|Evet|
|Bilgisayar|İhlalin gerçekleştiği test altındaki bilgisayarın adı. **Not:**  Bu, platformlarda yük testleri çalıştırdığınızda önemlidir.|Evet|
|Kategori|İhlalinin gerçekleştiği performans sayacının kategorisi.|Evet|
|Sayaç|İhlalinin gerçekleştiği performans sayacının adı.|Evet|
|Örnek|İhlalin gerçekleştiği performans karşı örneği.|Evet|
|İleti|Eşik ihlalini açıklayan bir ileti. Örneğin, **değer 5 0 kritik eşik değerini aşıyor.**|Evet|

> [!NOTE]
> Sütun üstbilgisini seçerek tabloyu sıralayabilirsiniz.

Daha fazla bilgi için bkz: [Tablolar görünümünde yük testi sonuçlarını ve hatalarını analiz](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)et.

## <a name="view-threshold-violations-in-the-counters-panel"></a>Sayaçlar panelinde eşik ihlallerini görüntüleme

Eşik ihlallerini **Sayaçlar** panelinde, yük testinizin performans sayaçlarını listeleyen ağaçta görüntüleyebilirsiniz. **Sayaçlar** panelindeki simgeler eşik ihlallerini bildirir. Simge aşağıdakilerden biri olacaktır:

Simge aşağıdakilerden biri olacaktır:

![Eşik ihlali yok](../test/media/icon_ltest_1.gif) Eşik ihlali yok.

![Son aralıkta kritik bir eşik ihlali](../test/media/icon_ltest_2.gif) Kritik bir eşik ihlali son aralıkta oluştu.

![Önceki aralıkta kritik bir eşik ihlali](../test/media/icon_ltest_3.gif) Kritik bir eşik ihlali önceki bir aralıkta oluştu.

![Son aralıkta bir uyarı eşik ihlali](../test/media/icon_ltest_4.gif) Son aralıkta bir uyarı eşiği ihlali oluştu.

![Önceki aralıkta bir uyarı eşik ihlali](../test/media/icon_ltest_5.gif) Önceki bir aralıkta bir uyarı eşiği ihlali oluştu.

İsteğe bağlı olarak, eşik ihlalleri grafikte de gösterilebilir. Eşik simgesi, eşik ihlalinin oluştuğu veri noktasının yanındaki grafikte görünür.

Karşı ağaçta, bir eşik ihlali simgesi, kök düğümüne kadar belirli sayaç düğümünden yayılır. Bu, ağaç genişletilmediği için ağaçta görünmeyebilecek bir sayaç ihlaline karşı sizi uyarır.

## <a name="view-threshold-violations-on-the-graph"></a>Grafikte eşik ihlallerini görüntüleme

Grafikte eşik ihlallerini görüntüleyebilirsiniz. **Sayaçlar** paneline benzer şekilde, simgeler grafikte eşik ihlallerini bildirir. Simgeler, eşik ihlalinin oluştuğu veri noktasının yanındaki grafikte görünür. Grafikte görünmeyen bir sayaçta bir eşik ihlali oluşursa, **sayaçlar** panelinden grafiğe sürükleyerek bunu grafiğe ekleyebilirsiniz.

Daha fazla bilgi için bkz: [Grafikler görünümünde yük testi sonuçlarını analiz](../test/analyze-load-test-results-in-the-graphs-view.md)et.

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testindeki bilgisayarlar için sayaç kümelerini ve eşik kurallarını belirtme](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Yük testi sonuçlarını analiz edin](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Tablolar görünümünde yük testi sonuçlarını ve hatalarını analiz etme](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)
