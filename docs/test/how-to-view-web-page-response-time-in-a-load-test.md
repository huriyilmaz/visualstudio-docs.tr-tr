---
title: Yük Testinde Sayfa Yanıt Süresi
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, response times
- response times in load tests
- load test results, response times
ms.assetid: e61c49f3-3161-45b1-9220-08b5459065a2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cf8bc1205658899a51cf1a50e83a9a8b34034b25
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75594345"
---
# <a name="how-to-view-web-page-response-time-in-a-load-test-using-the-load-test-analyzer"></a>Nasıl yapilir: Yük Testi Çözümleyicisini kullanarak yük testinde web sayfası yanıt süresini görüntüleme

Her web sayfasının yüklenmesi için gereken süre *yanıt süresi*olarak bilinir. Bir web performans testi oluşturduğunuzda, web performans testinizdeki her web sayfası isteği için bir yanıt süresi hedefi ayarlayabilirsiniz.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Web performans testinizi bir yük testinde stres altında çalıştırın, her sayfa için aşağıdaki bilgileri analiz edebilirsiniz:

- Sayfanın ortalama yanıt süresi.

- Sayfanın yanıt süresi hedefini karşılayan test yinelemelerinin yüzdesi.

- Yük Testi Çözümleyicisi'ndeki Tablolar görünümünü veya Grafikler **Load Test Analyzer**görünümünü kullanarak web sayfası yanıt sürelerini analiz edebilirsiniz:

- Tablo görünümünde web sayfası yanıt sürelerini analiz etme

- Grafikler görünümünde web sayfası yanıt sürelerini analiz etme

## <a name="view-response-time-data-in-a-table"></a>Yanıt süresi verilerini tabloda görüntüleme

1. Yük **Testi Çözümleyicisi'nde,** tablo ızgarasının görüntülendiğinden emin olmak için araç çubuğundaki **Tablolar'ı** seçin.

2. **Tablo** açılır liste kutusunda **Sayfalar'ı**seçin.

3. Her sayfanın verileri ızgarada görüntülenir. Aşağıdaki sütunlar normalde görüntülenir.

   |Sütun Başlığı|Açıklama|
   |-|-|
   |**Sayfası**|Web sayfasının adı.|
   |**Senaryo**|Senaryonun adı. Web performans testinizde birden fazla senaryo varsa önemlidir.|
   |**Test**|Web performans testinin adı. Yük testinizde birden fazla web performans testi varsa önemlidir.|
   |**Ağ**|Ağ türü.<br /><br /> Varsayılan olarak, bu veriler toplanmaz. Bu verileri toplamak için, **Çalıştır Ayarları** düğümünün altındaki Yük Testi Düzenleyicisi'nde, değiştirmek için çalıştır ayar düğümünü seçin. **Load Test Editor** **Özellikler** penceresinde, Zamanlama **Ayrıntıları Depolama** özelliği için **AllIndividualDetails'ı**seçin.|
   |**Toplam**|Web sayfası için yapılan toplam istek sayısı. Bu, yük testindeki tüm yinelemelerin toplamıdır.|
   |**Ave**|Ortalama sayfa yanıt süresi.<br /><br /> Varsayılan olarak, bu veriler toplanmaz. Bu verileri toplamak için, **Çalıştır Ayarları** düğümünün altındaki Yük Testi Düzenleyicisi'nde, değiştirmek için çalıştır ayar düğümünü seçin. **Load Test Editor** **Özellikler** penceresinde, Zamanlama **Ayrıntıları Depolama** özelliği için **AllIndividualDetails'ı**seçin.|
   |**Dk**|Minimum sayfa yanıt süresi.<br /><br /> Varsayılan olarak, bu veriler toplanmaz. Bu verileri toplamak için, **Çalıştır Ayarları** düğümünün altındaki Yük Testi Düzenleyicisi'nde, değiştirmek için çalıştır ayar düğümünü seçin. **Load Test Editor** **Özellikler** penceresinde, Zamanlama **Ayrıntıları Depolama** özelliği için **AllIndividualDetails'ı**seçin.|
   |**Medyan**|Ortanca sayfa yanıt süresi.<br /><br /> Varsayılan olarak, bu veriler toplanmaz. Bu verileri toplamak için, **Çalıştır Ayarları** düğümünün altındaki Yük Testi Düzenleyicisi'nde, değiştirmek için çalıştır ayar düğümünü seçin. **Load Test Editor** **Özellikler** penceresinde, Zamanlama **Ayrıntıları Depolama** özelliği için **AllIndividualDetails'ı**seçin.|
   |**90%**|Yanıt süresi için yüzde 90. Bu, sayfaların %90'ının bu sayıdan daha hızlı yanıt verdiğini ve sayfaların %10'unun daha yavaş yanıt verdiğini gösterir.<br /><br /> Varsayılan olarak, bu veriler toplanmaz. Bu verileri toplamak için, **Çalıştır Ayarları** düğümünün altındaki Yük Testi Düzenleyicisi'nde, değiştirmek için çalıştır ayar düğümünü seçin. **Load Test Editor** **Özellikler** penceresinde, Zamanlama **Ayrıntıları Depolama** özelliği için **AllIndividualDetails'ı**seçin.|
   |**95%**|Yanıt süresi için yüzde 95. Bu, sayfaların %95'inin bu sayıdan daha hızlı yanıt verdiğini ve sayfaların %5'inin daha yavaş yanıt verdiğini gösterir.|
   |**%99**|Yanıt süresi için yüzde 99. Bu, sayfaların %99'unun bu sayıdan daha hızlı yanıt verdiğini ve sayfaların %1'inin daha yavaş yanıt verdiğini gösterir.<br /><br /> Varsayılan olarak, bu veriler toplanmaz. Bu verileri toplamak için, **Çalıştır Ayarları** düğümünün altındaki Yük Testi Düzenleyicisi'nde, değiştirmek için çalıştır ayar düğümünü seçin. **Load Test Editor** **Özellikler** penceresinde, Zamanlama **Ayrıntıları Depolama** özelliği için **AllIndividualDetails'ı**seçin.|
   |**Max**|Maksimum sayfa yanıt süresi.<br /><br /> Varsayılan olarak, bu veriler toplanmaz. Bu verileri toplamak için, **Çalıştır Ayarları** düğümünün altındaki Yük Testi Düzenleyicisi'nde, değiştirmek için çalıştır ayar düğümünü seçin. **Load Test Editor** **Özellikler** penceresinde, Zamanlama **Ayrıntıları Depolama** özelliği için **AllIndividualDetails'ı**seçin.|
   |**Std Dev**|Varsayılan olarak, standart sapma verileri toplanmaz. Bu verileri toplamak için, **Çalıştır Ayarları** düğümünün altındaki Yük Testi Düzenleyicisi'nde, değiştirmek için çalıştır ayar düğümünü seçin. **Load Test Editor** **Özellikler** penceresinde, Zamanlama **Ayrıntıları Depolama** özelliği için **AllIndividualDetails'ı**seçin.|
   |**Sayfa Saati**|Web sayfası için yapılan tüm isteklerin ortalama yanıt süresi.|
   |**Hedef**|Sayfa zaman hedefi. Bu sayfa için sabit bir değerdir. **Not:**  Sayfa Süresi Hedefi yalnızca web performans testinde istek için hedef tanımlandığında görüntülenir.|
   |**% Toplantı Hedefi**|Yanıt süresi hedefini karşılayan web sayfası için yapılan isteklerin yüzdesi.|

   Daha fazla bilgi için bkz: [Tablolar görünümünde yük testi sonuçlarını ve hatalarını analiz](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)et.

## <a name="view-response-time-data-in-a-graph"></a>Yanıt süresi verilerini grafikte görüntüleme

Ayrıca, yük testiniz sırasında zaman içinde nasıl değiştiğini görmek için yanıt süresi verilerini grafikte görüntüleyebilirsiniz. Bu, özellikle test devam ettikçe yük deseniniz artarsa (örneğin, adım yük modelini kullanıyorsanız) kullanışlıdır. Daha fazla bilgi [için, sanal kullanıcı etkinliklerini modellemek için yük desenlerini düzenle'ye](../test/edit-load-patterns-to-model-virtual-user-activities.md)bakın.

Yanıt süresi verilerini grafikte görüntülemek için:

1. Yük **Testi Çözümleyicisi'nde,** grafiğin görüntülendiğinden emin olmak için araç çubuğundaki **Grafikler'i** seçin.

2. **Sayaçlar** penceresinde, ilgilendiğiniz senaryonun düğümlerini genişletin (örneğin, `Scenario1`).

3. İlgilendiğiniz web performans testinin düğümlerini genişletin.

4. Düğüm **Sayfalarını**genişletin.

5. İlgilendiğiniz sayfanın düğümlerini genişletin.

6. **% Sayfaları Toplantı Hedefi'ni** sağ tıklatın ve ardından **Grafikte Sayacı Göster'i**seçin.

    Veriler grafiğe eklenir.

7. (İsteğe bağlı) **Sayfa Saati, Sayfa**Yanıt Süresi **Hedefi**ve Toplam **Sayfalar**için önceki adımı yineleyin.

   > [!NOTE]
   > **Sayfa Yanıt Süresi Hedefi** sabittir.

   Daha fazla bilgi için bkz: [Grafikler görünümünde yük testi sonuçlarını analiz](../test/analyze-load-test-results-in-the-graphs-view.md)et.

## <a name="see-also"></a>Ayrıca bkz.

- [Tablolar görünümünde yük testi sonuçlarını ve hatalarını analiz etme](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)
- [Nasıl yapılı: Analiz için yük testi sonuçlarına erişin](../test/how-to-access-load-test-results-for-analysis.md)
- [Yük testi sonuçlarını analiz edin](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
