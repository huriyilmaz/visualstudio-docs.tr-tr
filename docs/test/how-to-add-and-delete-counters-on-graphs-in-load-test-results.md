---
title: Load Test Sonuçları grafiklerde sayaç ekleme ve silme
description: Bir grafiğe performans sayaçlarını eklemek ve örnek hızı özelliği hakkında bilgi edinmek için sayaçlar panelini kullanmayı öğrenin.
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
ms.openlocfilehash: bbf233d025d168f3f9d197af5876a0d6e735a9e9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99942405"
---
# <a name="how-to-add-and-delete-counters-on-graphs-in-load-test-results"></a>Nasıl yapılır: Yük Testi Sonuçlarındaki Grafiklerde Sayaç Ekleme ve Silme

Bir grafiğe performans sayaçlarını eklemek için **Sayaçlar** panelini kullanabilirsiniz.

![Grafiğe sayaç eklendi](../test/media/ltest_selectcounter.png)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

**Performans sayacı örnekleme aralığı konuları**

Yük testinin uzunluğuna bağlı olarak yük testi çalıştırma ayarlarındaki **örnek hız** özelliği için bir değer seçin. Beş saniyelik varsayılan değer gibi daha küçük bir örnek hız, yük testi sonuçları veritabanında daha fazla alan gerektirir. Daha uzun yük testleri için, örnek hızının artırılması topladığınız veri miktarını azaltır. Daha fazla bilgi için bkz. [nasıl yapılır: örnek hızını belirtme](../test/how-to-specify-the-sample-rate-for-a-load-test.md).

Örnek ücretler için bazı yönergeler aşağıda verilmiştir:

|Yük testi süresi|Önerilen örnek hızı|
|-|-----------------------------|
|\< 1 saat|5 saniye|
|1-8 saat|15 saniye|
|8-24 saat|30 saniye|
|> 24 saat|60 saniye|

**Yüzdelik veri toplamak için zamanlama ayrıntılarını dahil etme konuları**

**Zamanlama Ayrıntıları Depolaması** adlı Yük Testi Düzenleyicisi çalıştırma ayarlarında bir özellik vardır. **Zamanlama Ayrıntıları Deposu** özelliği etkinleştirilmişse, yük testi sırasında her bir test, işlem ve sayfanın yürütülmesi için geçen süre, yük testi sonuçları deposunda depolanır. Bu, 90. ve 95. yüzdebirlik verilerinin testler, Işlemler ve sayfalar tablolarındaki **Yük Testi Çözümleyicisi** 'nde görüntülenmesini sağlar.

**StatisticsOnly** ve **allindividualdetails** adlı çalışma ayarları özelliklerindeki **Zamanlama Ayrıntıları Depolama** özelliğini etkinleştirmek için iki seçenek vardır. Her iki seçenek de her bir test, sayfa ve işlem zaman aşımına uğramıştır ve yüzdelik veriler bireysel zamanlama verilerinden hesaplanır. Aradaki fark, en fazla yüzdebirlik verisi hesaplanmasından hemen sonra bireysel zamanlama verilerinin depodan silindiği, **StatisticsOnly** seçeneğinin bulunduğu farktır. Bu, zamanlama ayrıntılarını kullandığınızda depoda gereken alan miktarını azaltır. Bununla birlikte, gelişmiş kullanıcılar, SQL araçlarını kullanarak zamanlama ayrıntı verilerini başka yollarla işlemek isteyebilir. Bu durumda, bu işlem için zamanlama ayrıntı verilerinin kullanılabilir olması için **Allindividualdetails** seçeneğinin kullanılması gerekir. Ayrıca, özelliğini **Allindividualdetails** olarak ayarlarsanız, yük testi çalışmayı tamamladıktan sonra **Yük Testi Çözümleyicisi** 'ndeki **Sanal Kullanıcı etkinliği** grafiğini kullanarak sanal kullanıcı etkinliğini çözümleyebilirsiniz. Daha fazla bilgi için bkz. [Ayrıntılar görünümündeki sanal kullanıcı etkinliğini çözümleme](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md).

Zamanlama ayrıntıları verilerini depolamak için yük testi sonuçları deposunda gereken alan miktarı, özellikle daha uzun yük testleri için çok büyük olabilir. Ayrıca, bu verileri yük testinin sonundaki yük testi sonuçları deposunda depolama süresi daha uzundur çünkü bu veriler yük testinin yürütülmesi bitene kadar yük testi aracılarında depolanır. Yük testi tamamlandığında, veriler depoya depolanır. Varsayılan olarak, **Zamanlama Ayrıntıları Depolama** özelliği etkindir. Bu, test ortamınız için bir sorun ise, **zamanlama ayrıntıları depolamayı** **none** olarak ayarlamak isteyebilirsiniz.

Daha fazla bilgi için bkz. [nasıl yapılır: zamanlama ayrıntıları depolama özelliğini belirtme](../test/how-to-specify-the-timing-details-storage-property-for-a-load-test.md).

## <a name="to-display-a-particular-performance-counter-on-a-load-test-graph"></a>Belirli bir performans sayacını bir yük testi grafiğinde görüntüleme

1. Bir yük testi tamamlandıktan sonra veya bir test sonucunu yükledikten sonra, Yük Testi Çözümleyicisi 'nin araç çubuğunda **grafikler**' i seçin.

     **Sayaçlar** paneli, grafikler görünümünde görüntülenir.

    > [!NOTE]
    > **Sayaçlar** paneli görünür değilse, araç çubuğunda **sayaç bölmesini göster** ' i seçin.

2. **Sayaç** panelinde, grafik olarak görüntülenmesini istediğiniz performans sayacını bulana kadar hiyerarşideki düğümler ' i genişletin.

     Örneğin, kullanılabilir belleği testlerin çalıştığı bir bilgisayarda göstermek için **bilgisayarlar**' ı genişletin, bilgisayar düğümünü genişletin ve ardından **bellek**' i genişletin. **Kullanılabilir MBayt** sayacını görürsünüz.

3. Performans sayacını göstermek istediğiniz grafiği seçin.

4. **Sayaçlar** panelinde performans sayacını sağ tıklatın ve **grafikte sayacı göster**' i seçin.

    > [!TIP]
    > Grafik üzerinde performans sayacı verilerini görüntülemeyi geçici olarak durdurmak için, göstergede performans sayacı onay kutusunun işaretini kaldırın. Bu, grafikteki eğilim çizgisini görüntülemeden en düşük, en büyük ve ortalama istatistiklerin çözümlenmeye devam etmesine olanak tanır. Bu, sorunları çözümlemede grafik birden çok çakışan performans sayacı çizimleri içeriyorsa yararlı olabilir. Daha fazla bilgi için bkz. [yük testlerini çözümlemek Için grafik görünümü göstergesini kullanma](../test/use-the-graphs-view-legend-to-analyze-load-tests.md).

5. Grafikten performans sayacı verilerini kaldırmak için göstergenin **sayaç** sütununda performans sayacını sağ tıklatın ve **Sil**' i seçin.

     \- veya

     Grafikteki veri satırına sağ tıklayın ve **Sil**' i seçin.

     \- veya

     Göstergenin **sayaç** sütununda veya grafikteki veri satırında performans sayacını seçin ve ardından **Delete** tuşuna basın.

    > [!NOTE]
    > Gösterge üzerinde **Sayaç Ekle** komutunu kullanarak, göstergeye bir performans sayacı yerleştirmeyi tercih edebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Grafik görünümünde Yük testi sonuçlarını çözümleme](../test/analyze-load-test-results-in-the-graphs-view.md)
- [Nasıl yapılır: özel grafikler oluşturma](../test/how-to-create-custom-graphs-in-load-test-results.md)
