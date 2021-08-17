---
title: Yük Testinde Sayfa Yanıt Süresi
description: Bir web sayfasının yüklenme süresi yanıt süresidir. Web performans testinde her web sayfası isteği için yanıt süresi hedefi ayarlamayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, response times
- response times in load tests
- load test results, response times
ms.assetid: e61c49f3-3161-45b1-9220-08b5459065a2
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: 66084cee9d5d2ba979a2967fbe2782ead65df17f6c3c2130966c5d6db08ac3b4
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121227134"
---
# <a name="how-to-view-web-page-response-time-in-a-load-test-using-the-load-test-analyzer"></a>Nasıl yapabilirsiniz: Yük Testi Çözümleyicisi kullanarak bir yük testinde web sayfası yanıt sürelerini görüntüleme

Her web sayfasının yüklenme süresi yanıt süresi *olarak bilinir.* Bir web performans testi oluşturdukta, web performans testinde her web sayfası isteği için bir yanıt süresi hedefi oluşturabilirsiniz.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Yük testinde stres altında web performans testini çalıştırmanız, her sayfa için aşağıdaki bilgileri analiz edebilirsiniz:

- Sayfa için ortalama yanıt süresi.

- Sayfanın yanıt süresi hedefine uygun test yinelemelerinin yüzdesi.

- Yük Testi Çözümleyicisi'nin Tablolar görünümünü veya Graflar görünümünü kullanarak web sayfası yanıt **süreleri çözümleyebilirsiniz:**

- Tablolar görünümünde web sayfası yanıt süreleri analiz etme

- Graflar görünümünde web sayfası yanıt zamanlarını analiz etme

## <a name="view-response-time-data-in-a-table"></a>Tablodaki yanıt süresi verilerini görüntüleme

1. Yük Testi **Çözümleyicisi'nda,**  tablo kılavuzunda görüntülendiğinden emin olmak için araç çubuğunda Tablolar'ı seçin.

2. Tablo **açılan** listesi kutusunda Sayfalar'ı **seçin.**

3. Her sayfanın verileri kılavuzda görüntülenir. Aşağıdaki sütunlar normalde görüntülenir.

   |Sütun Başlığı|Açıklama|
   |-|-|
   |**Sayfa**|Web sayfasının adı.|
   |**Senaryo**|Senaryonun adı. Web performans testinde birden fazla senaryo varsa önemlidir.|
   |**Test**|Web performans testinin adı. Yük testinde birden fazla web performans testi varsa önemlidir.|
   |**Ağ**|Ağ türü.<br /><br /> Varsayılan olarak, bu veriler toplanmaz. Bu verileri toplamak için, **Yük Testi Düzenleyicisi** altında, Run **Ayarlar** düğümü altında değiştir ayar düğümünü seçin. Özellikler **penceresinde,** Timing **Details** Depolama **allIndividualDetails öğesini seçin.**|
   |**Toplam**|Web sayfası için yapılan isteklerin toplam sayısı. Bu, yük testinde tüm yinelemelerin toplamıdır.|
   |**Ave**|Ortalama sayfa yanıt süresi.<br /><br /> Varsayılan olarak, bu veriler toplanmaz. Bu verileri toplamak için, **Yük Testi Düzenleyicisi** altında, Run **Ayarlar** düğümü altında değiştir ayar düğümünü seçin. Özellikler **penceresinde,** Timing **Details** Depolama **allIndividualDetails öğesini seçin.**|
   |**Dk**|En düşük sayfa yanıt süresi.<br /><br /> Varsayılan olarak, bu veriler toplanmaz. Bu verileri toplamak için, **Yük Testi Düzenleyicisi** altında, Run **Ayarlar** düğümü altında değiştir ayar düğümünü seçin. Özellikler **penceresinde,** Timing **Details** Depolama **allIndividualDetails öğesini seçin.**|
   |**Medyan**|Ortan sayfası yanıt süresi.<br /><br /> Varsayılan olarak, bu veriler toplanmaz. Bu verileri toplamak için, **Yük Testi Düzenleyicisi** altında, Run **Ayarlar** düğümü altında değiştir ayar düğümünü seçin. Özellikler **penceresinde,** Timing **Details** Depolama **allIndividualDetails öğesini seçin.**|
   |**90%**|Yanıt süresi için 90. yüzdebirlik değer. Bu, sayfaların %90'ını bu sayıdan daha hızlı yanıt verdi ve sayfaların %10'larının daha yavaş yanıt verdi olduğunu gösterir.<br /><br /> Varsayılan olarak, bu veriler toplanmaz. Bu verileri toplamak için, **Yük Testi Düzenleyicisi** altında, Run **Ayarlar** düğümü altında değiştir ayar düğümünü seçin. Özellikler **penceresinde,** Timing **Details** Depolama **allIndividualDetails öğesini seçin.**|
   |**%95**|Yanıt süresi için 95. yüzdebirlik değer. Bu, sayfaların %95'inin bu sayıya göre daha hızlı yanıt verdi ve sayfaların %5'i daha yavaş yanıt verdi.|
   |**99%**|Yanıt süresi için 99. yüzdebirlik değer. Bu, sayfaların %99'larının bu sayıya göre daha hızlı yanıt vermelerine ve sayfaların %1'inin daha yavaş yanıt vermelerine neden olduğunu gösterir.<br /><br /> Varsayılan olarak, bu veriler toplanmaz. Bu verileri toplamak için, **Yük Testi Düzenleyicisi** altında, Run **Ayarlar** düğümü altında değiştir ayar düğümünü seçin. Özellikler **penceresinde,** Timing **Details** Depolama **allIndividualDetails öğesini seçin.**|
   |**Max**|En uzun sayfa yanıt süresi.<br /><br /> Varsayılan olarak, bu veriler toplanmaz. Bu verileri toplamak için, **Yük Testi Düzenleyicisi** altında, Run **Ayarlar** düğümü altında değiştir ayar düğümünü seçin. Özellikler **penceresinde,** Timing **Details** Depolama **allIndividualDetails öğesini seçin.**|
   |**Std Dev**|Varsayılan olarak, standart sapma verileri toplanmaz. Bu verileri toplamak için, **Yük Testi Düzenleyicisi** altında, Run **Ayarlar** düğümü altında değiştir ayar düğümünü seçin. Özellikler **penceresinde,** Timing **Details** Depolama **allIndividualDetails öğesini seçin.**|
   |**Sayfa Süresi**|Web sayfası için yapılan tüm isteklerin ortalama yanıt süresi.|
   |**Hedef**|Sayfa süresi hedefi. Bu, sayfa için sabit bir değerdir. **Not:**  Sayfa Süresi Hedefi yalnızca web performans testinde istek için hedef tanımlandığı zaman görüntülenir.|
   |**% Meeting Goal**|Yanıt süresi hedefine uygun web sayfası için yapılan isteklerin yüzdesi.|

   Daha fazla bilgi için Tablolar [görünümündeki Yük testi sonuçlarını ve hatalarını analiz etme makalesi'ne bakın.](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)

## <a name="view-response-time-data-in-a-graph"></a>Yanıt süresi verilerini bir grafikte görüntüleme

Ayrıca, yük testi sırasında zaman içinde nasıl değiştiklerini görmek için yanıt süresi verilerini bir grafikte görüntüebilirsiniz. Bu, özellikle de test çalıştırıldıklarında yük deseniniz artarsa (örneğin, adım yükleme desenini kullanıyorsanız) yararlıdır. Daha fazla bilgi için [bkz. Sanal kullanıcı etkinliklerini modellemek için yük düzenlerini düzenleme.](../test/edit-load-patterns-to-model-virtual-user-activities.md)

Yanıt süresi verilerini bir grafikte görüntülemek için:

1. Yük Testi **Çözümleyicisi'nda,** **grafiğin** görüntülendiğinden emin olmak için araç çubuğunda Grafikler'i seçin.

2. Sayaçlar  penceresinde ilgilendiğimiz senaryonun düğümünü genişletin (örneğin, `Scenario1` ).

3. İlgilenen web performans testinin düğümünü genişletin.

4. Düğüm **Sayfaları'nı genişletin.**

5. İlgilenen sayfanın düğümünü genişletin.

6. Sayfaların Toplantı **Hedefi% seçeneğine sağ tıklayın** ve ardından **hedefte Sayacı Göster'Graph.**

    Veriler grafiye eklenir.

7. (İsteğe bağlı) Önceki adımı **Ort. Sayfa Süresi,** Sayfa Yanıt Süresi Hedefi ve **Toplam** Sayfalar için **tekrarlayın.**

   > [!NOTE]
   > **Sayfa Yanıt Süresi Hedefi** sabittir.

   Daha fazla bilgi için [Bkz. Graflar görünümünde yük testi sonuçlarını analiz etme.](../test/analyze-load-test-results-in-the-graphs-view.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Tablolar görünümünde yük testi sonuçlarını ve hatalarını analiz etme](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)
- [Nasıllı: Analiz için yük testi sonuçlarına erişme](../test/how-to-access-load-test-results-for-analysis.md)
- [Yük testi sonuçlarını analiz etme](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
