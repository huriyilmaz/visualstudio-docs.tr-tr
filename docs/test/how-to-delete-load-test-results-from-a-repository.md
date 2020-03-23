---
title: 'Nasıl yapılır: Bir Depodan Yük Testi Sonuçlarını Silme'
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- results, load test
- load tests, deleting results
- load test results, removing
- Load Test Results Repository
- load tests, removing results
- load test results, deleting
ms.assetid: c2afe36b-d061-4f0e-9580-c18569ec08f9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 26dc9750a2bf2eaf5d0ee5dd3d08485c458bb74a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589064"
---
# <a name="how-to-delete-load-test-results-from-a-repository"></a>Nasıl yapılı: Yük testi sonuçlarını bir depodan silme

Bir yük testi çalıştırdığınızda, çalışma sırasında toplanan bilgiler Yük Testi Sonuçları Deposu'nda depolanır. Yük Testi Sonuçları Deposu, performans sayacı verileri ve hatalar hakkında bilgi içerir. Daha fazla bilgi için, [Yük Testi Sonuçları Deposu'ndaki yük testi sonuçlarını yönet'e](../test/manage-load-test-results-in-the-load-test-results-repository.md)bakın.

Yük Testi **Sonuçlarını Aç ve Yönet** iletişim kutusunu kullanarak Yük Testi Düzenleyicisi'nden yük testi sonuçlarını yönetebilirsiniz. Yük testi sonuçlarını açabilir, içe aktarabilir, dışa aktarabilir ve kaldırabilirsiniz.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-delete-results-from-a-repository"></a>Bir depodan sonuçları silmek için

1. Web performansı ve yükleme testi projesinden bir yük testi açın.

2. Katıştırılmış araç çubuğunda **Sonuçları Aç ve Yönet'i**seçin.

     **Yükle Test Sonuçlarını Aç ve Yönet** iletişim kutusu görüntülenir.

3. **Yük testi sonuçlarını bulmak için bir denetleyici adı girin,** bir denetleyici seçin. Yerel olarak depolanan sonuçlara erişmek için ** \<Yerel ->denetleyici yok'u** seçin.

4. **Aşağıdaki yükleme testinin sonuçlarını**göster'de, sonuçlarını görüntülemek istediğiniz yük testini seçin. Tüm testlerin tüm sonuçlarını görmek ** \<>tüm testlerin sonuçlarını göster'i** seçin.

     Yük testi sonuçları varsa, Yük **testi sonuçları** listesinde görünürler. Sütunlar **Zaman**, **Süre**, **Kullanıcı**, **Sonuç**, **Test**, ve **Açıklama**. **Test** testin adını içerir ve **Açıklama,** test çalıştırılmadan önce eklenen isteğe bağlı açıklamayı içerir. **Açıklama** sütunu, bu test sonucu için **Çözümleme Açıklamaları'na** girilen kısa açıklamaları görüntüler.

5. Load **test sonuçları** listesinde bir sonuç seçin. Birden fazla sonuç seçmek için **Shift** tuşunu, **Ctrl** tuşunu veya her ikisini de kullanabilirsiniz.

6. **Kaldır**'ı seçin.

     Sonuçlar depodan kaldırılır.

    > [!NOTE]
    > **Yükle Test Sonuçlarını Aç ve Yönet** iletişim kutusu, sonuçlar kaldırıldıktan sonra açık kalır.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapilir: Yük testi sonuçlarını bir depodan dışa aktarma](../test/how-to-export-load-test-results-from-a-repository.md)
- [Yük Testi Sonuçları Deposu'nda yük testi sonuçlarını yönetme](../test/manage-load-test-results-in-the-load-test-results-repository.md)
- [Yük testi sonuçlarını analiz edin](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Nasıl yapilir: Yük testi sonuçlarını depoya alma](../test/how-to-import-load-test-results-into-a-repository.md)
