---
title: Yük Testi Sonuçlarında Grafiklere Sayaç Ekleme ve Silme
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load test results graphs, adding counters
- load test results graph
- load test, results graph
- load test results, graphs
ms.assetid: 81536233-1962-40d9-9511-0b4633814d90
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: acb08edf74d3ca35a2449f588976681d679caeb4
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76115184"
---
# <a name="how-to-add-and-delete-counters-on-graphs-in-load-test-results"></a>Nasıl yapılır: Yük Testi Sonuçlarındaki Grafiklerde Sayaç Ekleme ve Silme

Bir grafiğe performans sayaçları eklemek için **Sayaçlar** panelini kullanabilirsiniz.

![Grafiğe sayaç eklendi](../test/media/ltest_selectcounter.png)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

**Performans Sayacı Örnekleme Aralığı Hususları**

Yük testinizin uzunluğuna bağlı olarak yük testi çalıştırma ayarlarında **Örnek Oran** özelliği için bir değer seçin. Beş saniyenin varsayılan değeri gibi daha küçük bir örneklem hızı, yük testi sonuçları veritabanında daha fazla alan gerektirir. Daha uzun yük testleri için, örnek lem oranını artırmak topladığınız veri miktarını azaltır. Daha fazla bilgi için [bkz: Örnek oranını belirtin.](../test/how-to-specify-the-sample-rate-for-a-load-test.md)

Örnek oranlar için bazı yönergeler aşağıda verilmiştir:

|Yük Testi Süresi|Önerilen Örnek Oran|
|-|-----------------------------|
|\<1 Saat|5 saniye|
|1 - 8 Saat arası|15 saniye|
|8 - 24 Saat|30 saniye|
|> 24 Saat|60 saniye|

**Yüzdelik Veri Toplamak için Zamanlama Ayrıntılarını Nİçldirecek Hususlar**

**Zamanlama Ayrıntıları Depolama**adlı Yük Testi Düzenleyicisi'nde çalışma ayarlarında bir özellik vardır. Zamanlama **Ayrıntıları Depolama** özelliği etkinleştirilirse, yükleme testi sırasında her bir testi, hareketi ve sayfayı yürütme süresi yük testi sonuçları deposunda depolanır. Bu, Testler, İşlemler ve Sayfalar tablolarında Yük **Testi Çözümleyicisi'nde** 90 ve 95 yüzdelik verilerin gösterilmesini sağlar.

**StatisticsOnly** ve **AllIndividualDetails**adlı çalışma ayarları özelliklerinde **Zamanlama Ayrıntıları Depolama** özelliğini etkinleştirmek için iki seçenek vardır. Her iki seçenekle de, tüm tek tek testler, sayfalar ve hareketler zamanlanır ve yüzdelik veriler tek tek zamanlama verilerinden hesaplanır. Aradaki fark, **StatisticsOnly** seçeneğiyle, yüzdelik veriler hesaplanır hesaplanmaz, tek tek zamanlama verilerinin depodan silinir. Bu, zamanlama ayrıntılarını kullandığınızda depoda gereken alan miktarını azaltır. Ancak, gelişmiş kullanıcılar zamanlama ayrıntı verilerini SQL araçlarını kullanarak başka şekillerde işlemek isteyebilir. Bu durumda, zamanlama ayrıntısı verilerinin bu işlem için kullanılabilmesi için **AllIndividualDetails** seçeneği kullanılmalıdır. Ayrıca, özelliği **AllIndividualDetails**olarak ayarlarsanız, yük testi çalışma tamamlandıktan sonra **Yük Testi Çözümleyicisi'ndeki** Sanal Kullanıcı **Etkinliği** grafiğini kullanarak sanal kullanıcı etkinliğini çözümleyebilirsiniz. Daha fazla bilgi için ayrıntılar [görünümünde sanal kullanıcı etkinliğini analiz et'](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)e bakın.

Zamanlama ayrıntıları verilerini depolamak için yük testi sonuçları deposunda gereken alan miktarı, özellikle daha uzun çalışan yük testleri için çok büyük olabilir. Ayrıca, bu verileri yük testinin sonundaki yük testi sonuçları deposunda depolama süresi daha uzundur, çünkü bu veriler yük testi yürütme tamamlanana kadar yük testi aracılarında depolanır. Yük testi bittiğinde, veriler depoya depolanır. Varsayılan olarak, **Zamanlama Ayrıntıları Depolama** özelliği etkinleştirilir. Bu, sınama ortamınız için bir sorunsa, **Zamanlama Ayrıntıları Depolamasını** **Yok**olarak ayarlamak isteyebilirsiniz.

Daha fazla bilgi için [bkz: Zamanlama ayrıntıları depolama özelliğini belirtin.](../test/how-to-specify-the-timing-details-storage-property-for-a-load-test.md)

## <a name="to-display-a-particular-performance-counter-on-a-load-test-graph"></a>Yük testi grafiğinde belirli bir performans sayacı nı görüntülemek için

1. Yük testi bittikten sonra veya bir test sonucunu yükledikten sonra, Yük Testi Çözümleyicisinin araç çubuğunda **Grafikler'i**seçin.

     **Sayaçlar** paneli Grafikler görünümünde görüntülenir.

    > [!NOTE]
    > **Sayaçlar** paneli görünmüyorsa, araç çubuğunda **Sayaçları Göster Panelini** seçin.

2. **Sayaçlar** panelinde, grafik olarak görüntülenmesini istediğiniz performans sayacını bulana kadar hiyerarşideki düğümleri genişletin.

     Örneğin, kullanılabilir belleği testlerin çalıştığı bir bilgisayarda görüntülemek için, **Bilgisayar'ı**genişletin, bilgisayar düğümlerini genişletin ve ardından **Bellek'i genişletin.** **Kullanılabilir MBytes** sayacını göreceksiniz.

3. Performans sayacını görüntülemek istediğiniz grafiği seçin.

4. **Sayaçlar** panelindeki performans sayacına sağ tıklayın ve **Grafikte Sayacı Göster'i**seçin.

    > [!TIP]
    > Performans sayacının verilerini grafikte görüntülemeyi geçici olarak durdurmak için Gösterge'deki performans sayacının onay kutusunu temizleyin. Bu, min, max ve ortalama istatistiklerin grafikteki eğilim çizgisini görüntülemeden hala analiz edilmesine olanak tanır. Bu, siz sorunları çözümlürken grafik birkaç çakışan performans sayacı çizimleri içeriyorsa yararlı olabilir. Daha fazla bilgi için bkz. [Yük testlerini analiz etmek için Grafikler görünüm göstergesini kullanın.](../test/use-the-graphs-view-legend-to-analyze-load-tests.md)

5. Performans sayacı verilerini grafikten kaldırmak için göstergenin **Sayaç** sütunundaki performans sayacına sağ tıklayın ve **Sil'i**seçin.

     \-veya -

     Grafikteki veri çizgisine sağ tıklayın ve **Sil'i**seçin.

     \-veya -

     Göstergenin **Sayaç** sütunundaki performans sayacını veya grafikteki veri satırını seçin ve sonra **Sil** tuşuna basın.

    > [!NOTE]
    > Ayrıca Gösterge'de **Sayaç Ekle** komutunu kullanarak göstergeye bir performans sayacı yerleştirmeyi de seçebilirsiniz, ancak grafiğe eklemeyi de seçebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Grafikler görünümünde yük testi sonuçlarını analiz edin](../test/analyze-load-test-results-in-the-graphs-view.md)
- [Nasıl yapılsın: Özel grafikler oluşturma](../test/how-to-create-custom-graphs-in-load-test-results.md)
