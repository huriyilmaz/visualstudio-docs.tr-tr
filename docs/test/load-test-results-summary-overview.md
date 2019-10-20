---
title: Yük Testi Sonuçları Özetine Genel Bakış
ms.date: 10/19/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.monitor.summary.view
helpviewer_keywords:
- load test results, summary
- load tests, summary in analyzer
- load tests, results summary
- Load Test Viewer, summary
- load tests, summary in Load Test Viewer
ms.assetid: 326b6c3c-5378-452b-8ca3-ba5a06ab3d41
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ba72bc9d4e63e1ccb1e6d8c05d20332880e19ea9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652986"
---
# <a name="load-test-results-summary-overview"></a>Yük testi sonuçları özetine genel bakış

Yük testini çalıştırdıktan sonra, sonuçları hızla anlamak için yük testi özetini görüntüleyebilirsiniz. Yük Testi Özeti, önemli sonuçları kompakt ve kolay okunabilir biçimde sağlar. Yük testi özetini de yazdırabilirsiniz. Bu, sonuçları paydaşlara iletmenin kullanımını kolaylaştırır. Yük Testi Özeti, daha önce çalıştırılan bir yük testinin yük testi sonucunu açtığınızda de varsayılan görünümüdür. Daha fazla bilgi için bkz. [nasıl yapılır: çözümleme için yük testi sonuçlarına erişme](../test/how-to-access-load-test-results-for-analysis.md).

![Özet görünümü](../test/media/ltest_summaryview.png)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="the-load-test-summary"></a>Yük Testi Özeti

Yük Testi Özeti bölümlere ayrılmıştır. İlk bölümler özetin en üstünde görünür ve her zaman görünür. Yük testi özetini görüntülediğinizde, aşağıdaki öğeler ilk olarak verilmiştir:

- Test çalıştırması bilgileri

- Genel sonuçlar

- Anahtar Istatistiği: en yavaş 5 sayfa

- Anahtar Istatistiği: en yavaş 5 test

- Anahtar Istatistiği: en yavaş 5 SQL Işlemi

    > [!NOTE]
    > SQL Işlemleri bölümü yalnızca, yük testinde SQL izleme etkinse görüntülenir.

Kapanış bölümleri özetin sonunda görünür ve boş alan kazanmak için daraltılabilirler. Aşağıdaki öğeler yük testi özetinin sonunda görünür:

- Test Sonuçları

- Sayfa sonuçları

- İşlem sonuçları

- Test kaynakları altındaki sistem

- Denetleyici ve aracı kaynakları

- Hatalar

## <a name="test-run-information"></a>Test çalıştırması bilgileri

Test çalıştırması bilgileri bölümü, testin adı, başlangıç ve bitiş zamanları ve testi çalıştıran denetleyici dahil olmak üzere çalıştırma hakkındaki genel bilgileri içerir. Bu bölüm, yük testini çalıştırdığınızda eklediğiniz çalıştırmanın isteğe bağlı açıklamasını da içerir.

## <a name="overall-results"></a>Genel sonuçlar

Genel sonuçlar bölümü, saniye başına istek sayısı, başarısız isteklerin toplam sayısı, ortalama yanıt süresi ve ortalama sayfa süresi dahil olmak üzere testin Özet sonuçlarını içerir.

## <a name="key-statistic-top-5-slowest-pages"></a>Anahtar istatistiği: en yavaş 5 sayfa

En yavaş sayfalar bölümü, yük testinde en yavaş 5 sayfayı içerir. URL ve ortalama sayfa yükleme süresi her sayfa için görüntülenir. Sayfalar azalan sırada listelenir. **Sayfalar** tablosunu açmak için bir sayfanın URL 'sini seçebilir ve Bu sayfa için daha fazla ayrıntı inceleyebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: Web sayfası yanıtını görüntüleme](../test/how-to-view-web-page-response-time-in-a-load-test.md).

**%95 sayfa süresi (sn)** raporunun %95 ' i için bu sürenin saniye cinsinden daha az bir süre içinde tamamlandığını belirten yüzdebirlik değeri.

## <a name="key-statistic-top-5-slowest-tests"></a>Anahtar istatistiği: en yavaş 5 test

En yavaş testler bölümü, yük testinde en yavaş 5 testi içerir. Testin adı ve ortalama test süresi her test için görüntülenir. Testler, azalan sırada listelenir. Test adını seçerek **testler** tablosunu açabilir ve bu test için daha fazla ayrıntı inceleyebilirsiniz. Daha fazla bilgi için bkz. [Tablolar görünümünde Yük testi sonuçlarını ve hatalarını çözümleme](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

**%95 test süresi (sn)** raporunun %95 ' i, testlerin% ' nin bu süreden daha az saniye içinde tamamlandığını belirten yüzdebirlik değeri.

## <a name="key-statistic-top-5-slowest-sql-operations"></a>Anahtar istatistiği: en yavaş 5 SQL işlemi

Yük testinde SQL izleme etkinse, en yavaş sorgular bölümü, yük testinde en yavaş 5 sorguyu içerir. İşlemin adı ve süre her test için görüntülenir. Süre mikrosaniye (SQL Server 2005) veya milisaniyelik (SQL Server 2000 ve önceki sürümler) olarak görüntülenir. Testler süreye göre azalan sırada listelenir. Bir işlemin adını seçerek **SQL izleme** tablosunu açabilir ve bu işlem için daha fazla ayrıntı inceleyebilirsiniz. Daha fazla bilgi için bkz. [SQL izleme verileri tablosu](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-sql-trace-data-table).

## <a name="test-results"></a>Test sonuçları

Test sonuçları bölümü, yük testinde tüm testlerin ve senaryoların bir listesini içerir. Testin adı, senaryo, kaç kez çalıştığı, kaç kez başarısız olduğu ve ortalama test süresi görüntülenir. Test adını seçerek **testler** tablosunu açabilir ve bu test için daha fazla ayrıntı inceleyebilirsiniz. Daha fazla bilgi için bkz. [Tablolar görünümünde Yük testi sonuçlarını ve hatalarını çözümleme](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

> [!NOTE]
> Bölüm başlığının solundaki oku seçerek bu bölümü daraltabilir ve genişletebilirsiniz.

## <a name="page-results"></a>Sayfa sonuçları

Sayfa sonuçları bölümü, yük testindeki tüm Web sayfalarının bir listesini içerir. URL, senaryo, testin adı, ortalama sayfa süresi ve sayı görüntülenir. **Sayfalar** tablosunu açmak için bir sayfanın URL 'sini seçebilir ve Bu sayfa için daha fazla ayrıntı inceleyebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: Web sayfası yanıtını görüntüleme](../test/how-to-view-web-page-response-time-in-a-load-test.md).

> [!NOTE]
> Bölüm başlığının solundaki oku seçerek bu bölümü daraltabilir ve genişletebilirsiniz.

## <a name="transaction-results"></a>İşlem sonuçları

İşlem sonuçları bölümü, yük testindeki tüm işlemlerin bir listesini içerir. İşlemin adı, senaryo, test, yanıt süresi, geçen süre ve sayı görüntülenir. **İşlem tablosunu açmak** ve bu işlem için daha fazla ayrıntı incelemek üzere bir işlem adı seçebilirsiniz. Daha fazla bilgi için bkz. [Tablolar görünümünde Yük testi sonuçlarını ve hatalarını çözümleme](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

> [!NOTE]
> Bölüm başlığının solundaki oku seçerek bu bölümü daraltabilir ve genişletebilirsiniz.

Yüzdelik değerler aşağıdaki işlem bilgilerini raporlar:

- Toplam işlem %90, \<time > saniyeden az bir süre içinde tamamlandı.

- Toplam işlem %95, \<time > saniyeden az bir süre içinde tamamlandı.

## <a name="system-under-test-resources"></a>Test kaynakları altındaki sistem

Test kaynakları altındaki sistem bölümü, yükün oluşturulduğu hedef bilgisayar kümesi olan bilgisayarların bir listesini içerir. Bu, aracı veya denetleyici dışında sayaç kümelerini topladığınız tüm bilgisayarları içerir. Bilgisayar adı,% işlemci zamanı ve kullanılabilir bellek görüntülenir. **Test grafiği altında sistemi** açmak için bir bilgisayar adı seçebilirsiniz ve zaman içinde kaynak kullanımını görebilirsiniz. Daha fazla bilgi için bkz. [Grafik görünümünde Yük testi sonuçlarını çözümleme](../test/analyze-load-test-results-in-the-graphs-view.md).

> [!NOTE]
> Bölüm başlığının solundaki oku seçerek bu bölümü daraltabilir ve genişletebilirsiniz.

## <a name="controller-and-agent-resources"></a>Denetleyici ve aracı kaynakları

Denetleyici ve aracı kaynakları bölümü, testi çalıştırmak için kullanılan bilgisayarların bir listesini içerir. Bilgisayar adı,% işlemci zamanı ve kullanılabilir bellek görüntülenir. **Denetleyici ve aracılar** grafiğini açmak ve zaman içinde kaynak kullanımını görmek için bir bilgisayar adı seçebilirsiniz. Daha fazla bilgi için bkz. [Grafik görünümünde Yük testi sonuçlarını çözümleme](../test/analyze-load-test-results-in-the-graphs-view.md).

> [!NOTE]
> Bölüm başlığının solundaki oku seçerek bu bölümü daraltabilir ve genişletebilirsiniz.

## <a name="errors"></a>Hatalar

Hatalar bölümü, yük testi sırasında oluşan tüm hataların bir listesini içerir. Hatanın türü ve alt türü, sayı ve son ileti görüntülenir. **Hatalar** tablosunu açmak için bir hata seçebilir ve bu hata için daha fazla ayrıntı inceleyebilirsiniz. Daha fazla bilgi için bkz. [Tablolar görünümünde Yük testi sonuçlarını ve hatalarını çözümleme](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

> [!NOTE]
> Bölüm başlığının solundaki oku seçerek bu bölümü daraltabilir ve genişletebilirsiniz.

## <a name="print-a-summary"></a>Özet Yazdır

Özet menüsünde kısayol menüsündeki **Yazdır** ' i seçerek yük testi özetini yazdırabilirsiniz. Özetin kısayol menüsünde **Baskı Önizleme** ' ye tıklayarak önce yazdırmayı önizleyebilirsiniz. Doğrudan Önizleme ekranından da yazdırabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Eşik Kuralı İhlallerini Çözümleme](../test/analyze-threshold-rule-violations-in-load-tests.md)
- [Yük testi sonuçlarını çözümle](../test/analyze-load-test-results-using-the-load-test-analyzer.md)