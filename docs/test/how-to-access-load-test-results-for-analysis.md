---
title: Yük testi sonuçlarını çözümle
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6be8649ab611a44cb9d2791ae1f4a0e61e930d5b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72664890"
---
# <a name="how-to-access-load-test-results-for-analysis"></a>Nasıl yapılır: analiz için yük testi sonuçlarına erişme

Yük Testi Düzenleyicisi bir yük testi çalıştırdığınızda, yük testi sonuçları otomatik olarak açılır ve çalışan yük testi **Yük Testi Çözümleyicisi**'nde görüntülenir. Komut satırından bir yük testi çalıştırdığınızda, yük testi sonuçlarına el ile erişmeniz gerekir.

Tamamlanan yük testinin yük testi sonucu, bilgisayarlardan düzenli olarak toplanan performans sayacı örneklerini ve hata bilgilerini içerir. Yük testi çalışması sırasında çok sayıda performans sayacı örneği toplanabilir. Toplanan performans verisi miktarı, Test çalıştırmasının uzunluğuna, örnekleme aralığına, test edilen bilgisayar sayısına, toplanan sayaç sayısına, yapılandırılan veri toplayıcılarına ve günlük düzeylerine bağlıdır. Büyük bir yük testi için toplanan performans verisi miktarı kolayca birkaç gigabayt olabilir. Daha fazla bilgi için bkz. [Test denetleyicileri ve test aracıları](configure-test-agents-and-controllers-for-load-tests.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-access-a-load-test-result"></a>Yük testi sonucuna erişmek için

1. Bir Web performans ve yük testi projesinden bir yük testi açın.

2. Yük Testi Düzenleyicisi araç çubuğunda **sonuçları aç ve Yönet** düğmesini seçin.

     **Sonuçları aç ve Yönet** iletişim kutusu görünür.

3. **Yük testi sonuçlarını bulmak için bir denetleyici adı girin**' de bir denetleyici seçin. **@No__t_1local >-** yerel olarak depolanan sonuçlara erişmek Için denetleyici yok ' u seçin.

4. **Aşağıdaki yük testi için sonuçları göster**bölümünde, sonuçlarını görüntülemek istediğiniz yük testini seçin. Tüm testlerin tüm sonuçlarını görmek **> Tüm testler için \<Show sonuçları** ' nı seçin.

     Yük testi sonuçları varsa, bunlar **Yük testi sonuçları** listesinde görünürler. Sütunlar **saat**, **süre**, **Kullanıcı**, **sonuç**, **Test**ve **Açıklama**. **Test, testin adını içerir ve** **Açıklama** , test çalıştırılmadan önce eklenen isteğe bağlı açıklamayı içerir.

    > [!NOTE]
    > Sonuçlar listenin en son sonuçlarıyla birlikte görüntülenir.

5. **Yük testi sonuçları** listesinde, analiz etmek istediğiniz yük testi sonuçlarını seçin ve **Aç**' ı seçin.

6. **Yük Testi Çözümleyicisi** görüntülenir. Seçili yük testi sonucu Özet görünümünde görüntülenir. Daha fazla bilgi için bkz. [Yük testi sonuçları özetine genel bakış](../test/load-test-results-summary-overview.md).

     Yük testi sonuçlarını içeri aktarma, dışarı aktarma ve kaldırma dahil olmak üzere **sonuçları aç ve Yönet** iletişim kutusunda yük testi sonuçlarının diğer yönlerini yönetebilirsiniz. Daha fazla bilgi için bkz. yük testi sonuçları [deposundaki yük testi sonuçlarını yönetme](../test/manage-load-test-results-in-the-load-test-results-repository.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi sonuçlarını çözümle](../test/analyze-load-test-results-using-the-load-test-analyzer.md)