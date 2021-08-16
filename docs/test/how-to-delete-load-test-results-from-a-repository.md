---
title: 'Nasıl yapılır: Bir Depodan Yük Testi Sonuçlarını Silme'
description: Yükü Aç ve Yönet iletişim kutusunu kullanarak Test Sonuçları Yükleme deposundan bilgi Test Sonuçları öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: e5baef422a9dac6ec2eefef3b8e0f7f491a627422c2d1c0e9ba20c606b9e2e4b
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121366686"
---
# <a name="how-to-delete-load-test-results-from-a-repository"></a>Nasıl olur: Bir depodan yük testi sonuçlarını silme

Bir yük testi çalıştırarak çalıştırma sırasında toplanan bilgiler Load Test Sonuçları Repository içinde depolanır. Load Test Sonuçları Deposu, performans sayacı verilerini ve hatalar hakkında bilgi içerir. Daha fazla bilgi için, Load Test Sonuçları Repository 'de [yük testi sonuçlarını yönetme.](../test/manage-load-test-results-in-the-load-test-results-repository.md)

Yük testi sonuçlarını, Yük Yük Testi Düzenleyicisi Aç ve Yönet iletişim **kutusunu kullanarak Test Sonuçları** yönetebilirsiniz. Yük testi sonuçlarını açabilir, içeri aktarın, dışarı aktarın ve kaldırın.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-delete-results-from-a-repository"></a>Bir depodan sonuçları silmek için

1. Web performansı ve yük testi projesinde bir yük testi açın.

2. Ekli araç çubuğunda Sonuçları Aç **ve Yönet'i seçin.**

     Yük **Dengelemeyi Aç ve Test Sonuçları** iletişim kutusu görüntülenir.

3. Yük **testi sonuçlarını bulmak için bir denetleyici adı girin içinde** bir denetleyici seçin. Yerel **\<Local - No controller>** olarak depolanan sonuçlara erişmek için öğesini seçin.

4. Aşağıdaki **yük testinin sonuçlarını göster** altında, sonuçlarını görüntülemek istediğiniz yük testini seçin. Tüm **\<Show results for all tests>** testlerin tüm sonuçlarını görmek için öğesini seçin.

     Yük testi sonuçları varsa, Test sonuçlarını yükle **listesinde** görünürler. Sütunlar **Time,** **Duration**, **User**, **Outcome**, **Test** ve **Description sütunlarıdır.** **Test,** testin adını, **Açıklama** ise test çalıştırılamadan önce eklenen isteğe bağlı açıklamayı içerir. Açıklama **sütunu,** bu test sonucu için Analiz Açıklamalarında **girilen** kısa açıklamaları görüntüler.

5. Test **sonuçlarını yükle listesinden** bir sonuç seçin. Birden fazla sonuç seçmek için **Shift** tuşunu, **Ctrl** tuşunu veya her ikisini birden kullanabilirsiniz.

6. **Kaldır**'ı seçin.

     Sonuçlar depodan kaldırılır.

    > [!NOTE]
    > Sonuçlar **kaldırıldıktan sonra Test Sonuçları** Aç ve Yönet iletişim kutusu açık kalır.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl olur: Bir depodan yük testi sonuçlarını dışarı aktarma](../test/how-to-export-load-test-results-from-a-repository.md)
- [Load Test Sonuçları Repository'de yük testi sonuçlarını yönetme](../test/manage-load-test-results-in-the-load-test-results-repository.md)
- [Yük testi sonuçlarını analiz etme](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Nasıl olur: Yük testi sonuçlarını depoya aktarma](../test/how-to-import-load-test-results-into-a-repository.md)
