---
title: 'Nasıl yapılır: Yük Testi Sonuçlarını bir Depoya Aktarma'
description: Yükü Aç ve Yönet iletişim kutusunu kullanarak Test Sonuçları Yükleme deposuna bilgi Test Sonuçları öğrenin.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- results, load test
- load test results, importing
- Load Test Results Repository
- load tests, importing results
ms.assetid: a955b3d2-c8ad-40dd-8ea3-9f1a271e1eed
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: 20006867b3c045948395655e6546a68e65c1545c7a3269def066246a5a3e6f5b
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121409156"
---
# <a name="how-to-import-load-test-results-into-a-repository"></a>Nasıl olur: Yük testi sonuçlarını depoya aktarma

Bir yük testi çalıştırarak çalıştırma sırasında toplanan bilgiler Load Test Sonuçları Depoda depolanır. Load Test Sonuçları Deposu, performans sayacı verilerini ve hatalar hakkında bilgi içerir. Daha fazla bilgi için, Load Test Sonuçları Repository 'de [yük testi sonuçlarını yönetme.](../test/manage-load-test-results-in-the-load-test-results-repository.md)

Yük testi sonuçlarını, Yük Yük Testi Düzenleyicisi Aç ve Yönet iletişim **kutusunu kullanarak Test Sonuçları** yönetebilirsiniz. Yük testi sonuçlarını açabilir, içeri aktarın, dışarı aktarın ve kaldırın.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-import-results-into-a-repository"></a>Sonuçları depoya içeri aktarma

1. Web performansı ve yük testi projesinde bir yük testi açın.

2. Ekli araç çubuğunda Sonuçları Aç **ve Yönet'i seçin.**

     Yük **Dengelemeyi Aç ve Test Sonuçları** iletişim kutusu görüntülenir.

3. Yük **testi sonuçlarını bulmak için bir denetleyici adı girin içinde** bir denetleyici seçin. Yerel **\<local>** olarak depolanan sonuçlara erişmek için öğesini seçin.

     Kullanılabilir yük testi sonuçları varsa, bunlar Test **sonuçlarını yükle listesinde** görünür. Sütunlar **Time,** **Duration**, **User**, **Outcome**, **Test** ve **Description sütunlarıdır.** **Test,** testin adını, **Açıklama** ise test çalıştırılamadan önce eklenen isteğe bağlı açıklamayı içerir.

4. İçeri **Aktar'ı seçin.**

     Yükü **İçeri Aktar iletişim Test Sonuçları** kutusu görüntülenir.

5. Dosya **adı kutusuna** arşivlenmiş test sonuçları dosyasının adını yazın ve aç'ı **seçin.**

     \- veya -

     Dosyaya göz atarak Aç'ı **seçin.**

    > [!NOTE]
    > Dışarı Aktarma işlemi gerçekleştirerek bu adımda belirttiğiniz arşivlenmiş bir test sonuçları dosyası oluşturulmuş olması gerekir.

     Sonuçlar içe aktarılır ve Yük testi **sonuçları listesinde** görüntülenir.

## <a name="see-also"></a>Ayrıca bkz.

- [Load Test Sonuçları Repository'de yük testi sonuçlarını yönetme](../test/manage-load-test-results-in-the-load-test-results-repository.md)
- [Yük testi sonuçlarını analiz etme](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Nasıl olur: Bir depodan yük testi sonuçlarını dışarı aktarma](../test/how-to-export-load-test-results-from-a-repository.md)
