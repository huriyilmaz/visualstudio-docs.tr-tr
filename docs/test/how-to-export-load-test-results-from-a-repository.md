---
title: İhracat Yükü Test Sonuçları
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- results, load test
- load tests, exporting results
- Load Test Results Repository
- load test results, exporting
ms.assetid: 716c2af5-8737-4d31-956f-a0273f7c5c0c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3f72dbd687bc9177cd4cfd36416acb23445d30c8
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589051"
---
# <a name="how-to-export-load-test-results-from-a-repository"></a>Nasıl yapilir: Yük testi sonuçlarını bir depodan dışa aktarma

Bir yük testi çalıştırdığınızda, çalışma sırasında toplanan bilgiler Yük Testi Sonuçları Deposu'nda depolanır. Yük Testi Sonuçları Deposu, performans sayacı verileri ve hatalar hakkında bilgi içerir. Daha fazla bilgi için, [Yük Testi Sonuçları Deposu'ndaki yük testi sonuçlarını yönet'e](../test/manage-load-test-results-in-the-load-test-results-repository.md)bakın.

Yük Testi **Sonuçlarını Aç ve Yönet** iletişim kutusunu kullanarak Yük Testi Düzenleyicisi'nden yük testi sonuçlarını yönetebilirsiniz. Yük testi sonuçlarını açabilir, içe aktarabilir, dışa aktarabilir ve kaldırabilirsiniz.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-export-results-from-a-repository"></a>Bir depodan sonuç aktarmak için

1. Web performansı ve yükleme testi projesinden bir yük testi açın.

2. Katıştırılmış araç çubuğunda **Sonuçları Aç ve Yönet'i**seçin.

     **Yükle Test Sonuçlarını Aç ve Yönet** iletişim kutusu görüntülenir.

3. **Yük testi sonuçlarını bulmak için bir denetleyici adı girin,** bir denetleyici seçin. Yerel olarak depolanan sonuçlara erişmek için ** \<Yerel - Denetimsiz>'ı** seçin.

4. **Aşağıdaki yükleme testinin sonuçlarını**göster'de, sonuçlarını görüntülemek istediğiniz yük testini seçin. Tüm testlerin tüm sonuçlarını görmek ** \<>tüm testlerin sonuçlarını göster'i** seçin.

     Yük testi sonuçları varsa, Yük **testi sonuçları** listesinde görünürler. Sütunlar **Zaman**, **Süre**, **Kullanıcı**, **Sonuç**, **Test**, ve **Açıklama**. **Test** testin adını içerir ve **Açıklama,** test çalıştırılmadan önce eklenen isteğe bağlı açıklamayı içerir. **Açıklama** sütunu, bu test sonucu için **Çözümleme Açıklamaları'na** girilen kısa açıklamaları görüntüler.

5. Load **test sonuçları** listesinde bir sonuç seçin. Birden fazla sonuç seçmek ve bunları tek bir dosyaya aktarmak için **Shift** tuşunu, **Ctrl** tuşunu veya her ikisini de kullanabilirsiniz.

6. **Dışa Aktarma'yı**seçin.

     **Dışa Aktarma Yük Testi Sonuçları** iletişim kutusu görüntülenir.

7. Dosya **adı** kutusuna, bir ad yazın ve sonra **Kaydet'i**seçin.

     Sonuçlar bir arşiv dosyasına dışa aktarılır.

    > [!NOTE]
    > **Yükle Test Sonuçlarını Aç ve Yönet** iletişim kutusu, sonuçlar göründükten sonra açık kalır.

## <a name="see-also"></a>Ayrıca bkz.

- [Yük Testi Sonuçları Deposu'nda yük testi sonuçlarını yönetme](../test/manage-load-test-results-in-the-load-test-results-repository.md)
- [Nasıl yapılı: Yük testi sonuçlarını bir depodan silme](../test/how-to-delete-load-test-results-from-a-repository.md)
- [Yük testi sonuçlarını analiz edin](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Nasıl yapilir: Yük testi sonuçlarını depoya alma](../test/how-to-import-load-test-results-into-a-repository.md)
