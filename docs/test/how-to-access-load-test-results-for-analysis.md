---
title: Yük testi sonuçlarını analiz edin
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- results, load test
- load test results, accessing
- Load Test Viewer
- load tests, accessing
- load tests, analyzing
- load tests, results
- Load Test Viewer, viewing
ms.assetid: b0a3e694-2894-479b-b270-7e61e9fafacd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b6a5da728e24d5d7fdbeccd1e28aa2742e04bf48
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596469"
---
# <a name="how-to-access-load-test-results-for-analysis"></a>Nasıl yapılı: Analiz için yük testi sonuçlarına erişin

Yük Testi Düzenleyicisi'nden bir yük testi çalıştırdığınızda, yük testi sonuçları otomatik olarak açılır ve çalışan yük testi **Yük Testi Çözümleyicisi'nde**görüntülenir. Komut satırından bir yük testi çalıştırdığınızda, yük testi sonuçlarına el ile erişmeniz gerekir.

Tamamlanan yük testi için yük testi sonucu, performans sayacı örneklerini ve test altındaki bilgisayarlardan periyodik olarak toplanan hata bilgilerini içerir. Bir yük testi çalışması boyunca çok sayıda performans sayacı örneği toplanabilir. Toplanan performans verilerinin miktarı, test çalışmasının uzunluğuna, örnekleme aralığına, test altındaki bilgisayar sayısına, toplanan sayaç sayısına, yapılandırılan veri toplayıcılarına ve günlük düzeylerine bağlıdır. Büyük bir yük testi için, toplanan performans verilerinin miktarı kolayca birkaç gigabayt olabilir. Daha fazla bilgi için test [denetleyicileri ve test aracıları'na](configure-test-agents-and-controllers-for-load-tests.md)bakın.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-access-a-load-test-result"></a>Yük testi sonucuna erişmek için

1. Web performansı ve yükleme testi projesinden bir yük testi açın.

2. Load Test Düzenleyicisi'nin araç çubuğunda **Sonuçları Aç ve Yönet** düğmesini seçin.

     **Sonuçları Aç ve Yönet** iletişim kutusu görüntülenir.

3. **Yük testi sonuçlarını bulmak için bir denetleyici adı girin,** bir denetleyici seçin. ** \<Yerel>** seçin - Yerel olarak depolanan sonuçlara erişmek için denetleyici yok.

4. **Aşağıdaki yükleme testinin sonuçlarını**göster'de, sonuçlarını görüntülemek istediğiniz yük testini seçin. Tüm testlerin tüm sonuçlarını görmek ** \<>tüm testlerin sonuçlarını göster'i** seçin.

     Yük testi sonuçları varsa, **Bunlar Yük testi sonuçları** listesinde görünür. Sütunlar **Zaman**, **Süre**, **Kullanıcı**, **Sonuç**, **Test**, ve **Açıklama**. **Test** testin adını içerir ve **Açıklama,** test çalıştırılmadan önce eklenen isteğe bağlı açıklamayı içerir.

    > [!NOTE]
    > Sonuçlar listenin en üstündeki en son sonuçlarla birlikte görünür.

5. Load **test sonuçları** listesinde, çözümlemek istediğiniz yük testi sonuçlarını seçin ve **Aç'ı**seçin.

6. **Yük Testi Çözümleyicisi** görüntülenir. Seçili yük testi sonucu Özet görünümünde görüntülenir. Daha fazla bilgi için bkz: [Yükle test sonuçları özeti özetine genel bakış.](../test/load-test-results-summary-overview.md)

     Yük testi sonuçlarını **alma,** dışa aktarma ve kaldırma gibi Sonuçları Aç ve Yönet iletişim kutusunda yük testi sonuçlarının diğer yönlerini yönetebilirsiniz. Daha fazla bilgi için bkz: [Yük testi sonuçları deposundaki yük testi sonuçlarını yönet.](../test/manage-load-test-results-in-the-load-test-results-repository.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi sonuçlarını analiz edin](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
