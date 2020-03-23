---
title: 'Nasıl yapılır: Yük Testi Sonuçlarını bir Depoya Aktarma'
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- results, load test
- load test results, importing
- Load Test Results Repository
- load tests, importing results
ms.assetid: a955b3d2-c8ad-40dd-8ea3-9f1a271e1eed
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bbc8c352c7bf3cda0524f07aa82b6ccbe70602b2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589038"
---
# <a name="how-to-import-load-test-results-into-a-repository"></a>Nasıl yapilir: Yük testi sonuçlarını depoya alma

Bir yük testi çalıştırdığınızda, çalışma sırasında toplanan bilgiler Yük Testi Sonuçları Deposu'nda depolanır. Yük Testi Sonuçları Deposu, performans sayacı verileri ve hatalar hakkında bilgi içerir. Daha fazla bilgi için, [Yük Testi Sonuçları Deposu'ndaki yük testi sonuçlarını yönet'e](../test/manage-load-test-results-in-the-load-test-results-repository.md)bakın.

Yük Testi **Sonuçlarını Aç ve Yönet** iletişim kutusunu kullanarak Yük Testi Düzenleyicisi'nden yük testi sonuçlarını yönetebilirsiniz. Yük testi sonuçlarını açabilir, içe aktarabilir, dışa aktarabilir ve kaldırabilirsiniz.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-import-results-into-a-repository"></a>Sonuçları bir depoya almak için

1. Web performansı ve yükleme testi projesinden bir yük testi açın.

2. Katıştırılmış araç çubuğunda **Sonuçları Aç ve Yönet'i**seçin.

     **Yükle Test Sonuçlarını Aç ve Yönet** iletişim kutusu görüntülenir.

3. **Yük testi sonuçlarını bulmak için bir denetleyici adı girin,** bir denetleyici seçin. Yerel olarak depolanan sonuçlara erişmek için ** \<yerel>** seçin.

     Yük testi sonuçları varsa, **Bunlar Yük testi sonuçları** listesinde görünür. Sütunlar **Zaman**, **Süre**, **Kullanıcı**, **Sonuç**, **Test**, ve **Açıklama**. **Test** testin adını içerir ve **Açıklama,** test çalıştırılmadan önce eklenen isteğe bağlı açıklamayı içerir.

4. **Alma'yı**seçin.

     **İçe Aktar Yükü Test Sonuçları** iletişim kutusu görüntülenir.

5. Dosya **adı** kutusuna, arşivlenmiş bir test sonuçları dosyasının adını yazın ve sonra **Aç'ı**seçin.

     \-veya -

     Dosyaya göz atın ve sonra **Aç'ı**seçin.

    > [!NOTE]
    > Bu adımda belirttiğiniz arşivlenmiş bir test sonuçları dosyası, Dışa Aktarma işlemi gerçekleştirerek oluşturulmuş olmalıdır.

     Sonuçlar alınır ve Load **test sonuçları** listesinde görünür.

## <a name="see-also"></a>Ayrıca bkz.

- [Yük Testi Sonuçları Deposu'nda yük testi sonuçlarını yönetme](../test/manage-load-test-results-in-the-load-test-results-repository.md)
- [Yük testi sonuçlarını analiz edin](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Nasıl yapilir: Yük testi sonuçlarını bir depodan dışa aktarma](../test/how-to-export-load-test-results-from-a-repository.md)
