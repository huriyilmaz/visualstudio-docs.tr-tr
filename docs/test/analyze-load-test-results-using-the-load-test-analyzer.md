---
title: Yük Test Sonuçları çözümleniyor
description: Performans sorunlarını bulmak, hataları belirlemek ve uygulamanızdaki iyileştirmeleri ölçmek için Yük Testi Çözümleyicisi 'ni nasıl kullanacağınızı öğrenin.
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
manager: jillfra
ms.openlocfilehash: 4f33898aa1c3c08179f1438a7c6e6e11a75587bc
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2020
ms.locfileid: "95442488"
---
# <a name="analyze-load-test-results-using-the-load-test-analyzer"></a>Yük Testi Çözümleyicisini kullanarak yük testi sonuçlarını analiz etme

**Yük Testi Çözümleyicisi**'ni kullanırken performans sorunlarını bulun, hataları belirleyin ve uygulamanızdaki iyileştirmeleri ölçün.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Yük testi sonuçlarını şu yollarla çözümleyin:

- Bir yük testini çalışırken izleyin.

- Yük testini tamamladıktan sonra analiz edin.

- Önceki bir yük testinin sonuçlarını görüntüleyin.

Ayrıca, eğilim analizi için iki veya daha fazla raporu, paydaşlarla paylaşmak üzere karşılaştıran raporlar da oluşturabilirsiniz. Bkz. [Test karşılaştırmaları veya eğilim analizi için yük testi sonuçlarını raporlama](../test/compare-load-test-results.md).

Yük testinizi Visual Studio Enterprise veya komut satırından çalıştırdığınız ve yük testinizi tek bir bilgisayarda mı yoksa uzak bir makinede mı çalıştırdığınız, bu görevleri tamamlayabilirsiniz.

## <a name="differences-between-analyzing-a-running-and-a-completed-load-test"></a>Çalışan ve tamamlanmış bir yük testinin çözümlenmesi arasındaki farklar

Bir yük testi çalıştırdığınızda, yük testi **Çözümleyicisi** , yük testinizin adı ve testin başlatıldığı zaman ile birlikte ayrı bir sekmede görüntülenir (örneğin, **LOADTEST1 [12:40 PM]**). Bir yük testi çalıştırıldığında, performans sayacı verileri daha küçük bir kümesi bellekte tutulur. Yük testiniz çalıştırıldığında, bu veri kümesini izleyebilirsiniz. Bir yük testi tamamlandıktan sonra, veritabanındaki tüm verileri analiz edebilirsiniz. Bir yük testi çalıştırıldığında hangi verilerin görüntüleneceği ve bir yük testi tamamlandıktan sonra görebileceğiniz veriler arasındaki farklar vardır. Örneğin, yüzde 90 ve %95 yanıt süresi verileri, yük testi tamamlanana kadar hesaplanmaz. Ayrıca, verileri çözümlemek için kullanılabilen araçların işlevselliğinde bazı farklılıklar oluşur.

Yük testini çalıştırdığınızda iki görünüm bulunur: **grafikler** görünümü ve **Tablolar** görünümü. **Grafikler** görünümü, toplanan performans sayaçlarını grafiketmenize olanak tanır. **Tablolar** görünümü, toplanan testlerin, sayfaların, işlemlerin ve isteklerin her biri hakkında bilgi verir. Ayrıca, hataları listeleyen bir tablo alırsınız.

Varsayılan olarak, yük testi çalıştırması tamamlandığında **Özet** görünümü görüntülenir. Araç çubuğunu kullanarak **Özet**, **grafikler**, **Tablolar** ve **Ayrıntılar** görünümleri arasında geçiş yapabilirsiniz. **Yük Testi Çözümleyicisi** , normal Visual Studio pencere işleme teknikleri kullanılarak yerleştirilebilir veya float olarak ayarlanabilir. Tamamlanan yük testi çalıştırmalarını analiz ettiğinizde, farklı yük testi çalıştırmalarını karşılaştırmak için aynı anda birden çok **Yük testi çözümleyicilerinin** açılmasını sağlayabilirsiniz.

## <a name="tasks"></a>Görevler

|Görevler|İlişkili konular|
|-|-|
|**Yük testinizin sonuçlarına erişme:** Yük Testi Düzenleyicisi bir yük testi çalıştırdığınızda, yük testi sonuçları otomatik olarak açılır ve çalışan yük testi **Yük Testi Çözümleyicisi**'nde görüntülenir.|-   [Nasıl yapılır: analiz için yük testi sonuçlarına erişme](../test/how-to-access-load-test-results-for-analysis.md)|
|**Yük testinize analiz notları ekleyin:** Analizinizi yaparken, yük testinize yorum ekleyebilirsiniz. Yorumlar, yük testi sonucuyla birlikte kalıcı olarak depolanır. Girdiğiniz açıklama Ayrıca, Yük Testi Düzenleyicisi içindeki **Aç ve yönet test sonuçları** iletişim kutusunda yük testiyle ilişkili **Açıklama** sütununda görüntülenir.<br /><br /> Daha fazla bilgi için bkz. [nasıl yapılır: çözümleme için yük testi sonuçlarına erişme](../test/how-to-access-load-test-results-for-analysis.md).<br /><br /> Ayrıca, açıklamalar, yük testi sonuçları için bir Excel raporu oluşturduğunuzda görüntülenir.<br /><br /> Daha fazla bilgi için bkz. [Test karşılaştırmaları veya eğilim analizi için yük testi sonuçlarını raporlama](../test/compare-load-test-results.md).||
|**Yük testinizin sonuçları çözümleniyor:** Yük testi çalıştırma verilerine erişduktan sonra, elde edilen verileri çözümleyebilirsiniz. Sonuçları hızla anlamak için yük testi özetini görüntüleyebilirsiniz. Yük Testi Özeti, önemli sonuçları sıkıştırılmış ve kolay okunabilir biçimde gösterir.<br /><br /> Yük testi özetini yazdırabilirsiniz. Bu, sonuçları paydaşlara iletmenin kullanımını kolaylaştırır.<br /><br /> Sonuçlarda grafik ve tabloları kullanarak yük testi sonuçlarınızın ayrıntılarını çözümleyebilirsiniz. Bunlar arasında **hatalar**, **Sayfalar**, **istekler**, **SQL izleme**, **testler**, **eşikler** ve **işlemler** bulunur.|-   [Yük testi sonuçları özetine genel bakış](../test/load-test-results-summary-overview.md)<br />-   [Nasıl yapılır: Web sayfası yanıtını görüntüleme](../test/how-to-view-web-page-response-time-in-a-load-test.md)<br />-   [Eşik Kuralı İhlallerini Çözümleme](../test/analyze-threshold-rule-violations-in-load-tests.md)<br />-   [Grafik görünümünde Yük testi sonuçlarını çözümleme](../test/analyze-load-test-results-in-the-graphs-view.md)<br />-   [Tablolar görünümünde Yük testi sonuçlarını ve hatalarını çözümleme](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)|
|**Performans sorunlarını yalıtmak için yük testi sonuçlarınızda sanal kullanıcı etkinliğini analiz etme:** Sanal Kullanıcı Etkinlik grafiğini kullanarak bir yük testi sırasında sanal kullanıcıların ne yaptığını görselleştirebilirsiniz. Bu, ani artışları bir CPU veya isteklerin/sn cinsinden yalıtmak ve bu ani artışlar ve bırakılanlar sırasında hangi testlerin veya sayfaların çalıştığını belirlemek için yardımcı olabilir.|-   [Ayrıntılar görünümündeki sanal kullanıcı etkinliğini çözümleme](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)|
