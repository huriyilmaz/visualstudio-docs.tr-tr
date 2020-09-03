---
title: Yük testlerinde eşik kuralı Ihlallerini çözümleme
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75591287"
---
# <a name="analyzing-threshold-rule-violations-in-load-tests-using-the-load-test-analyzer"></a>Yük Testi Çözümleyicisini kullanarak yük testlerinde eşik kuralı ihlallerini çözümleme

Eşik kuralları belirli performans sayaçlarıyla ilişkilendirilir ve ihlaller bir performans sayacının bir küme değerinin altında aşıldığını ya da ihlal olduğunu gösterir. Bir yük testi çalıştırdığınızda, daha önce ayarladığınız eşik kuralları için oluşan ihlalleri çözümleyebilirsiniz.

Herhangi bir ihlal oluştuysa, **Yük Testi Çözümleyicisi** durum çubuğunda bir **eşik ihlalleri** Köprüsü görüntülenir ve oluşan ihlallerin sayısını belirtir. Eşik ihlalleri tablosunu göstermek için köprüyü seçersiniz. Eşik ihlallerini **Sayaçlar** penceresinde ve grafikte da görüntüleyebilirsiniz.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="view-threshold-violations-in-the-table"></a>Tablodaki Eşik ihlallerini görüntüleme

Eşik ihlalleri tablosu ilk 1.000 ihlallerini görüntüler. Aşağıdaki tablo şu sütunları içerir:

|Sütun|Açıklama|Varsayılan olarak görünür|
|-|-|-|
|Süre|Yük testi sırasında ihlalin gerçekleştiği zaman.|Yes|
|Bilgisayar|İhlalin gerçekleştiği test altındaki bilgisayarın adı. **Note:**  Bu, yük testlerini Rig 'ler üzerinde çalıştırdığınızda önemlidir.|Yes|
|Kategori|İhlalin gerçekleştiği performans sayacının kategorisi.|Yes|
|Sayaç|İhlalin gerçekleştiği performans sayacının adı.|Yes|
|Örnek|İhlalin gerçekleştiği performans sayacı örneği.|Yes|
|İleti|Eşik ihlalini açıklayan bir ileti. Örneğin, **5 değeri 0 ' ın kritik eşik değerini aşıyor**.|Yes|

> [!NOTE]
> Sütun üstbilgilerini seçerek tabloyu sıralayabilirsiniz.

Daha fazla bilgi için bkz. [Tablolar görünümünde Yük testi sonuçlarını ve hatalarını çözümleme](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

## <a name="view-threshold-violations-in-the-counters-panel"></a>Sayaç panelinde Eşik ihlallerini görüntüleme

Eşik ihlallerini, **sayaç** panelinde, yük testiniz için performans sayaçlarını listeleyen ağaçta görüntüleyebilirsiniz. **Sayaçlar** panelindeki simgeler eşik ihlallerine iletişim kurar. Simge aşağıdakilerden biri olacaktır:

Simge aşağıdakilerden biri olacaktır:

![Eşik ihlali yok](../test/media/icon_ltest_1.gif) Eşik ihlali yok.

![Son aralıkta kritik eşik ihlali](../test/media/icon_ltest_2.gif) Son aralıkta kritik bir eşik ihlali oluştu.

![Önceki aralıkta kritik eşik ihlali](../test/media/icon_ltest_3.gif) Önceki aralıkta kritik bir eşik ihlali oluştu.

![Son aralıkta bir uyarı eşiği ihlali](../test/media/icon_ltest_4.gif) Son aralıkta bir uyarı eşiği ihlali oluştu.

![Önceki aralıkta bir uyarı eşiği ihlali](../test/media/icon_ltest_5.gif) Önceki aralıkta bir uyarı eşiği ihlali oluştu.

İsteğe bağlı olarak, eşik ihlalleri grafik üzerinde de görüntülenebilir. Eşik simgesi, eşik ihlalinin gerçekleştiği veri noktasının yanındaki grafikte görüntülenir.

Sayaç ağacında, eşik ihlali simgesi belirli sayaç düğümünden kök düğüme kadar yayılır. Bu, ağaç genişletilmediği için ağaçta görünemeyen bir sayaca karşı sizi uyarır.

## <a name="view-threshold-violations-on-the-graph"></a>Grafikteki Eşik ihlallerini görüntüleme

Eşik ihlallerini grafik üzerinde görüntüleyebilirsiniz. **Sayaçlar** paneline benzer şekilde, simgeler grafikteki Eşik ihlallerini de birbirleriyle iletişim kurar. Simgeler, eşik ihlalinin gerçekleştiği veri noktasının yanındaki grafikte görüntülenir. Grafikte görünmeyen bir sayaca bir eşik ihlali oluşursa, bu öğeyi **Sayaçlar** panelinden grafiğe sürükleyerek grafiğe ekleyebilirsiniz ().

Daha fazla bilgi için bkz. [Grafik görünümünde Yük testi sonuçlarını çözümleme](../test/analyze-load-test-results-in-the-graphs-view.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testinde bilgisayarlar için sayaç kümelerini ve eşik kurallarını belirtme](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Yük testi sonuçlarını çözümle](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Tablolar görünümünde Yük testi sonuçlarını ve hatalarını çözümleme](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)
