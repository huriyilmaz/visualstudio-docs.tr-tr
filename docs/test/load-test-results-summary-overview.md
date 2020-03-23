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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7df3324c2182c376cb9547a4192fca3e601b3dd5
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75584497"
---
# <a name="load-test-results-summary-overview"></a>Yük testi sonuçları özetine genel bakış

Bir yük testi çalıştırdıktan sonra, sonuçları hızlı bir şekilde anlamak için yük testi özetini görüntüleyebilirsiniz. Yük testi özeti, kompakt ve okunması kolay bir biçimde anahtar sonuçları sağlar. Yük testi özetini de yazdırabilirsiniz. Bu, sonuçları hissedarlara iletdiğinizde kullanımı kolaylaştırır. Yük testi özeti, daha önce çalıştırıladığınız bir yük testi sonucunu açtığınızda varsayılan görünümdür. Daha fazla bilgi için [bkz: Çözümleme için yük testi sonuçlarına erişin.](../test/how-to-access-load-test-results-for-analysis.md)

![Özet görünümü](../test/media/ltest_summaryview.png)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="the-load-test-summary"></a>Yük testi özeti

Yük testi özeti bölümlere ayrılmıştır. İlk bölümler özetin en üstünde görünür ve her zaman görünür. Yük testi özetini görüntülediğinizde, önce aşağıdaki öğeler vardır:

- Test Çalıştır Bilgileri

- Genel Sonuçlar

- Anahtar İstatistik: En Yavaş 5 Sayfa

- Anahtar İstatistik: En Yavaş 5 Test

- Anahtar İstatistik: En Yavaş 5 SQL İşlemleri

    > [!NOTE]
    > SQL İşlemleri bölümü yalnızca yükleme testinde SQL izleme etkinse görüntülenir.

Kapanış bölümleri özetin sonunda görünür ve yer kazanmak için daraltılabilir. Aşağıdaki öğeler yük testi özetinin sonunda görünür:

- Test Sonuçları

- Sayfa Sonuçları

- İşlem Sonuçları

- Test Kaynakları Altında Sistem

- Denetleyici ve Aracı Kaynakları

- Hatalar

## <a name="test-run-information"></a>Test çalıştırma bilgileri

Test çalıştırma bilgileri bölümü, testin adı, başlangıç ve bitiş saatleri ve testi çalıştıran denetleyici de dahil olmak üzere çalışma hakkında genel bilgiler içerir. Bu bölümde, yük testini çalıştırdığınızda eklediğiniz çalıştırmanın isteğe bağlı açıklamasını da içerir.

## <a name="overall-results"></a>Genel sonuçlar

Genel sonuçlar bölümü, saniyedeki istek sayısı, başarısız isteklerin toplam sayısı, ortalama yanıt süresi ve ortalama sayfa süresi dahil olmak üzere testin özet sonuçlarını içerir.

## <a name="key-statistic-top-5-slowest-pages"></a>Anahtar istatistik: En yavaş 5 sayfa

En yavaş sayfalar bölümü, yükleme testindeki en yavaş 5 sayfayı içerir. URL ve ortalama sayfa yükleme süresi her sayfa için görüntülenir. Sayfalar azalan sırada listelenir. **Sayfalar** tablosunu açmak ve bu sayfayla ilgili daha fazla ayrıntıyı incelemek için sayfanın URL'sini seçebilirsiniz. Daha fazla bilgi için [bkz: Web sayfası yanıtını görüntüle.](../test/how-to-view-web-page-response-time-in-a-load-test.md)

**%95 Sayfa Saati (sn)** için yüzdelik değer, sayfaların %95'inin saniyeler içinde bu saatten daha kısa sürede tamamlandığını bildirir.

## <a name="key-statistic-top-5-slowest-tests"></a>Anahtar istatistik: En yavaş 5 test

En yavaş testler bölümü, yük testindeki en yavaş 5 testi içerir. Testin adı ve ortalama test süresi her test için görüntülenir. Testler azalan sırada listelenir. **Testler** tablosunu açmak ve bu test için daha fazla ayrıntı incelemek için bir testin adını seçebilirsiniz. Daha fazla bilgi için bkz: [Tablolar görünümünde yük testi sonuçlarını ve hatalarını analiz](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)et.

**%95 Test Süresi (sn)** için yüzdelik değer, testlerin %95'inin saniyeler içinde bu saatten daha kısa sürede tamamlandığını bildirir.

## <a name="key-statistic-top-5-slowest-sql-operations"></a>Anahtar istatistik: En yavaş 5 SQL işlemleri

Yükleme testinde SQL izleme etkinleştirilmişse, en yavaş sorgular bölümü yük testinde en yavaş 5 sorguyu içerir. Her test için işlemin adı ve süresi görüntülenir. Süre mikrosaniye (SQL Server 2005) veya milisaniye (SQL Server 2000 ve daha önce) olarak görüntülenir. Testler, süreye göre azalan sırada listelenir. **SQL Trace** tablosunu açmak ve bu işlem için daha fazla ayrıntı incelemek için bir işlemin adını seçebilirsiniz. Daha fazla bilgi için [SQL İzleme veri tablosuna](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-sql-trace-data-table)bakın.

## <a name="test-results"></a>Test sonuçları

Test sonuçları bölümü, yük testindeki tüm testlerin ve senaryoların bir listesini içerir. Testin adı, senaryo, kaç kez çalıştırılamadığı, kaç kez başarısız olduğu ve ortalama test süresi görüntülenir. **Testler** tablosunu açmak ve bu test için daha fazla ayrıntı incelemek için bir testin adını seçebilirsiniz. Daha fazla bilgi için bkz: [Tablolar görünümünde yük testi sonuçlarını ve hatalarını analiz](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)et.

> [!NOTE]
> Bölüm başlığının solundaki oku seçerek bu bölümü daraltabilir ve genişletebilirsiniz.

## <a name="page-results"></a>Sayfa sonuçları

Sayfa sonuçları bölümü, yükleme testindeki tüm web sayfalarının listesini içerir. URL, senaryo, testin adı, ortalama sayfa süresi ve sayım görüntülenir. **Sayfalar** tablosunu açmak ve bu sayfayla ilgili daha fazla ayrıntıyı incelemek için sayfanın URL'sini seçebilirsiniz. Daha fazla bilgi için [bkz: Web sayfası yanıtını görüntüle.](../test/how-to-view-web-page-response-time-in-a-load-test.md)

> [!NOTE]
> Bölüm başlığının solundaki oku seçerek bu bölümü daraltabilir ve genişletebilirsiniz.

## <a name="transaction-results"></a>İşlem sonuçları

Hareket sonuçları bölümü, yük testindeki tüm hareketlerin listesini içerir. Hareketin adı, senaryo, test, yanıt süresi, geçen süre ve sayım görüntülenir. **Hareketler** tablosunu açmak ve bu hareket le ilgili daha fazla ayrıntıyı incelemek için bir hareketin adını seçebilirsiniz. Daha fazla bilgi için bkz: [Tablolar görünümünde yük testi sonuçlarını ve hatalarını analiz](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)et.

> [!NOTE]
> Bölüm başlığının solundaki oku seçerek bu bölümü daraltabilir ve genişletebilirsiniz.

Yüzdelik değerler aşağıdaki işlem bilgilerini bildirir:

- Toplam işlemlerin %90'ı> \<saniyeden kısa sürede tamamlandı.

- Toplam işlemlerin %95'i> \<saniyeden kısa sürede tamamlandı.

## <a name="system-under-test-resources"></a>Test kaynakları altında sistem

Test kaynakları bölümünün altındaki sistem, yük oluşturulmakta olan hedef bilgisayarlar kümesi olan bilgisayarların listesini içerir. Bu, Aracı veya Denetleyici dışında sayaç kümeleri topladığınız tüm bilgisayarları içerir. Bilgisayar adı, % işlemci süresi ve kullanılabilir bellek görüntülenir. Test grafiği **altında Sistemi** açmak ve zaman içinde kaynak kullanımını görmek için bir bilgisayar adı seçebilirsiniz. Daha fazla bilgi için bkz: [Grafikler görünümünde yük testi sonuçlarını analiz](../test/analyze-load-test-results-in-the-graphs-view.md)et.

> [!NOTE]
> Bölüm başlığının solundaki oku seçerek bu bölümü daraltabilir ve genişletebilirsiniz.

## <a name="controller-and-agent-resources"></a>Denetleyici ve aracı kaynakları

Denetleyici ve aracı kaynakları bölümü, testi çalıştırmak için kullanılan bilgisayarların listesini içerir. Bilgisayar adı, % işlemci süresi ve kullanılabilir bellek görüntülenir. **Denetleyici ve Aracılar** grafiğini açmak ve zaman içinde kaynak kullanımını görmek için bir bilgisayar adı seçebilirsiniz. Daha fazla bilgi için bkz: [Grafikler görünümünde yük testi sonuçlarını analiz](../test/analyze-load-test-results-in-the-graphs-view.md)et.

> [!NOTE]
> Bölüm başlığının solundaki oku seçerek bu bölümü daraltabilir ve genişletebilirsiniz.

## <a name="errors"></a>Hatalar

Hatalar bölümü, yük testi sırasında oluşan tüm hataların bir listesini içerir. Hatanın türü ve alt türü, sayısı ve son ileti görüntülenir. **Hatalar** tablosunu açmak için bir hata seçebilir ve bu hata yla ilgili daha fazla ayrıntıyı inceleyebilirsiniz. Daha fazla bilgi için bkz: [Tablolar görünümünde yük testi sonuçlarını ve hatalarını analiz](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)et.

> [!NOTE]
> Bölüm başlığının solundaki oku seçerek bu bölümü daraltabilir ve genişletebilirsiniz.

## <a name="print-a-summary"></a>Özet yazdırma

Özetteki kısayol menüsünde **Yazdır'ı** seçerek yük testi özetini yazdırabilirsiniz. Özetteki kısayol menüsünde **Yazdır Önizleme'yi** seçerek önce baskıyı önizleyebilirsiniz. Doğrudan önizleme ekranından da yazdırabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Eşik kuralı ihlallerini analiz edin](../test/analyze-threshold-rule-violations-in-load-tests.md)
- [Yük testi sonuçlarını analiz edin](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
