---
title: Test Günlük Ayarlarını Yükleyin
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, logging, modifying
ms.assetid: 9649226a-857d-41ef-8ec7-047b6e498033
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0c0a9967f1248c6dc23c5d70be35788ad9e05eb2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75566312"
---
# <a name="modify-load-test-logging-settings"></a>Yük testi günlüğe kaydetme ayarlarını değiştirme

Tamamlanan yük testi nin yük testi sonucu, performans sayacı örneklerini ve test altındaki bilgisayarlardan düzenli olarak bir günlükte toplanan hata bilgilerini içerir. Bir yük testi çalışması boyunca çok sayıda performans sayacı örneği toplanabilir. Toplanan performans verilerinin miktarı, çalıştırmanın uzunluğuna, örnekleme aralığına, sınanan bilgisayar sayısına ve toplanacak sayaç sayısına bağlıdır. Büyük bir yük testi için, toplanan performans verilerinin miktarı kolayca birkaç gigabayt olabilir; bu nedenle, verilerin günlüğe ne sıklıkta kaydedilebildiğini değiştirmeyi düşünebilirsiniz. Bkz. [Test denetleyicileri ve test aracıları.](configure-test-agents-and-controllers-for-load-tests.md)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

*Test denetleyicisi,* toplanan tüm yük testi örnek verilerini test çalışırken bir veritabanı günlüğüne toplar. Zamanlama ayrıntıları ve hata ayrıntıları gibi ek veriler, test tamamlandığında veritabanına yüklenir.

|Görev|İlişkili konular|
|-|-----------------------|
|**Yük testi başarısız olursa günlükleri kaydet:** Bir yük testi başarısız olduğunda test günlüğünü kaydetmek isteyip istemediğinizi belirtebilirsiniz.|-   [Nasıl yapılır: Test günlükleri için test hataları kaydedilir seve belirtin](../test/how-to-specify-if-test-failures-are-saved-to-test-logs.md)|
|**Günlük dosyası için maksimum dosya boyutunu ayarlayın:** Günlük dosyası için kullanmak istediğiniz maksimum dosya boyutunu belirtmek için test denetleyicisi hizmetiyle ilişkili XML yapılandırma dosyasını düzenleme yapabilirsiniz.|`<add key="LogSizeLimitInMegs" value="20"/>` *QTCcontroller.exe.config* XML yapılandırma dosyasında değiştirin.|

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi çalıştırma ayarlarını yapılandırma](../test/configure-load-test-run-settings.md)
