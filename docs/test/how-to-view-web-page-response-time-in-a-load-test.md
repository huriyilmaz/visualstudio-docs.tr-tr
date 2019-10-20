---
title: Yük testinde sayfa yanıt süresi
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, response times
- response times in load tests
- load test results, response times
ms.assetid: e61c49f3-3161-45b1-9220-08b5459065a2
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5fbaa3f8f322bc6633e4f5081ba4cae38b581b95
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72653293"
---
# <a name="how-to-view-web-page-response-time-in-a-load-test-using-the-load-test-analyzer"></a>Nasıl yapılır: Yük Testi Çözümleyicisini kullanarak yük testinde Web sayfası yanıt süresini görüntüleme

Her Web sayfasının yüklenmesi için gereken süre *yanıt süresi*olarak bilinir. Web performans testi oluşturduğunuzda, Web performans testinizde her bir Web sayfası isteği için bir yanıt süresi hedefi ayarlayabilirsiniz.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Web performans testinizi yük testinde stres altında çalıştırırsanız, her sayfa için aşağıdaki bilgileri çözümleyebilirsiniz:

- Sayfa için Ortalama yanıt süresi.

- Sayfa için yanıt süresi hedefini karşılayan test yinelemelerinin yüzdesi.

- **Yük Testi Çözümleyicisi**'ndeki tablolar görünümünü veya grafik görünümünü kullanarak Web sayfası yanıt sürelerini çözümleyebilirsiniz:

- Tablolar görünümünde Web sayfası yanıt sürelerini çözümleme

- Grafik görünümündeki Web sayfası yanıt sürelerini çözümleme

## <a name="view-response-time-data-in-a-table"></a>Bir tablodaki yanıt süresi verilerini görüntüleme

1. **Yük Testi Çözümleyicisi**'nde tablo kılavuzunun görüntülendiğinden emin olmak için araç çubuğunda **Tablolar** ' ı seçin.

2. **Tablo** aşağı açılan liste kutusunda **Sayfalar**' ı seçin.

3. Her sayfanın verileri kılavuzda görüntülenir. Aşağıdaki sütunlar normalde görüntülenir.

   |Sütun başlığı|Açıklama|
   |-|-|
   |**Sayfasında**|Web sayfasının adı.|
   |**Senaryo**|Senaryonun adı. Web performans testinizde birden fazla senaryonuz varsa önemlidir.|
   |**Test**|Web performans testinin adı. Yük testinizde birden fazla Web performans testiniz varsa önemlidir.|
   |**Network**|Ağ türü.<br /><br /> Varsayılan olarak, bu veriler toplanmaz. Bu verileri toplamak için, **Yük Testi Düzenleyicisi**, **çalışma ayarları** düğümü altında, değiştirilecek çalışma ayarı düğümünü seçin. **Özellikler** penceresinde, **Zamanlama Ayrıntıları Deposu** özelliği Için, **alllindividualdetails**' i seçin.|
   |**Toplamda**|Web sayfası için yapılan isteklerin toplam sayısı. Bu, yük testinde tüm yinelemeler için toplamdır.|
   |**Ortalama**|Ortalama sayfa yanıt süresi.<br /><br /> Varsayılan olarak, bu veriler toplanmaz. Bu verileri toplamak için, **Yük Testi Düzenleyicisi**, **çalışma ayarları** düğümü altında, değiştirilecek çalışma ayarı düğümünü seçin. **Özellikler** penceresinde, **Zamanlama Ayrıntıları Deposu** özelliği Için, **alllindividualdetails**' i seçin.|
   |**Min**|En küçük sayfa yanıt süresi.<br /><br /> Varsayılan olarak, bu veriler toplanmaz. Bu verileri toplamak için, **Yük Testi Düzenleyicisi**, **çalışma ayarları** düğümü altında, değiştirilecek çalışma ayarı düğümünü seçin. **Özellikler** penceresinde, **Zamanlama Ayrıntıları Deposu** özelliği Için, **alllindividualdetails**' i seçin.|
   |**Ortanca**|Ortanca sayfa yanıt süresi.<br /><br /> Varsayılan olarak, bu veriler toplanmaz. Bu verileri toplamak için, **Yük Testi Düzenleyicisi**, **çalışma ayarları** düğümü altında, değiştirilecek çalışma ayarı düğümünü seçin. **Özellikler** penceresinde, **Zamanlama Ayrıntıları Deposu** özelliği Için, **alllindividualdetails**' i seçin.|
   |**%90**|Yanıt süresi için 90. yüzdebirlik. Bu, sayfaların %90 ' unun bu sayıdan daha hızlı yanıt verdiğini ve sayfaların %10 ' unun daha yavaş yanıt verdiğini gösterir.<br /><br /> Varsayılan olarak, bu veriler toplanmaz. Bu verileri toplamak için, **Yük Testi Düzenleyicisi**, **çalışma ayarları** düğümü altında, değiştirilecek çalışma ayarı düğümünü seçin. **Özellikler** penceresinde, **Zamanlama Ayrıntıları Deposu** özelliği Için, **alllindividualdetails**' i seçin.|
   |**%95**|Yanıt süresi için 95. yüzdebirlik. Bu, sayfaların %95 ' unun bu sayıdan daha hızlı yanıt verdiğini ve sayfaların %5 ' unun daha yavaş yanıt verdiğini gösterir.|
   |**%99**|Yanıt süresi için 99. yüzdebirlik. Bu, sayfaların %99 ' unun bu sayıdan daha hızlı yanıt verdiğini ve sayfaların %1 ' unun daha yavaş yanıt verdiğini gösterir.<br /><br /> Varsayılan olarak, bu veriler toplanmaz. Bu verileri toplamak için, **Yük Testi Düzenleyicisi**, **çalışma ayarları** düğümü altında, değiştirilecek çalışma ayarı düğümünü seçin. **Özellikler** penceresinde, **Zamanlama Ayrıntıları Deposu** özelliği Için, **alllindividualdetails**' i seçin.|
   |**Biçimlendir**|En fazla sayfa yanıt süresi.<br /><br /> Varsayılan olarak, bu veriler toplanmaz. Bu verileri toplamak için, **Yük Testi Düzenleyicisi**, **çalışma ayarları** düğümü altında, değiştirilecek çalışma ayarı düğümünü seçin. **Özellikler** penceresinde, **Zamanlama Ayrıntıları Deposu** özelliği Için, **alllindividualdetails**' i seçin.|
   |**STD dev**|Varsayılan olarak, standart sapma verileri toplanmaz. Bu verileri toplamak için, **Yük Testi Düzenleyicisi**, **çalışma ayarları** düğümü altında, değiştirilecek çalışma ayarı düğümünü seçin. **Özellikler** penceresinde, **Zamanlama Ayrıntıları Deposu** özelliği Için, **alllindividualdetails**' i seçin.|
   |**Sayfa saati**|Web sayfası için yapılan tüm isteklere yönelik ortalama yanıt süresi.|
   |**B**|Sayfa saati hedefi. Bu sayfa için sabit bir değerdir. **Note:**  Sayfa saati hedefi yalnızca hedef, Web performans testinde istek için tanımlandığında görüntülenir.|
   |**% Toplantı hedefi**|Yanıt süresi hedefini karşılayan Web sayfası için yapılan isteklerin yüzdesi.|

   Daha fazla bilgi için bkz. [Tablolar görünümünde Yük testi sonuçlarını ve hatalarını çözümleme](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

## <a name="view-response-time-data-in-a-graph"></a>Bir grafikteki yanıt süresi verilerini görüntüleme

Ayrıca, yanıt süresi verilerini bir grafik halinde görüntüleyerek yük testiniz sırasında zaman içinde nasıl değiştiği hakkında bilgi alabilirsiniz. Bu özellikle, yük düzeniniz test çalıştırmaları (örneğin, adım yükleme modelini kullanıyorsanız) arttıkça yararlı olur. Daha fazla bilgi için bkz. [Sanal Kullanıcı etkinliklerini modellemek için yük düzenlerini düzenleme](../test/edit-load-patterns-to-model-virtual-user-activities.md).

Yanıt süresi verilerini bir grafikte görüntülemek için:

1. **Yük Testi Çözümleyicisi**' nde, grafiğin görüntülendiğinden emin olmak için araç çubuğunda **grafikler** ' i seçin.

2. **Sayaçlar** penceresinde, ilgilendiğiniz senaryonun düğümünü genişletin (örneğin, `Scenario1`).

3. İlgilendiğiniz Web performans testinin düğümünü genişletin.

4. Düğüm **sayfalarını**genişletin.

5. İlgilendiğiniz sayfanın düğümünü genişletin.

6. " **Hedef Toplantı sayfası** " na sağ tıkladıktan sonra **grafik üzerinde sayacı göster**' i seçin.

    Veriler grafiğe eklenir.

7. Seçim **Ortalama sayfa zamanı**, **sayfa yanıt süresi hedefi**ve **Toplam sayfa**için önceki adımı tekrarlayın.

   > [!NOTE]
   > **Sayfa yanıt süresi hedefi** sabittir.

   Daha fazla bilgi için bkz. [Grafik görünümünde Yük testi sonuçlarını çözümleme](../test/analyze-load-test-results-in-the-graphs-view.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Tablolar görünümünde Yük testi sonuçlarını ve hatalarını çözümleme](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)
- [Nasıl yapılır: analiz için yük testi sonuçlarına erişme](../test/how-to-access-load-test-results-for-analysis.md)
- [Yük testi sonuçlarını çözümle](../test/analyze-load-test-results-using-the-load-test-analyzer.md)