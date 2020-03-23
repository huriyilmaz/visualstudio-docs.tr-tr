---
title: Yük Testi Sanal Kullanıcı Etkinliğini Analiz Etme
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
manager: jillfra
ms.openlocfilehash: 0289ff0d4a20eacc4f6801d9300d39df594bc79e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591241"
---
# <a name="analyzing-load-test-virtual-user-activity-in-the-details-view-of-the-load-test-analyzer"></a>Yük Testi Sanal Kullanıcı Etkinliğini, Yük Testi Çözümleyicisinin Ayrıntılar görünümünde analiz etme

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

**Sanal Kullanıcı Etkinlik Grafiği**

![Sanal Kullanıcı Etkinlik Grafiği](../test/media/virtual_actchart.png)

**Ayrıntılar** görünümü, tek tek sanal kullanıcıların yükleme testi sırasında ne yaptığını görsel olarak analiz etmek için kullanılan **Sanal Kullanıcı Etkinlik Grafiği'ni**görüntüler. **Sanal Kullanıcı Etkinlik Grafiği,** kullanıcı etkinliği desenlerini görmenizi, desenleri yüklemenizi, başarısız veya yavaş testleri ilişkilendirmenizi ve istekleri diğer sanal kullanıcı etkinliğiyle görmenizi sağlar. **Sanal Kullanıcı Etkinlik Grafiği,** CPU kullanımındaki ani artışları, isteklerde saniyede düşüşleri ve ani artışlar ve düşmeler sırasında hangi testlerin veya sayfaların çalıştığını belirlemenize de yardımcı olabilir.

> [!NOTE]
> **Sanal Kullanıcı Etkinliği Ayrıntıları Grafiği'ni**kullanmak istediğiniz yükleme testini çalıştırmadan önce, Yük Performansı Testi Düzenleyicisi'ni kullanarak Zamanlama Ayrıntıları **Depolama** özelliğinin **AllIndividualDetails** seçeneğine ayarlı olduğunu doğrulamanız gerekir.

**Ayrıntılar Legend Paneli**

![Ayrıntılar efsane paneli](../test/media/ltest_detailslegend.png)

Ayrıntılar gösterge paneli Sanal **Kullanıcı Etkinlik Grafiği'nde**görünür. Ayrıntılar gösterge bölmesi, testleri, sayfaları ve hareketleri birkaç farklı ölçüte göre filtrelemenizi sağlar. Örneğin, görünümden belirli testleri kaldırabilir veya tüm başarılı testleri kaldırabilir veya belirli hatalarla başarısız olan testleri kaldırabilirsiniz. Günlükleri olmayan tüm testleri de kaldırabilirsiniz.

Başarısız olan testleri vurgulayabilirsiniz, bu da tüm başarısız testleri kırmızı renkte görüntüler. Ayrıca, test günlükleri olan testleri vurgulayabilirsiniz. Günlükleri ile testler yeşil renkli olacaktır.

**Filtre sonuçları Panel**

![Filtre sonuçları paneli](../test/media/ltest_filterresults.png)

Filtre sonuç paneli Sanal **Kullanıcı Etkinlik Grafiği'nde**görünür. Filtre sonuç paneli aşağıdakileri filtreleyebilir:

- **Yalnızca günlüklerle sonuçları göster** Yalnızca kendileriyle ilişkili test günlükleri olan test sonuçlarını görüntüler.

- **Başarılı sonuçları göster** Başarılı sonuçlar görüntüler.

- **Sonuçları hatalarla göster** Sonuçları hata ayıklamada yardımcı olabilecek hatalarla görüntüler.

## <a name="tasks"></a>Görevler

|Görevler|İlişkili konular|
|-|-|
|**Yük testinizi çalıştırın:** Bir yük testi oluşturduktan ve sanal kullanıcı etkinliği veri toplamayı etkinleştirecek şekilde yapılandırdıktan sonra, **Sanal Kullanıcı Etkinlik Grafiği'ni**görüntülemek için testi tamamlanana kadar çalıştırmanız gerekir.||
|**Sanal kullanıcı etkinlik verilerini içeren yük testi sonuçlarını görüntüleyin:** Yük testiniz oluşturulduktan, yapılandırıldıktan ve çalıştırmayı tamamladıktan sonra, **Sanal Kullanıcı Etkinlik Grafiği'ni**kullanarak sanal kullanıcı etkinlik verilerini görüntüleyebilirsiniz.|-   [Yük testi sonuçlarını analiz edin](../test/analyze-load-test-results-using-the-load-test-analyzer.md)<br />-   [Nasıl yapılır: Yükleme testi sırasında sanal kullanıcıların ne yaptığını analiz etme](../test/how-to-analyze-virtual-user-activity-during-a-load-test.md)|
|**Yük testlerinde performans sorunlarını yalıtın:** Yük testinizdeki performans sorunlarını yalıtmaya yardımcı olmak için **Sanal Kullanıcı Etkinlik Grafiği'ni** kullanabilirsiniz.|-   [İzole: Sorunları yalıtmak için sanal kullanıcı etkinlik grafiğini kullanma](../test/walkthrough-use-the-virtual-user-activity-chart-to-isolate-issues.md)|

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi sonuçlarını analiz edin](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Tablolar görünümünde yük testi sonuçlarını ve hatalarını analiz etme](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)
