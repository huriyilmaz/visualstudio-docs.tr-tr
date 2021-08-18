---
title: Load Test Sonuçları'da Graflara Sayaç Ekleme ve Silme
description: Bir grafiye performans sayaçları eklemek için Sayaçlar panelini ve Sample Rate özelliğini kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load test results graphs, adding counters
- load test results graph
- load test, results graph
- load test results, graphs
ms.assetid: 81536233-1962-40d9-9511-0b4633814d90
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: 743dbd7c5732c674d18fcbb586dd375a47bd74bd
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122123079"
---
# <a name="how-to-add-and-delete-counters-on-graphs-in-load-test-results"></a>Nasıl yapılır: Yük Testi Sonuçlarındaki Grafiklerde Sayaç Ekleme ve Silme

Bir **grafiye performans** sayaçları eklemek için Sayaçlar panelini kullanabilirsiniz.

![Grafiye sayaç eklendi](../test/media/ltest_selectcounter.png)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

**Performans Sayacı Örnekleme Aralığı Konuları**

Yük testi çalıştırma **ayarlarında Örnek Hızı** özelliği için yük testinizin uzunluğuna göre bir değer seçin. Varsayılan beş saniyelik değer gibi daha küçük bir örnek oranı, yük testi sonuçları veritabanında daha fazla alan gerektirir. Daha uzun yük testleri için örnek oranının artırılması, toplayan veri miktarını azaltır. Daha fazla bilgi için, [bkz. How to: Specify the sample rate](../test/how-to-specify-the-sample-rate-for-a-load-test.md).

Örnek hızlar için bazı yönergeler şu şekildedir:

|Yük Testi Süresi|Önerilen Örnek Oranı|
|-|-----------------------------|
|\< 1 Saat|5 saniye|
|1 - 8 Saat|15 saniye|
|8 - 24 Saat|30 saniye|
|> 24 Saat|60 saniye|

**Yüzdebirlik Verileri Toplamak için Zamanlama Ayrıntılarını dahil etmek için dikkat edilmesi gerekenler**

içinde çalıştırma ayarlarında Timing Details Yük Testi Düzenleyicisi adlı bir **özellik Depolama.** Zamanlama **Ayrıntıları Depolama** etkinse, yük testi sırasında her bir testi, işlemi ve sayfayı yürütme süresi yük testi sonuçları deposunda depolanır. Bu, Testler, İşlemler ve Sayfalar tablolarında Yük Testi  Çözümleyicisi'ne 90. ve 95. yüzdebirlik verilerin gösterilmelerini sağlar.

**StatisticsOnly** ve **AllIndividualDetails** adlı çalıştırma ayarları özelliklerinde Timing **Details** Depolama özelliğini etkinleştirmek için iki seçenek vardır. Her iki seçenekte de tüm testler, sayfalar ve işlemler zamanlanmış ve yüzdebirlik veriler tek tek zamanlama verilerinden hesaplanır. Fark, **statisticsOnly** seçeneğiyle yüzdebirlik veriler hesaplanmaz tek tek zamanlama verileri depodan silinir. Bu, zamanlama ayrıntılarını kullanırken depoda gerekli olan alan miktarını azaltır. Öte yandan ileri düzey kullanıcılar, zamanlama ayrıntıları verilerini farklı şekillerde, farklı araçlar kullanarak SQL istiyor olabilir. Böyle bir durumda, zamanlama ayrıntısı verileri bu işleme için kullanılabilir olacak şekilde **AllIndividualDetails** seçeneği kullanılmalıdır. Buna ek olarak, **özelliğini AllIndividualDetails** olarak ayarsanız, yük testinin çalışma tamamlandıktan sonra Yük **Testi** Çözümleyicisi'nin Sanal Kullanıcı Etkinliği grafiğini kullanarak sanal kullanıcı etkinliğini analiz edersiniz.  Daha fazla bilgi için Ayrıntılar [görünümündeki Sanal kullanıcı etkinliğini analiz etme'ye bakın.](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)

Yük testi sonuçları deposunda zamanlama ayrıntıları verilerini depolamak için gereken alan miktarı, özellikle de daha uzun süre çalışan yük testleri için çok büyük olabilir. Ayrıca, yük testinin sonundaki yük testi sonuçları deposunda bu verilerin depolandığı süre daha uzun olur çünkü bu veriler yük testinin yürütülmesi tamamlanıncaya kadar yük testi aracılarında depolanır. Yük testi tamamlandığı zaman veriler depoda depolanır. Varsayılan olarak, **Timing Details Depolama** özelliği etkindir. Bu test ortamınız için bir sorunsa Zamanlama Ayrıntıları'nın Hiçbiri olarak **Depolama** **iyi olabilir.**

Daha fazla bilgi için, [bkz. How to: Specify the timing details storage property](../test/how-to-specify-the-timing-details-storage-property-for-a-load-test.md).

## <a name="to-display-a-particular-performance-counter-on-a-load-test-graph"></a>Yük testi grafı üzerinde belirli bir performans sayacını görüntülemek için

1. Yük testi tamam olduktan sonra veya bir test sonucu yükledikten sonra Yük Testi Çözümleyicisi'nin araç çubuğunda **Grafikler'i seçin.**

     **Sayaçlar** paneli Graflar görünümünde görüntülenir.

    > [!NOTE]
    > Sayaçlar **paneli görünmüyorsa,** araç çubuğunda **Sayaç panelini Göster'i** seçin.

2. Sayaçlar **panelinde,** grafik olarak görüntülenebilir görmek istediğiniz performans sayacını bulana kadar hiyerarşideki düğümleri genişletin.

     Örneğin, kullanılabilir belleği testlerin çalıştır olduğu bir bilgisayarda görüntülemek için Bilgisayarlar'ı **genişletin,** bilgisayarın düğümünü genişletin ve ardından Bellek'i **genişletin.** Kullanılabilir **MBayt sayacını** görüntülersiniz.

3. Performans sayacını görüntülemek istediğiniz grafiği seçin.

4. Sayaçlar panelinde performans sayacına sağ **tıklayın ve** 'de **Sayacı Göster'i Graph.**

    > [!TIP]
    > Performans sayacının verilerini grafikte görüntülemeyi geçici olarak durdurmak için Gösterge'de performans sayacının onay kutusunu temizleyin. Bu sayede minimum, maksimum ve ortalama istatistiklerin grafikte eğilim çizgisi görüntülemeden analiz edilir. Siz sorunları analiz ederken grafikte çakışan birkaç performans sayacı çizimi varsa bu yararlı olabilir. Daha fazla bilgi için [bkz. Yük testlerini analiz etmek için Graflar görünüm göstergesini kullanma.](../test/use-the-graphs-view-legend-to-analyze-load-tests.md)

5. Grafikten performans sayacı verilerini kaldırmak için göstergenin Sayaç sütununda performans sayacına sağ tıklayın **ve** Sil'i **seçin.**

     \- veya -

     Grafikte veri satırına sağ tıklayın ve Sil'i **seçin.**

     \- veya -

     Göstergenin Sayaç **sütunundaki performans** sayacını veya grafikte veri çizgisini seçin ve ardından Sil **tuşuna** basın.

    > [!NOTE]
    > Göstergeye Sayaç Ekle komutunu kullanarak göstergeye bir performans sayacı da koyabilirsiniz ancak **grafikte yer a seçebilirsiniz.**

## <a name="see-also"></a>Ayrıca bkz.

- [Graflar görünümünde yük testi sonuçlarını analiz etme](../test/analyze-load-test-results-in-the-graphs-view.md)
- [Nasıl gösterilir: Özel graflar oluşturma](../test/how-to-create-custom-graphs-in-load-test-results.md)
