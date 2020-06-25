---
title: Yük testi çalışma ayarı için zamanlama ayrıntıları depolama özelliği
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, properties
- load tests, run settings
ms.assetid: 867a9c21-0909-4963-bc02-d41e9393008c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0225ae23ed141b317d4424da573593d446766f43
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85287317"
---
# <a name="how-to-specify-the-timing-details-storage-property-for-a-load-test-run-setting"></a>Nasıl yapılır: bir yük testi çalışma ayarı için zamanlama ayrıntıları depolama özelliğini belirtme

**Yeni Yük Testi Sihirbazı**yük testinizi oluşturduktan sonra, ayarları test ihtiyaçlarını ve hedeflerinizi karşılayacak şekilde değiştirmek için **Yük Testi Düzenleyicisi** kullanabilirsiniz.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Çalışma ayarının **Zamanlama Ayrıntıları Depolama** özelliğinin değerini **Özellikler** penceresinde düzenleyebilirsiniz. **Zamanlama Ayrıntıları Depolama** özelliği aşağıdaki seçeneklerden herhangi birine ayarlanabilir:

- **Tüm Bireysel Ayrıntılar:** Test sırasında verilen her test, işlem ve sayfa için bireysel zamanlama verilerini toplar ve depolar.

  > [!NOTE]
  > Yük testi sonuçlarınızda Sanal Kullanıcı veri bilgilerini etkinleştirmek için **Tüm Bireysel Ayrıntılar** seçeneğinin seçilmesi gerekir. Daha fazla bilgi için bkz. [Ayrıntılar görünümündeki sanal kullanıcı etkinliğini çözümleme](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md).

- **Hiçbiri:** Bireysel zamanlama ayrıntıları toplanmaz. Ancak, ortalama değerler hala kullanılabilir.

- **Yalnızca İstatistikler:** Tek tek zamanlama verilerini depolar, ancak yalnızca yüzdebirlik verisi olarak. Bu alan kaynakları kaydeder.

  **Zamanlama Ayrıntıları Depolama özelliği için değerlendirmeler**

  **Zamanlama Ayrıntıları Deposu** özelliği etkinleştirilmişse, yük testi sırasında her bir test, işlem ve sayfanın yürütülmesi için geçen süre, yük testi sonuçları deposunda depolanır. Bu, 90. ve 95. yüzdebirlik verilerinin **testler**, **işlemler**ve **Sayfalar** tablolarındaki **Yük Testi Çözümleyicisi** 'nde görüntülenmesini sağlar.

  **Zamanlama Ayrıntıları Depolama** özelliği etkinleştirilmişse, değerini **StatisticsOnly** veya **allindividualdetails**olarak ayarlayarak, tüm bireysel testler, sayfalar ve işlemler zaman aşımına uğramıştır ve yüzdelik veriler bireysel zamanlama verilerinden hesaplanır. Aradaki fark, bir yüzdebirlik verileri hesaplandıktan sonra, bireysel zamanlama verilerinin depodan silindiği, **StatisticsOnly** seçeneğinin bulunduğu farktır. Bu, zamanlama ayrıntıları kullanıldığında depoda gereken alan miktarını azaltır. Bununla birlikte, zamanlama ayrıntı verilerini SQL araçlarını kullanarak başka yollarla işlemek isteyebilirsiniz, bu durumda **Allindividualdetails** seçeneği bu işlem için zamanlama ayrıntı verilerinin kullanılabilir olması için kullanılmalıdır. Ayrıca, özelliğini **Allindividualdetails**olarak ayarlarsanız, yük testi çalışmayı tamamladıktan sonra **Yük Testi Çözümleyicisi** 'Ndeki **Sanal Kullanıcı etkinliği grafiğini** kullanarak sanal kullanıcı etkinliğini çözümleyebilirsiniz. Daha fazla bilgi için bkz. [Ayrıntılar görünümündeki sanal kullanıcı etkinliğini çözümleme](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md).

  Zamanlama ayrıntıları verilerini depolamak için yük testi sonuçları deposunda gereken alan miktarı, özellikle daha uzun yük testleri için çok büyük olabilir. Ayrıca, bu verileri yük testinin sonundaki yük testi sonuçları deposunda depolama süresi daha uzundur, çünkü bu veriler yük testi yürütmeyi tamamlayana kadar yük testinin yürütülmesi bitene kadar, verilerin depoya depolandığı zaman. **Zamanlama Ayrıntıları Depolama** özelliği varsayılan olarak etkindir. Bu, test ortamınız için bir sorun ise, **zamanlama ayrıntıları depolamayı** **none**olarak ayarlamak isteyebilirsiniz.

  Zamanlama ayrıntıları verileri çalıştırma sırasında *Loadtestemresults. dat* dosyasında depolanır ve yük testi tamamlandıktan sonra denetleyiciye geri gönderilir. Uzun süre çalışan bir yük testi için, dosyanın boyutu büyük olur. Aracı makinede yeterli disk alanı yoksa, bu bir sorun olacaktır.

  Visual Studio yük testinin önceki bir sürümünden bir projeyi yükseltiyorsanız, tam ayrıntı toplamayı etkinleştirmek için aşağıdaki yordamı kullanın.

## <a name="to-configure-the-timing-details-storage-property-in-a-load-test"></a>Bir yük testinde zamanlama ayrıntıları depolama özelliğini yapılandırmak için

1. Yük testi düzenleyicisinde bir yük testi açın.

2. Yük testinde **çalışma ayarları** düğümünü genişletin.

3. Yapılandırmak istediğiniz çalıştırma ayarlarını seçin, örneğin **Ayarları1 [etkin] çalıştırın**.

4. **Özellikler** penceresini açın. **Görünüm** menüsünde **Özellikler penceresi**' ni seçin.

5. **Sonuçlar** kategorisi altında **Zamanlama Ayrıntıları Depolama** özelliğini seçin ve **Tüm Bireysel Ayrıntılar**' ı seçin.

     **Zamanlama Ayrıntıları Depolaması** özelliği Için **Tüm Bireysel Ayrıntılar** ayarlarını yapılandırdıktan sonra, yük testinizi çalıştırabilir ve **Sanal Kullanıcı etkinliği grafiğini**görüntüleyebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: yük testi sırasında sanal kullanıcıların ne yaptığını çözümleme](../test/how-to-analyze-virtual-user-activity-during-a-load-test.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Ayrıntılar görünümündeki sanal kullanıcı etkinliğini çözümleme](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)
- [İzlenecek yol: sorunları yalıtmak için Sanal Kullanıcı etkinliği grafiğini kullanma](../test/walkthrough-use-the-virtual-user-activity-chart-to-isolate-issues.md)
