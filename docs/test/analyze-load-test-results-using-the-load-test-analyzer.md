---
title: Yük Testi Sonuçlarının Analizi
ms.date: 10/20/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, test results
- load tests, analyzing test results
- load tests, managing test results
ms.assetid: 8a4ba300-425d-447c-91d9-c53f4345feee
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9300dd1ebeaee9d87d2527dbc49fa66e319970c1
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591248"
---
# <a name="analyze-load-test-results-using-the-load-test-analyzer"></a>Yük Testi Çözümleyicisini kullanarak yük testi sonuçlarını analiz edin

**Yük Testi Çözümleyicisini**kullandığınızda darboğazları bulun, hataları belirleyin ve uygulamanızdaki gelişmeleri ölçün.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Yük testi sonuçlarını şu şekilde analiz edin:

- Çalışırken bir yük testini izleyin.

- Bir yük testini tamamlandıktan sonra analiz edin.

- Önceki bir yükleme testinin sonuçlarını görüntüleyin.

Ayrıca, eğilim çözümlemesi için iki veya daha fazla raporu hissedarlarla paylaşmak üzere karşılaştıran raporlar da oluşturabilirsiniz. Bkz. [Test karşılaştırmaları veya eğilim analizi için yük testleri sonuçlarını raporlama.](../test/compare-load-test-results.md)

Bu görevleri, visual studio enterprise'dan veya komut satırından çalıştırıp çalıştırmadığınızı ve yük testinizi tek bir bilgisayarda veya uzak bir makinede çalıştırıp çalıştırmadığınızı tamamlayabilirsiniz.

## <a name="differences-between-analyzing-a-running-and-a-completed-load-test"></a>Çalışan ve tamamlanmış yük testini çözümleme arasındaki farklar

Bir yük testi çalıştırdığınızda, **Yük Testi Çözümleyicisi,** yük testinin adı ve testin başlatıldık zamanıyla birlikte ayrı bir sekmede görüntülenir (örneğin, **LoadTest1 [12:40 PM]**). Bir yük testi çalıştığında, performans sayacı verilerinin daha küçük bir kümesi bellekte tutulur. Yük testiniz çalıştığında bu veri kümesini izleyebilirsiniz. Bir yük testi tamamlandıktan sonra, veritabanından tam veri kümesini çözümleyebilirsiniz. Bir yük testi çalıştığında hangi verilerin görüntülendiği ve yük testi tamamlandıktan sonra görebileceğiniz verilerde farklılıklar vardır. Örneğin, yük testi tamamlanana kadar yüzde 90 ve yüzde 95 yanıt süresi verileri hesaplanmaz. Verileri çözümlemek için kullanılabilen araçların işlevselliğinde de bazı farklılıklar oluşur.

Yük testini çalıştırdığınızda, iki görünüm kullanılabilir: **Grafikler** görünümü ve **Tablolar** görünümü. **Grafikler** görünümü, toplanan performans sayaçlarını grafikle yapmanızı sağlar. **Tablolar** görünümü, toplanan testlerin, sayfaların, hareketlerin ve isteklerin her biri hakkında bilgi verir. Ayrıca hataları listeleyen bir tablo alırsınız.

Varsayılan olarak, yük testi çalışması tamamlandığında **Özet** görünümü görüntülenir. Araç çubuğunu kullanarak **Özet,** Grafikler, **Tablolar**ve **Ayrıntılar** **görünümleri**arasında geçiş yapabilirsiniz. **Yük Testi Çözümleyicisi,** her zamanki Visual Studio pencere işleme tekniklerini kullanarak sabitlenebilir veya yüzdürmek üzere ayarlanabilir. Tamamlanan yük testi çalıştırmalarını analiz ettiğinizde, farklı yük testi çalıştırmalarını karşılaştırmak için aynı anda birden çok **Yük Testi Çözümleyicisi** açılabilir.

## <a name="tasks"></a>Görevler

|Görevler|İlişkili konular|
|-|-|
|**Yük testinizin sonuçlarına erişim:** Yük Testi Düzenleyicisi'nden bir yük testi çalıştırdığınızda, yük testi sonuçları otomatik olarak açılır ve çalışan yük testi **Yük Testi Çözümleyicisi'nde**görüntülenir.|-   [Nasıl yapılı: Analiz için yük testi sonuçlarına erişin](../test/how-to-access-load-test-results-for-analysis.md)|
|**Yük testinize analiz notları ekleyin:** Analizinizi yaparken yükleme testinize yorum ekleyebilirsiniz. Açıklamalar, yük testi sonucuyla birlikte kalıcı olarak depolanır. Girdiğiniz açıklama, Yükle Test Düzenleyicisi'ndeki Test Sonuçlarını **Aç ve Yönet** iletişim kutusunda ki yük testiyle ilişkili **Açıklama** sütununda da görüntülenir.<br /><br /> Daha fazla bilgi için [bkz: Çözümleme için yük testi sonuçlarına erişin.](../test/how-to-access-load-test-results-for-analysis.md)<br /><br /> Ayrıca, yük testi sonuçları için bir Excel raporu oluşturduğunuzda açıklamalar görüntülenir.<br /><br /> Daha fazla bilgi için, [test karşılaştırmaları veya eğilim çözümlemesi için yük testleri sonuçlarını raporlama'ya](../test/compare-load-test-results.md)bakın.||
|**Yük testinizin sonuçlarını analiz etmek:** Yük testi çalıştırma verilerine eriştinkten sonra, elde edilen verileri çözümleyebilirsiniz. Sonuçları hızlı bir şekilde anlamak için Yük Testi Özeti'ni görüntüleyebilirsiniz. Yük testi özeti, anahtar sonuçlarını kompakt ve kolay okunabilmektedir.<br /><br /> Yük testi özetini yazdırabilirsiniz. Bu, sonuçları hissedarlara iletdiğinizde kullanımı kolaylaştırır.<br /><br /> Sonuçlardaki grafikleri ve tabloları kullanarak yük testi sonuçlarınızın ayrıntılarını analiz edebilirsiniz. Bunlar **Hatalar,** **Sayfalar,** **İstekler,** **SQL İzleme,** **Testler,** **Eşikler**ve **Hareketler**içerir.|-   [Yük testi sonuçları özetine genel bakış](../test/load-test-results-summary-overview.md)<br />-   [Nasıl yapılır: Web sayfası yanıtını görüntüleme](../test/how-to-view-web-page-response-time-in-a-load-test.md)<br />-   [Eşik kural ihlallerini çözümleme](../test/analyze-threshold-rule-violations-in-load-tests.md)<br />-   [Grafikler görünümünde yük testi sonuçlarını analiz edin](../test/analyze-load-test-results-in-the-graphs-view.md)<br />-   [Tablolar görünümünde yük testi sonuçlarını ve hatalarını analiz etme](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)|
|**Performans sorunlarını yalıtmak için yük testi sonuçlarınızdaki sanal kullanıcı etkinliğini çözümleme:** Sanal kullanıcıların yükleme testi sırasında ne yaptığını görselleştirmek için Sanal Kullanıcı Etkinlik Grafiği'ni kullanabilirsiniz. Bu, cpu'daki ani artışları yalıtmanıza veya istek/sn'deki düşüşleri yalıtmanıza ve bu ani artışlar ve düşmeler sırasında hangi testlerin veya sayfaların çalıştığını belirlemenize yardımcı olabilir.|-   [Ayrıntılar görünümünde sanal kullanıcı etkinliğini analiz etme](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)|
