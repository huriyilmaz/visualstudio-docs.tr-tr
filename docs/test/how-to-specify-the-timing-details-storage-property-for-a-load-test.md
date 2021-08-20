---
title: Timing Details Depolama özelliği (yük testi çalıştırma ayarı)
description: 'Bir çalıştırma ayarı için Timing Details Depolama özelliğini düzenlemeyi öğrenin. Geçerli değerler: Tüm Bireysel Ayrıntılar, Hiçbiri ve Yalnızca İstatistikler.'
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, properties
- load tests, run settings
ms.assetid: 867a9c21-0909-4963-bc02-d41e9393008c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: d563c8ecfcdd52020e8adb1dfc04856d027fddc8
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122148538"
---
# <a name="how-to-specify-the-timing-details-storage-property-for-a-load-test-run-setting"></a>Nasıllı: Yük testi çalıştırma ayarı için zamanlama ayrıntıları depolama özelliğini belirtme

Yük testini New Yük Testi Sihirbazı ile **oluşturdukta,** ayarları **test Yük Testi Düzenleyicisi** hedeflerinizi karşılayacak şekilde değiştirmek için Yük Testi Düzenleyicisi kullanabilirsiniz.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Özellikler penceresinde bir çalıştırma ayarının **Timing Details Depolama** özelliğinin değerini **düzenleyebilirsiniz.** **Timing Details Depolama** özelliği aşağıdaki seçeneklerden herhangi biri olarak ayarlanmış olabilir:

- **Tüm Bireysel Ayrıntılar:** Test sırasında verilen her test, işlem ve sayfa için ayrı zamanlama verileri toplar ve depolar.

  > [!NOTE]
  > Yük **testi sonuçlarında** sanal kullanıcı veri bilgilerini etkinleştirmek için Tüm Bireysel Ayrıntılar seçeneğinin seçili olması gerekir. Daha fazla bilgi için Ayrıntılar [görünümündeki Sanal kullanıcı etkinliğini analiz etme'ye bakın.](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)

- **Hiçbiri:** Tek tek zamanlama ayrıntılarını toplamaz. Ancak, ortalama değerler hala kullanılabilir.

- **Yalnızca İstatistikler:** Tek tek zamanlama verilerini depolar, ancak yalnızca yüzdebirlik verileri olarak depolar. Bu sayede alan kaynakları tasarruf sağlar.

  **Timing Details Depolama Özelliği ile ilgili önemli noktalar**

  Zamanlama **Ayrıntıları Depolama** etkinse, yük testi sırasında her bir testi, işlemi ve sayfayı yürütme süresi yük testi sonuçları deposunda depolanır. Bu, **Testler,** İşlemler **ve** Sayfalar tablolarında Yük Testi  Çözümleyicisi'ne 90. ve 95. yüzdebirlik **verilerin gösterilmelerini** sağlar.

  Timing **Details Depolama** özelliği etkinleştirilirse, değeri **StatisticsOnly** veya **AllIndividualDetails** olarak ayarlanarak tüm bireysel testler, sayfalar ve işlemler zamanlanmış olur ve tek tek zamanlama verilerinden yüzdebirlik veriler hesaplanır. Fark, **statisticsOnly seçeneğiyle** yüzdebirlik veri hesaplanmasından sonra tek tek zamanlama verileri depodan silinir. Bu, zamanlama ayrıntıları kullanılırken depoda gerekli olan alan miktarını azaltır. Ancak, zamanlama ayrıntısı verilerini SQL araçlarını kullanarak farklı şekillerde işlemeyi tercih ediyor olabilirsiniz. Bu durumda, zamanlama ayrıntısı verilerini bu işleme için kullanılabilir olacak şekilde **AllIndividualDetails** seçeneği kullanılmalıdır. Ayrıca, özelliğini **AllIndividualDetails** olarak ayarsanız, yük testinin çalışma  tamamlandıktan sonra Yük **Testi** Çözümleyicisi'nin Sanal Kullanıcı Etkinlik Grafiği'ne bakarak sanal kullanıcı etkinliğini analiz edersiniz. Daha fazla bilgi için Ayrıntılar [görünümündeki Sanal kullanıcı etkinliğini analiz etme'ye bakın.](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)

  Yük testi sonuçları deposunda zamanlama ayrıntıları verilerini depolamak için gereken alan miktarı, özellikle de daha uzun süre çalışan yük testleri için çok büyük olabilir. Ayrıca, yük testinin sonundaki yük testi sonuçları deposunda bu verilerin depolandığı süre daha uzun olur çünkü bu veriler yük testi yürütülinceye kadar yük testi aracılarında depolanır ve veriler depoda depolanır. Timing **Details Depolama** özelliği varsayılan olarak etkindir. Bu test ortamınız için bir sorunsa Zamanlama Ayrıntıları'nın Hiçbiri olarak **Depolama** **olabilir.**

  Zamanlama ayrıntıları verileri, çalıştırma sırasında *LoadTestItemResults.dat* dosyasında depolanır ve yük testi tamamlandıktan sonra denetleyiciye geri gönderilir. Uzun süre çalışan bir yük testi için dosyanın boyutu büyüktür. Aracı makinede yeterli disk alanı yoksa bu soruna neden olur.

  Bir projeyi yük testinin önceki bir sürümünden Visual Studio, tam ayrıntı toplamayı etkinleştirmek için aşağıdaki yordamı kullanın.

## <a name="to-configure-the-timing-details-storage-property-in-a-load-test"></a>Yük testinde zamanlama ayrıntıları depolama özelliğini yapılandırmak için

1. Yük testi düzenleyicisinde bir yük testi açın.

2. Yük **testinde Ayarlar** düğümünü genişletin.

3. Yapılandırmak istediğiniz çalıştırma ayarlarını seçin, örneğin Çalıştırma **Ayarları1[Etkin]**.

4. Özellikler **Penceresini** açın. Görünüm menüsünde **Özellikler** **Penceresi'ne tıklayın.**

5. Sonuçlar **kategorisinin** altında Timing Details Depolama **özelliğini** ve ardından Tüm Bireysel **Ayrıntılar'ı seçin.**

     Timing **Details** Depolama  özelliği için Tüm Bireysel Ayrıntılar ayarını yapılandırdıktan sonra yük testini çalıştırarak Sanal Kullanıcı Etkinlik **Grafiği'ne bakabilirsiniz.** Daha fazla bilgi için, [bkz. How to: Analyze what virtual users are doing during a load test](../test/how-to-analyze-virtual-user-activity-during-a-load-test.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Ayrıntılar görünümünde sanal kullanıcı etkinliğini analiz etme](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)
- [Adım adım kılavuz: Sorunları yalıtmak için Sanal Kullanıcı Etkinlik Grafiği'nin kullanımı](../test/walkthrough-use-the-virtual-user-activity-chart-to-isolate-issues.md)
