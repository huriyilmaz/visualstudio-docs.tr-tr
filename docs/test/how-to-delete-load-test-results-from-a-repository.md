---
title: 'Nasıl yapılır: Bir Depodan Yük Testi Sonuçlarını Silme'
ms.date: 10/19/2016
ms.topic: how-to
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
ms.openlocfilehash: dd196076fb769f80c36ab8630eebf1e8a0f8b234
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85287785"
---
# <a name="how-to-delete-load-test-results-from-a-repository"></a>Nasıl yapılır: bir depodan yük testi sonuçlarını silme

Bir yük testi çalıştırdığınızda, çalıştırma sırasında toplanan bilgiler Load Test Sonuçları deposunda depolanır. Load Test Sonuçları Deposu, performans sayacı verilerini ve hatalar hakkındaki bilgileri içerir. Daha fazla bilgi için bkz. [yük test sonuçları deposundaki yük testi sonuçlarını yönetme](../test/manage-load-test-results-in-the-load-test-results-repository.md).

Yük testi sonuçlarını, **yük test sonuçları aç ve Yönet** iletişim kutusunu kullanarak Yük Testi Düzenleyicisi yönetebilirsiniz. Yük testi sonuçlarını açabilir, içeri aktarabilir, dışarı aktarabilir ve kaldırabilirsiniz.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-delete-results-from-a-repository"></a>Bir depodan sonuçları silmek için

1. Bir Web performans ve yük testi projesinden bir yük testi açın.

2. Katıştırılmış araç çubuğunda, **sonuçları aç ve Yönet**' i seçin.

     **Yük test sonuçları aç ve Yönet** iletişim kutusu görüntülenir.

3. **Yük testi sonuçlarını bulmak için bir denetleyici adı girin**' de bir denetleyici seçin. **\<Local - No controller>** Yerel olarak depolanan sonuçlara erişmek için seçin.

4. **Aşağıdaki yük testi için sonuçları göster**bölümünde, sonuçlarını görüntülemek istediğiniz yük testini seçin. **\<Show results for all tests>** Tüm testlerin tüm sonuçlarını görmek için seçin.

     Yük testi sonuçları kullanılabiliyorsa, bunlar **Yük testi sonuçları** listesinde görünürler. Sütunlar **saat**, **süre**, **Kullanıcı**, **sonuç**, **Test**ve **Açıklama**. **Test, testin adını içerir ve** **Açıklama** , test çalıştırılmadan önce eklenen isteğe bağlı açıklamayı içerir. **Açıklama** sütunu, bu test sonucu Için **analiz açıklamalarında** girilen kısa açıklamaları görüntüler.

5. **Yük testi sonuçları** listesinde bir sonuç seçin. Birden fazla sonuç seçmek için **SHIFT** tuşunu, **CTRL** tuşunu veya her ikisini de kullanabilirsiniz.

6. **Kaldır**'ı seçin.

     Sonuçlar depodan kaldırılır.

    > [!NOTE]
    > **Yük test sonuçları aç ve Yönet** iletişim kutusu, sonuçlar kaldırıldıktan sonra açık kalır.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: bir depodan yük testi sonuçlarını dışarı aktarma](../test/how-to-export-load-test-results-from-a-repository.md)
- [Yük Test Sonuçları deposundaki yük testi sonuçlarını yönetme](../test/manage-load-test-results-in-the-load-test-results-repository.md)
- [Yük testi sonuçlarını çözümle](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Nasıl yapılır: yük testi sonuçlarını depoya aktarma](../test/how-to-import-load-test-results-into-a-repository.md)
