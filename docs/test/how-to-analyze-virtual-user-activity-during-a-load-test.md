---
title: Yük testleri için Sanal Kullanıcı Etkinliğini Analiz Etme
description: Kullanıcı etkinliğinin desenlerini ve diğer bilgileri görmek için test sırasında her bir sanal kullanıcının çalıştırarak sanal kullanıcı etkinlik grafiğini nasıl göreceğiniz hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- virtual user activity chart, viewing
ms.assetid: 8bda19b3-91c1-4daf-b6c7-09108bddadff
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: f58b696b706c6d4b2313f5c6dd82c3b801edbbc7
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122026739"
---
# <a name="how-to-analyze-what-virtual-users-are-doing-during-a-load-test-using-the-virtual-user-activity-chart"></a>Nasıl: Sanal kullanıcı etkinlik grafiğini kullanarak yük testi sırasında sanal kullanıcıların neler yaptığını analiz etme

Sanal Kullanıcı Etkinlik Grafiği'nin kullanarak yük testiyle ilişkili sanal **kullanıcı etkinliğini görüntüleme.** Grafikte yer alan her satır tek bir sanal kullanıcıyı temsil eder. Sanal **Kullanıcı Etkinlik Grafiği,** test sırasında her bir sanal kullanıcının tam olarak ne yürütt yaptığını gösterir. Kullanıcı etkinliğinin desenlerini, yük desenlerini görebilir, başarısız veya yavaş testlerle ilişkili olabilir ve istekleri diğer sanal kullanıcı etkinliğiyle birlikte görebilir. Sanal **Kullanıcı Etkinlik Grafiği yalnızca** yük testinin çalıştırması tamam olduktan sonra kullanılabilir.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Aşağıdaki yordamlar Sanal Kullanıcı Etkinlik Grafiği'nin nasıl görüntülenmiş **olduğunu,** belirli bir kullanıcının etkinliğinin nasıl araştırıldığını ve filtrelemenin nasıl kullanıldığını gösterir.

## <a name="to-view-the-virtual-user-activity-chart-in-your-load-test-results"></a>Yük testi sonuçlarınız içinde Sanal Kullanıcı Etkinlik Grafiği'ne görüntülemek için

1. Sanal kullanıcı verilerini görüntülemek için, önce  yük testiyle ilişkili **Zamanlama** Ayrıntıları Depolama Tüm Bireysel Ayrıntılar ayarını yapılandırmanız gerekir. Ardından yük testini çalıştırın.

2. Yük testini çalıştırdıktan sonra test sonuçları özet sayfası görüntülenir. Araç çubuğunda **Kullanıcı Ayrıntıları** düğmesini seçin.

     -veya-

     Araç çubuğundaki Grafikler düğmesini **seçerek Graflar** görünümünü açın. Bir grafiye sağ tıklayın ve ardından Kullanıcı **ayrıntılarına git'i seçin.**

     Bu seçeneği kullanırsanız, **Sanal Kullanıcı Etkinlik** Grafiği testin sağ tıklamış olduğu bölümü otomatik olarak yakınlaştırabilir. Örneğin, işaretçiniz yaklaşık 30 saniyelik işarette yer alıyorsa, ayrıntı görünümü Sanal Kullanıcı Etkinliği  Grafiği'nin altındaki Zaman dönemi yakınlaştırma aracında yaklaşık 30 saniyelik **işarette görüntülenir.**

     Daha sonra, Sanal Kullanıcı Etkinlik Grafiği'nin belirli bir kullanıcının etkinlik **ayrıntılarını araştırabilirsiniz.**

## <a name="to-investigate-a-specific-users-activity-in-the-virtual-user-activity-chart"></a>Sanal Kullanıcı Etkinlik Grafiği'ne belirli bir kullanıcının etkinliğini araştırmak için

1. Grafikte belirli bir kullanıcıyla ilgili  ayrıntıları araştırmak istediğiniz bir alanı seçmek için Sanal Kullanıcı Etkinlik Grafiği'nin altındaki Zaman dönemi yakınlaştırma aracını kullanın.

2. İşaretçinizi grafikte bir ayrıntının üzerine gelin. Araç ipucunda aşağıdaki bilgilerin görüntülendiğinden dikkat edin:

   - **Kullanıcı Kimliği**

   - **Senaryo**

   - **Test**

   - **URL** (Testte veya işlemde görüntülenmez)

   - **Sonuç**

   - **Tarayıcı** (Testte veya işlemde görüntülenmez)

   - **Ağ**

   - **Başlangıç Zamanı**

   - **Süre**

   - **Aracı**

   - **Test günlüğü** (Test günlüğüne bağlantı)

     > [!NOTE]
     > Test günlüğü bağlantısını, web testi sonuçlarını  veya günlükle ilişkili birim testi sonuçlarını seçerseniz, uygulamanın hata ayıklamasına yardımcı olmak için açık günlük.

     Daha sonra, Sanal Kullanıcı Etkinlik Grafiği'ne yönelik filtreleme ve vurgulama **işlemlerini kullanabilirsiniz.**

## <a name="to-use-filtering-options-in-the-virtual-user-activity-chart"></a>Sanal Kullanıcı Etkinlik Grafiği'nin filtreleme seçeneklerini kullanmak için

1. Ayrıntılar **Göstergesinde,** test , Sayfa veya İşlem'i seçmek **için** açılan listeyi **kullanın.**

    **Ayrıntılar Gösterge paneli**

    ![Ayrıntılar gösterge paneli](../test/media/ltest_detailslegend.png)

2. Yük testiyle ilişkili hatalar, günlükler, testler, arama ve aspx sayfalarının onay kutularını seçin veya temizleyin.

    Sanal **Kullanıcı Etkinlik Grafiği uygun** şekilde güncelleştirmeler.

    Sanal **Kullanıcı Etkinlik Grafiği,** testleri, sayfaları ve işlemleri çeşitli ölçütlere göre filtreleme olanağı sağlar. Görünümden belirli testleri kaldırabilir veya tüm başarılı testleri kaldırabilir ya da belirli hatalarla başarısız olan testleri kaldırabilirsiniz. Ayrıca, günlükleri olan tüm testleri de kaldıracaksınız.

    Örneğin, grafikte tüm hataları kırmızı renkle görüntüleyen **(Hataları vurgula)** seçeneğini belirleyin. Ayrıca grafikte yeşil **renkli günlükler bulunan** tüm test sonuçlarını görüntüleyen (Sonuçları günlüklerle vurgula) seçeneğini de belirleyin.

    **Filtre sonuçları paneli**

    ![Filtre sonuçları paneli](../test/media/ltest_filterresults.png)

3. Filtre **sonuçları alanında,** aşağıdaki filtre seçeneklerinin onay kutularını seçin veya temizleyin:

   - **Yalnızca sonuçları günlüklerle gösterme** Yalnızca test günlüklerinin ilişkili olduğu test sonuçlarını görüntüler.

   - **Başarılı sonuçları gösterme** Başarılı sonuçları görüntüler.

   - **Sonuçları hatalarla gösterme** Hata ayıklamaya yardımcı olan hatalarla sonuçları görüntüler.

     > [!NOTE]
     > Sonuçları hatalarla göster düğümü altında  listelenen hata türlerinin listesi, Web Performansı  ve Görüntüleyici araç çubuğunda tablolar düğmesi **seçerek Test Sonuçları araştırabilirsiniz.** Daha fazla bilgi için Tablolar [görünümündeki Yük testi sonuçlarını ve hatalarını analiz etme makalesi'ne bakın.](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)

     Sanal **Kullanıcı Etkinlik Grafiği uygun** şekilde güncelleştirmeler.

## <a name="see-also"></a>Ayrıca bkz.

- [Ayrıntılar görünümünde sanal kullanıcı etkinliğini analiz etme](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)
- [Adım adım kılavuz: Sorunları yalıtmak için sanal kullanıcı etkinlik grafiğini kullanma](../test/walkthrough-use-the-virtual-user-activity-chart-to-isolate-issues.md)