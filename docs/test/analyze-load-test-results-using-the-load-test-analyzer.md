---
title: Yük Analizi Test Sonuçları
description: Uygulamanıza yönelik performans sorunlarını bulmak, hataları belirlemek ve geliştirmeleri ölçmek için Yük Testi Çözümleyicisi'nin nasıl kullanılası hakkında bilgi alın.
ms.custom: SEO-VS-2020
ms.date: 10/20/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, test results
- load tests, analyzing test results
- load tests, managing test results
ms.assetid: 8a4ba300-425d-447c-91d9-c53f4345feee
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: 3c32efc335441b57ff23fe55b5619297e50bf700
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122083979"
---
# <a name="analyze-load-test-results-using-the-load-test-analyzer"></a>Yük Testi Çözümleyicisi kullanarak yük testi sonuçlarını analiz etme

Yük Testi Çözümleyicisi'nini kullanarak uygulamanıza performans sorunlarını bulun, hataları belirleyin **ve geliştirmeleri ölçün.**

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Yük testi sonuçlarını şu yollarla analiz etme:

- Bir yük testini, çalışıyorken izleme.

- Tamamlandıktan sonra bir yük testini analiz etme.

- Önceki bir yük testinin sonuçlarını görüntüleme.

Ayrıca, proje katılımcıları ile paylaşmak için eğilim analizi için iki veya daha fazla raporu karşılaştıran raporlar oluşturabilirsiniz. Test [karşılaştırmaları veya eğilim analizi için bkz. Yük testi sonuçlarını raporlama.](../test/compare-load-test-results.md)

Yük testini ister komut Visual Studio Enterprise ister komut satırına bakarak ve yük testini tek bir bilgisayarda veya uzak bir makinede çalıştırarak bu görevleri tamamabilirsiniz.

## <a name="differences-between-analyzing-a-running-and-a-completed-load-test"></a>Çalışan ve tamamlanan yük testini analiz etme arasındaki farklar

Bir yük testi çalıştırarak  Yük Testi Çözümleyicisi, yük testinizin adı ve testin başlat olduğu zaman (örneğin, **LoadTest1 [12:40 PM] )** ile birlikte ayrı bir sekmede görüntülenir. Yük testi çalıştırıldıklarında, daha küçük bir performans sayacı veri kümesi bellekte korunur. Yük testini çalıştırırken bu veri kümelerini izleyebilirsiniz. Yük testi tamamlandıktan sonra veritabanındaki tüm veri kümelerini analiz edersiniz. Yük testi çalıştırlendiğinde hangi verilerin görüntülendiğinde ve yük testi tamamlandıktan sonra hangi verileri göreyebilirsiniz arasında farklar vardır. Örneğin, yük testi tamamlanana kadar yüzde 90 ve yüzde 95 yanıt süresi verileri hesaplanmaz. Bazı farklılıklar, verileri analiz etmek için kullanılabilen araçların işlevselliğinde de ortaya çıkar.

Yük testini çalıştırarak iki görünüm kullanılabilir: **Graflar görünümü** ve **Tablolar** görünümü. **Graflar** görünümü, toplanan performans sayaçlarını grafik olarak görüntülemeye olanak sağlar. Tablolar **görünümü** toplanan testler, sayfalar, işlemler ve istekler hakkında bilgi verir. Ayrıca hataları listeleen bir tablo da alırsınız.

Varsayılan olarak, yük testi çalıştırması tamamlandığında **Özet** görünümü görüntülenir. Araç çubuğunu kullanarak **Özet,** **Graflar,** **Tablolar** ve **Ayrıntılar görünümleri** arasında geçişebilirsiniz. Yük **Testi Çözümleyicisi,** her zamanki pencere işleme teknikleri kullanılarak Visual Studio veya float olarak ayarlanır. Tamamlanan yük testi çalıştırmalarını analiz ederken, farklı yük testi çalıştırmalarını karşılaştırmak için aynı anda birden çok Yük Testi Çözümleyicisi açabilirsiniz. 

## <a name="tasks"></a>Görevler

|Görevler|İlişkili konular|
|-|-|
|**Yük testin sonuçlarına erişme:** Yük testini yük testi Yük Testi Düzenleyicisi yük testi sonuçları otomatik olarak açılır ve çalışan yük testi Yük Testi **Çözümleyicisi'ne görüntülenir.**|-   [Nasıllı: Analiz için yük testi sonuçlarına erişme](../test/how-to-access-load-test-results-for-analysis.md)|
|**Yük teste analiz notları ekleyin:** Analizinizi yürütecekleri zaman yük teste açıklama eklemek için bu açıklamalara da yer vesersiniz. Açıklamalar, yük testi sonucuyla birlikte kalıcı olarak depolanır. Ayrıca, girişte yer alan  Aç ve Yönet iletişim kutusundaki yük testiyle ilişkili Açıklama **sütununda da Test Sonuçları** açıklama Yük Testi Düzenleyicisi.<br /><br /> Daha fazla bilgi için, [bkz. How to: Access load test results for analysis](../test/how-to-access-load-test-results-for-analysis.md).<br /><br /> Buna ek olarak, yük testi sonuçları için bir Excel raporu 70000000000000000000000000000000000000000000000000000<br /><br /> Daha fazla bilgi için [bkz. Test karşılaştırmaları veya eğilim analizi için yük testi sonuçlarını raporlama.](../test/compare-load-test-results.md)||
|**Yük testin sonuçlarını analiz etme:** Yük testi çalıştırma verilerine erişdikten sonra elde edilen verileri analiz edersiniz. Sonuçları hızla anlamak için Yük Testi Özeti'ne bakabilirsiniz. Yük testi özeti, önemli sonuçları sıkıştırılmış ve kolayca okunan bir biçimde gösterir.<br /><br /> Yük testi özetini yazdırabilirsiniz. Bu, sonuçları paydaşlara iletirken kullanımı kolay hale getirir.<br /><br /> Sonuçlardaki grafikleri ve tabloları kullanarak yük testi sonuçlarınıza ilişkin ayrıntıları analiz edin. Bunlara **Hatalar,** **Sayfalar,** **İstekler,** SQL **İzleme,** **Testler,** **Eşikler** ve **İşlemler dahildir.**|-   [Yük testi sonuçları özetine genel bakış](../test/load-test-results-summary-overview.md)<br />-   [Nasıl: Web sayfası yanıtını görüntüleme](../test/how-to-view-web-page-response-time-in-a-load-test.md)<br />-   [Eşik kuralı ihlallerini analiz etme](../test/analyze-threshold-rule-violations-in-load-tests.md)<br />-   [Graflar görünümünde yük testi sonuçlarını analiz etme](../test/analyze-load-test-results-in-the-graphs-view.md)<br />-   [Tablolar görünümünde yük testi sonuçlarını ve hatalarını analiz etme](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)|
|**Performans sorunlarını yalıtmak için yük testi sonuçlarınıza sanal kullanıcı etkinliğini analiz etme:** Yük testi sırasında sanal kullanıcıların neler yaptığını görselleştirmek için Sanal Kullanıcı Etkinlik Grafiği'nin kullanabilirsiniz. Bu, CPU'daki ani artışları yalıtmanıza veya istek/sn'de düşüşleri yalıtmanıza ve bu ani artışlar ve düşüşler sırasında hangi testlerin veya sayfaların çalıştırlır olduğunu belirlemenize yardımcı olabilir.|-   [Ayrıntılar görünümünde sanal kullanıcı etkinliğini analiz etme](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)|
