---
title: Yük testi günlük kaydı ayarları
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, logging, modifying
ms.assetid: 9649226a-857d-41ef-8ec7-047b6e498033
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0c0a9967f1248c6dc23c5d70be35788ad9e05eb2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75566312"
---
# <a name="modify-load-test-logging-settings"></a>Yük testi günlük ayarlarını değiştir

Tamamlanan yük testinin yük testi sonucu, test altındaki bilgisayarlardan düzenli aralıklarla bir günlükte toplanan performans sayacı örneklerini ve hata bilgilerini içerir. Yük testi çalışması sırasında çok sayıda performans sayacı örneği toplanabilir. Toplanan performans verileri miktarı çalıştırmanın uzunluğuna, örnekleme aralığına, test edilen bilgisayar sayısına ve toplanacak sayaç sayısına bağlıdır. Büyük bir yük testi için toplanan performans verisi miktarı kolayca birkaç gigabayt olabilir; Bu nedenle, verilerin günlüğe ne sıklıkta kaydedileceğini değiştirmeyi düşünebilirsiniz. Bkz. [Test denetleyicileri ve test aracıları](configure-test-agents-and-controllers-for-load-tests.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Test *denetleyicisi* , test çalışırken tüm toplanan yük testi örnek verilerini bir veritabanı günlüğüne biriktirir. Zamanlama ayrıntıları ve hata ayrıntıları gibi ek veriler, test tamamlandığında veritabanına yüklenir.

|Görev|İlişkili konular|
|-|-----------------------|
|**Yük testi başarısız olursa günlükleri Kaydet:** Bir yük testi başarısız olduğunda test günlüğünü kaydetmek istediğinizi belirtebilirsiniz.|-   [Nasıl yapılır: test başarısızlıklarının test günlüklerine kaydedilip kaydedilmediğini belirtme](../test/how-to-specify-if-test-failures-are-saved-to-test-logs.md)|
|**Günlük dosyası için en büyük dosya boyutunu ayarlayın:** Günlük dosyası için kullanmak istediğiniz en büyük dosya boyutunu belirtmek için test denetleyicisi hizmeti ile ilişkili XML yapılandırma dosyasını düzenleyebilirsiniz.|`<add key="LogSizeLimitInMegs" value="20"/>` *QTCcontroller.exe.config* XML yapılandırma dosyasında değiştirin.|

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi çalıştırma ayarlarını yapılandır](../test/configure-load-test-run-settings.md)
