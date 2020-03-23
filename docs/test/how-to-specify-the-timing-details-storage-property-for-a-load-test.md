---
title: Yük Testi Çalıştırma Ayarı Için Zamanlama Ayrıntıları Depolama Özelliği
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, properties
- load tests, run settings
ms.assetid: 867a9c21-0909-4963-bc02-d41e9393008c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fbd3b2a7d7e56870a994af288f5887f1d86256af
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591651"
---
# <a name="how-to-specify-the-timing-details-storage-property-for-a-load-test-run-setting"></a>Nasıl yapilir: Yük testi ayarı için zamanlama ayrıntıları depolama özelliğini belirtin

**Yeni Yük Testi Sihirbazı**ile yük testinizi oluşturduktan sonra, test ihtiyaçlarınızı ve hedeflerinizi karşılamak için ayarları değiştirmek için Yük Testi Düzenleyicisi'ni kullanabilirsiniz. **Load Test Editor**

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Çalışma ayarının Zamanlama Ayrıntıları **Depolama** özelliğinin değerini **Özellikler** penceresinde ayarlayabilirsiniz. **Zamanlama Ayrıntıları Depolama** özelliği aşağıdaki seçeneklerden herhangi biri olarak ayarlanabilir:

- **Tüm Bireysel Ayrıntılar:** Test sırasında verilen her test, işlem ve sayfa için ayrı zamanlama verilerini toplar ve depolar.

  > [!NOTE]
  > **Tüm Bireysel Ayrıntılar** seçeneği, yük testi sonuçlarınızda sanal kullanıcı veri bilgilerini etkinleştirmek için seçilmelidir. Daha fazla bilgi için ayrıntılar [görünümünde sanal kullanıcı etkinliğini analiz et'](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)e bakın.

- **Yok:** Herhangi bir bireysel zamanlama ayrıntıları toplamaz. Ancak, ortalama değerler hala kullanılabilir.

- **Yalnızca İstatistikler:** Tek tek zamanlama verilerini, ancak yalnızca yüzdelik veri olarak depolar. Bu, alan kaynaklarını kaydeder.

  **Zamanlama Ayrıntıları Depolama Özelliği için Dikkat Edilecek Noktalar**

  Zamanlama **Ayrıntıları Depolama** özelliği etkinleştirilirse, yükleme testi sırasında her bir testi, hareketi ve sayfayı yürütme süresi yük testi sonuçları deposunda depolanır. Bu, **Testler,** **İşlemler**ve **Sayfalar** tablolarında Yük **Testi Çözümleyicisi'nde** 90 ve 95 yüzdelik verilerin gösterilmesini sağlar.

  Zamanlama **Ayrıntıları Depolama** özelliği etkinleştirilirse, değerini **StatisticsOnly** veya **AllIndividualDetails**olarak ayarlayarak, tüm tek tek testler, sayfalar ve hareketler zamanlanır ve yüzdelik veriler tek tek zamanlama verilerinden hesaplanır. Aradaki fark, **StatisticsOnly** seçeneğiyle, yüzdelik veriler hesaplandıktan sonra, tek tek zamanlama verilerinin depodan silinmiş olmasıdır. Bu, zamanlama ayrıntıları kullanıldığında depoda gereken alan miktarını azaltır. Ancak, zamanlama ayrıntısı verilerini SQL araçlarını kullanarak başka şekillerde işlemek isteyebilirsiniz, bu durumda **AllIndividualDetails** seçeneği bu işlem için zamanlama ayrıntısı verilerinin kullanılabilmesi için kullanılmalıdır. Ayrıca, özelliği **AllIndividualDetails**olarak ayarlarsanız, yük testi çalışma tamamlandıktan sonra **Yük Testi Çözümleyicisi'ndeki** Sanal Kullanıcı Etkinlik **Grafiği'ni** kullanarak sanal kullanıcı etkinliğini çözümleyebilirsiniz. Daha fazla bilgi için ayrıntılar [görünümünde sanal kullanıcı etkinliğini analiz et'](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)e bakın.

  Zamanlama ayrıntıları verilerini depolamak için yük testi sonuçları deposunda gereken alan miktarı, özellikle daha uzun çalışan yük testleri için çok büyük olabilir. Ayrıca, bu verileri yük testinin sonundaki yük testi sonuçları deposunda depolama süresi daha uzundur, çünkü bu veriler yük testi yürütme tamamlanana kadar yük testi aracılarında depolanır ve bu süre içinde veriler depoya saklanır. **Zamanlama Ayrıntıları Depolama** özelliği varsayılan olarak etkinleştirilir. Bu, test ortamınız için bir sorunsa, **Zamanlama Ayrıntıları Depolamasını** **Yok**olarak ayarlamak isteyebilirsiniz.

  Zamanlama ayrıntıları verileri çalışma sırasında *LoadTestItemResults.dat* dosyasında saklanır ve yük testi tamamlandıktan sonra denetleyiciye geri gönderilir. Uzun süre çalışan bir yük testi için dosyanın boyutu büyüktür. Aracı makinesinde yeterli disk alanı yoksa, bu bir sorun olacaktır.

  Bir projeyi Visual Studio yükleme testinin önceki sürümünden yükseltiyorsanız, tam ayrıntı toplamayı etkinleştirmek için aşağıdaki yordamı kullanın.

## <a name="to-configure-the-timing-details-storage-property-in-a-load-test"></a>Yükleme testinde zamanlama ayrıntıları depolama özelliğini yapılandırmak için

1. Yük testi düzenleyicisinde bir yük testi açın.

2. Yük testinde **Ayarlar** düğümlerini genişletin.

3. Yapılandırmak istediğiniz çalıştır ayarlarını seçin (örneğin **Ayarlar1'ı Çalıştır[Etkin]**.

4. **Özellikler** Penceresini açın. **Görünüm** menüsünde **Özellikler Penceresi'ni**seçin.

5. **Sonuçlar** kategorisi altında, **Zamanlama Ayrıntıları Depolama** özelliğini seçin ve Tüm **Bireysel Ayrıntılar'ı**seçin.

     **Zamanlama Ayrıntıları Depolama** özelliği için Tüm Bireysel **Ayrıntılar** ayarını yapılandırdıktan sonra, yük testinizi çalıştırabilir ve Sanal Kullanıcı **Etkinlik Grafiği'ni**görüntüleyebilirsiniz. Daha fazla bilgi için [bkz: Nasıl yapılır: Sanal kullanıcıların yükleme testi sırasında ne yaptığını analiz](../test/how-to-analyze-virtual-user-activity-during-a-load-test.md)edin.

## <a name="see-also"></a>Ayrıca bkz.

- [Ayrıntılar görünümünde sanal kullanıcı etkinliğini analiz edin](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)
- [Walkthrough: Sorunları yalıtmak için Sanal Kullanıcı Etkinlik Grafiği'ni kullanma](../test/walkthrough-use-the-virtual-user-activity-chart-to-isolate-issues.md)
