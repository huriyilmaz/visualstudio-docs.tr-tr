---
title: 'Nasıl yapılır: Yük Testi Sonuçlarını bir Depoya Aktarma'
description: Yükleme ve yönetme Test Sonuçları iletişim kutusunu kullanarak yükleme Test Sonuçları deposuna bilgi yüklemeyi öğrenin.
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
ms.openlocfilehash: 61b0fdf8ea07ba7ad5106fccdd3543228651cd2a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122092494"
---
# <a name="how-to-import-load-test-results-into-a-repository"></a>Nasıl yapılır: yük testi sonuçlarını depoya aktarma

Bir yük testi çalıştırdığınızda, çalıştırma sırasında toplanan bilgiler Load Test Sonuçları deposunda depolanır. Load Test Sonuçları Deposu, performans sayacı verilerini ve hatalar hakkındaki bilgileri içerir. Daha fazla bilgi için bkz. [yük test sonuçları deposundaki yük testi sonuçlarını yönetme](../test/manage-load-test-results-in-the-load-test-results-repository.md).

Yük testi sonuçlarını, **yük test sonuçları aç ve Yönet** iletişim kutusunu kullanarak Yük Testi Düzenleyicisi yönetebilirsiniz. Yük testi sonuçlarını açabilir, içeri aktarabilir, dışarı aktarabilir ve kaldırabilirsiniz.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-import-results-into-a-repository"></a>Sonuçları bir depoya aktarmak için

1. Bir Web performans ve yük testi projesinden bir yük testi açın.

2. Katıştırılmış araç çubuğunda, **sonuçları aç ve Yönet**' i seçin.

     **Yük test sonuçları aç ve Yönet** iletişim kutusu görüntülenir.

3. **Yük testi sonuçlarını bulmak için bir denetleyici adı girin**' de bir denetleyici seçin. **\<local>** Yerel olarak depolanan sonuçlara erişmek için seçin.

     Yük testi sonuçları varsa, bunlar **Yük testi sonuçları** listesinde görünürler. Sütunlar **saat**, **süre**, **Kullanıcı**, **sonuç**, **Test** ve **Açıklama**. **Test, testin adını içerir ve** **Açıklama** , test çalıştırılmadan önce eklenen isteğe bağlı açıklamayı içerir.

4. **Içeri aktar**' ı seçin.

     **Yük test sonuçları Içeri aktar** iletişim kutusu görünür.

5. **Dosya adı** kutusunda, arşivlenmiş bir test sonuçları dosyasının adını yazın ve **Aç**' ı seçin.

     \- veya

     Dosyasına gidin ve **Aç**' ı seçin.

    > [!NOTE]
    > Bu adımda belirttiğiniz arşivlenmiş bir test sonuçları dosyası, dışarı aktarma işlemi gerçekleştirerek oluşturulmuş olmalıdır.

     Sonuçlar içeri aktarılır ve **Yük testi sonuçları** listesinde görüntülenir.

## <a name="see-also"></a>Ayrıca bkz.

- [Yük Test Sonuçları deposundaki yük testi sonuçlarını yönetme](../test/manage-load-test-results-in-the-load-test-results-repository.md)
- [Yük testi sonuçlarını çözümle](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Nasıl yapılır: bir depodan yük testi sonuçlarını dışarı aktarma](../test/how-to-export-load-test-results-from-a-repository.md)
