---
title: Yük Testi Sanal Kullanıcı Etkinliğini Analiz Etme
description: Sanal Kullanıcı Etkinlik Grafiği'nin görüntü olduğu Ayrıntılar görünümü hakkında bilgi edinebilirsiniz. Yük testi sırasında tek tek sanal kullanıcıların ne yaptığını analiz etme.
ms.custom: SEO-VS-2020
ms.date: 10/03/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.monitor.activitychart
helpviewer_keywords:
- virtual user activity chart
- load test, virtual user activity chart
ms.assetid: 63f4bd42-3cfb-4eee-af68-e8334976539e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: 96809db56259e0a5e2225aa223ebeefcaa2e249ed567d1051c88aec04fda63bb
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121395478"
---
# <a name="analyzing-load-test-virtual-user-activity-in-the-details-view-of-the-load-test-analyzer"></a>Yük Testi Çözümleyicisi'nin Ayrıntılar görünümünde yük testi sanal kullanıcı etkinliğini analiz etme

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

**Sanal Kullanıcı Etkinlik Grafiği**

![Sanal Kullanıcı Etkinlik Grafiği](../test/media/virtual_actchart.png)

Ayrıntılar **görünümü,** yük **testi sırasında tek tek** sanal kullanıcıların neler yaptığını görsel olarak analiz etmek için kullanılan Sanal Kullanıcı Etkinlik Grafiği'nin görüntülenir. **Sanal Kullanıcı Etkinliği Grafiği** kullanıcı etkinliğinin desenlerini, yük desenlerini görmenizi, başarısız veya yavaş testlerle ilişki oluşturmanizi ve istekleri diğer sanal kullanıcı etkinliğiyle görmenizi sağlar. Sanal **Kullanıcı Etkinlik Grafiği** cpu kullanımında ani artışları, saniye başına isteklerde düşüşleri ve ani artışlar ve düşüşler sırasında hangi testlerin veya sayfaların çalıştırlı olduğunu belirlemenize de yardımcı olabilir.

> [!NOTE]
> Sanal Kullanıcı Etkinlik Ayrıntıları Grafiği'ni kullanmak istediğiniz yük testini çalıştırmadan **önce,** Yük Performansı Test Düzenleyicisi'ni kullanarak **Timing Details Depolama** özelliğinin **AllIndividualDetails** seçeneğine ayar olduğunu doğrulamanız gerekir.

**Ayrıntılar Gösterge Paneli**

![Ayrıntılar gösterge paneli](../test/media/ltest_detailslegend.png)

Ayrıntılar gösterge paneli Sanal Kullanıcı Etkinlik **Grafiği'ne görünür.** Ayrıntılar gösterge bölmesi testleri, sayfaları ve işlemleri çeşitli ölçütlere göre filtrelemenizi sağlar. Örneğin, görünümden belirli testleri kaldırabilir veya tüm başarılı testleri kaldırabilir ya da belirli hatalarla başarısız olan testleri kaldırabilirsiniz. Ayrıca, günlükleri olan tüm testleri de kaldıracaksınız.

Başarısız olan testleri vurgulayın; bu, tüm başarısız testleri kırmızı renkle gösterir. Test günlükleri olan testleri de vurguleyebilirsiniz. Günlüklerle yapılan testler yeşil renkle renklendirilmiş olur.

**Filtre sonuçları Paneli**

![Filtre sonuçları paneli](../test/media/ltest_filterresults.png)

Filtre sonuçları paneli, Sanal Kullanıcı **Etkinlik Grafiği'ne görünür.** Sonuçları filtrele paneli aşağıdakilere göre filtreleyebilirsiniz:

- **Yalnızca sonuçları günlüklerle gösterme** Yalnızca test günlüklerinin ilişkili olduğu test sonuçlarını görüntüler.

- **Başarılı sonuçları gösterme** Başarılı sonuçları görüntüler.

- **Sonuçları hatalarla gösterme** Hata ayıklamaya yardımcı olan hatalarla sonuçları görüntüler.

## <a name="tasks"></a>Görevler

|Görevler|İlişkili konular|
|-|-|
|**Yük testini çalıştırın:** Bir yük testi oluşturduktan ve sanal kullanıcı etkinliği verilerini toplamayı etkinleştiracak şekilde yapılandırdıktan sonra, Sanal Kullanıcı Etkinlik Grafiğini görüntülemek için testi tamamlayana **kadar çalıştırmanız gerekir.**||
|**Sanal kullanıcı etkinliği verilerini içeren yük testi sonuçlarını görüntüleme:** Yük testini oluşturduktan, yapılandırdıktan ve çalıştırmayı tamamlandıktan sonra, Sanal Kullanıcı Etkinlik Grafiği'ne bakarak **sanal kullanıcı etkinliği verilerini görüntüebilirsiniz.**|-   [Yük testi sonuçlarını analiz etme](../test/analyze-load-test-results-using-the-load-test-analyzer.md)<br />-   [Nasıl: Yük testi sırasında sanal kullanıcıların ne yaptığını analiz etme](../test/how-to-analyze-virtual-user-activity-during-a-load-test.md)|
|**Yük testlerinde performans sorunlarını yalıtma:** Yük testinde performans **sorunlarını yalıtmak** için Sanal Kullanıcı Etkinlik Grafiği'nin kullanabilirsiniz.|-   [Adım adım kılavuz: Sorunları yalıtmak için sanal kullanıcı etkinlik grafiğini kullanma](../test/walkthrough-use-the-virtual-user-activity-chart-to-isolate-issues.md)|

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi sonuçlarını analiz etme](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Tablolar görünümünde yük testi sonuçlarını ve hatalarını analiz etme](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)
