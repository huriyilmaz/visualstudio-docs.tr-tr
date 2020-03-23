---
title: Yük testleri için Sanal Kullanıcı Etkinliğini Analiz Edin
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- virtual user activity chart, viewing
ms.assetid: 8bda19b3-91c1-4daf-b6c7-09108bddadff
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c997f27e65a8e3992239fac78d52b0b4f19670c3
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "78169410"
---
# <a name="how-to-analyze-what-virtual-users-are-doing-during-a-load-test-using-the-virtual-user-activity-chart"></a>Nasıl yapılır: Sanal kullanıcı etkinlik grafiğini kullanarak yükleme testi sırasında sanal kullanıcıların ne yaptığını analiz etme

**Sanal Kullanıcı Etkinlik Grafiği'ni**kullanarak yük testinizle ilişkili sanal kullanıcı etkinliğini görüntüleyin. Grafikteki her satır tek bir sanal kullanıcıyı temsil eder. **Sanal Kullanıcı Etkinlik Grafiği,** her sanal kullanıcının test sırasında tam olarak ne yaptığını gösterir. Kullanıcı etkinliği kalıplarını, yükleme desenlerini görebilir, başarısız veya yavaş testleri ilişkilendirebilir ve istekleri diğer sanal kullanıcı etkinliğiyle görebilirsiniz. **Sanal Kullanıcı Etkinlik Grafiği** yalnızca yük testi çalışması bittikten sonra kullanılabilir.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Aşağıdaki yordamlar Sanal Kullanıcı **Etkinlik Grafiği'ni**nasıl görüntüleneniz, belirli bir kullanıcının etkinliğini nasıl araştırılakullanılacağı ve filtrelemenin nasıl kullanılacağını gösterir.

## <a name="to-view-the-virtual-user-activity-chart-in-your-load-test-results"></a>Yük testi sonuçlarınızda Sanal Kullanıcı Etkinlik Grafiği'ni görüntülemek için

1. Sanal kullanıcı verilerini görüntülemek için öncelikle yükleme testinizle ilişkili **Zamanlama Ayrıntıları Depolama** özelliği için Tüm Bireysel **Ayrıntılar** ayarını yapılandırmanız gerekir. Sonra yükleme testini çalıştırın.

2. Yükleme testiniz çalıştırıladıktan sonra test sonuçları özet sayfası görüntülenir. Araç çubuğundaki **Kullanıcı Ayrıntısı** düğmesini seçin.

     -veya-

     Araç çubuğundaki **Grafikler** düğmesini seçerek Grafikler görünümünü açın. Bir grafiğe sağ tıklayın ve ardından **kullanıcı ayrıntısına git'i**seçin.

     Bu seçeneği kullanırsanız, **Sanal Kullanıcı Etkinlik Grafiği,** testin sağ tıklatma kısmını otomatik olarak yakınlaştırır. Örneğin, işaretçiniz yaklaşık 30 saniyelik işarette bulunuyorsa, ayrıntı görünümü **Sanal Kullanıcı Etkinlik Grafiği'nin**altındaki Zaman **Dilimini Yakınlaştırma** aracındaki 30 saniyelik işarette yaklaşık olarak görüntülenir.

     Ardından, **Sanal Kullanıcı Etkinlik Grafiği'nde**belirli bir kullanıcının etkinlik ayrıntılarını araştırma'yı kullanabilirsiniz.

## <a name="to-investigate-a-specific-users-activity-in-the-virtual-user-activity-chart"></a>Sanal Kullanıcı Etkinlik Grafiği'nde belirli bir kullanıcının etkinliğini araştırmak için

1. **Grafikte** belirli bir kullanıcının ayrıntılarını araştırmak istediğiniz bir alanı seçmek için Sanal Kullanıcı Etkinlik Grafiği'nin altındaki Zaman Dilimini Yakınla aracını kullanın.

2. İşaretçini grafikteki bir ayrıntının üzerine tover. Araç ipucunda aşağıdaki bilgilerin görüntülendiğine dikkat edin:

   - **Kullanıcı Kimliği**

   - **Senaryo**

   - **Test**

   - **URL** (Test veya işlemde görüntüleniyor)

   - **Sonuç**

   - **Tarayıcı** (Test veya işlemde görüntüleniyor)

   - **Ağ**

   - **Başlangıç Saati**

   - **Süre**

   - **Aracı**

   - **Test günlüğü** (Test günlüğüne bağlantı)

     > [!NOTE]
     > Uygulamanızın hata ayıklanmasına yardımcı olmak için, **Test günlüğü** bağlantısını seçerseniz, web test sonucu veya günlük açıkla ilişkili birim test sonucu.

     Ardından, **Sanal Kullanıcı Etkinlik Grafiği'nde**bulunan filtreleme ve vurgulama işlemlerini kullanabilirsiniz.

## <a name="to-use-filtering-options-in-the-virtual-user-activity-chart"></a>Sanal Kullanıcı Etkinlik Grafiği'nde filtreleme seçeneklerini kullanmak için

1. Ayrıntılar **Gösterge'** de, **Test,** **Sayfa**veya **Hareket'i**seçmek için açılır listeyi kullanın.

    **Ayrıntılar Legend paneli**

    ![Ayrıntılar efsane paneli](../test/media/ltest_detailslegend.png)

2. Yükleme testiile ilişkili hatalar, günlükler, testler, arama ve aspx sayfaları için onay kutularını seçin veya temizleyin.

    **Sanal Kullanıcı Etkinlik Grafiği** buna göre güncellenir.

    **Sanal Kullanıcı Etkinlik Grafiği,** testleri, sayfaları ve hareketleri birkaç farklı ölçüte göre filtreleme olanağı sağlar. Görünümden belirli testleri kaldırabilir veya tüm başarılı testleri kaldırabilir veya belirli hatalarla başarısız olan testleri kaldırabilirsiniz. Günlükleri olmayan tüm testleri de kaldırabilirsiniz.

    Örneğin, grafikteki tüm hataları kırmızı renkle gösteren **(Hataları Vurgula)** seçeneğini seçebilirsiniz. Ayrıca, grafikte yeşil renkte günlükleri olan tüm test sonuçlarını görüntüleyen **(Günlüklerle sonuçları vurgulay)** seçeneğini de seçebilirsiniz.

    **Filtre sonuçları paneli**

    ![Filtre sonuçları paneli](../test/media/ltest_filterresults.png)

3. Filtre **sonuçlarında,** aşağıdaki filtre seçenekleri için onay kutularını seçin veya temizleyin:

   - **Yalnızca günlüklerle sonuçları göster** Yalnızca kendileriyle ilişkili test günlükleri olan test sonuçlarını görüntüler.

   - **Başarılı sonuçları göster** Başarılı sonuçlar görüntüler.

   - **Sonuçları hatalarla göster** Sonuçları hata ayıklamada yardımcı olabilecek hatalarla görüntüler.

     > [!NOTE]
     > **Hata düğümüyle sonuçları göster** altında listelenen hata türlerinin listesi, Web Performans Testi Sonuçları **Görüntüleyici** araç çubuğundaki **Tablolar** düğmesini seçerek daha da araştırılabilir. Daha fazla bilgi için bkz: [Tablolar görünümünde yük testi sonuçlarını ve hatalarını analiz](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)et.

     **Sanal Kullanıcı Etkinlik Grafiği** buna göre güncellenir.

## <a name="see-also"></a>Ayrıca bkz.

- [Ayrıntılar görünümünde sanal kullanıcı etkinliğini analiz edin](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)
- [İzole: Sorunları yalıtmak için sanal kullanıcı etkinlik grafiğini kullanma](../test/walkthrough-use-the-virtual-user-activity-chart-to-isolate-issues.md)