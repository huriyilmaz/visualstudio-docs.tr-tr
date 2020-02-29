---
title: Yük testleri için sanal kullanıcı etkinliğini çözümleme
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- virtual user activity chart, viewing
ms.assetid: 8bda19b3-91c1-4daf-b6c7-09108bddadff
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c997f27e65a8e3992239fac78d52b0b4f19670c3
ms.sourcegitcommit: 1efb6b219ade7c35068b79fbdc573a8771ac608d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78169410"
---
# <a name="how-to-analyze-what-virtual-users-are-doing-during-a-load-test-using-the-virtual-user-activity-chart"></a>Nasıl yapılır: sanal kullanıcı etkinlik grafiğini kullanarak yük testi sırasında sanal kullanıcıların ne yaptıklarını çözümleme

**Sanal Kullanıcı Etkinlik grafiğini**kullanarak yük testinizdeki ilişkili sanal kullanıcı etkinliğini görüntüleyin. Grafikteki her satırın tek bir sanal kullanıcı temsil eder. **Sanal Kullanıcı etkinliği grafiği** , her bir sanal kullanıcının test sırasında hangi şekilde yürüttüğünü gösterir. Kullanıcı Etkinlik düzenlerini görebilir, yük düzenleri, yavaş veya başarısız testleri ilişkilendirin ve diğer sanal kullanıcı etkinliğini isteklerle bakın. **Sanal Kullanıcı etkinliği grafiği** yalnızca yük testinin çalışması bittikten sonra kullanılabilir.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Aşağıdaki yordamlarda, **Sanal Kullanıcı Etkinlik grafiğinin**nasıl görüntüleneceği, belirli bir kullanıcının etkinliğinin nasıl araştırılacağı ve filtrelemenin nasıl kullanılacağı gösterilmektedir.

## <a name="to-view-the-virtual-user-activity-chart-in-your-load-test-results"></a>Yük testi sonuçlarınızda Sanal kullanıcı aktivite grafiği görüntülemek için

1. Sanal Kullanıcı verilerini görüntülemek için, önce yük testiniz ile ilişkili **Zamanlama Ayrıntıları Depolama** özelliği Için **Tüm Bireysel Ayrıntılar** ayarını yapılandırmanız gerekir. Daha sonra Yük testi çalıştırın.

2. Sonra Yük test çalıştırmaları, test sonuçları Özet sayfasında görüntülenir. Araç çubuğunda **Kullanıcı ayrıntısı** düğmesini seçin.

     veya

     Araç çubuğundaki **grafikler** düğmesini seçerek grafikler görünümünü açın. Bir grafiğe sağ tıklayın ve sonra **Kullanıcı ayrıntısına git**' i seçin.

     Bu seçeneği kullanırsanız, **Sanal Kullanıcı etkinliği grafiği** sağ tıklattığınız testin kısmına otomatik olarak yakınlaştıracaktır. Örneğin, işaretçiniz yaklaşık 30 saniye işaretinde bulunuyorsa, ayrıntı görünümü **Sanal Kullanıcı etkinliği grafiğinin**alt kısmındaki **zaman dilimi yakınlaştırma** aracında yaklaşık olarak 30 saniyelik bir işaret görüntüler.

     Sonra, **Sanal Kullanıcı Etkinlik grafiğinde**belirli bir kullanıcının etkinlik ayrıntılarını Araştır ' ı kullanabilirsiniz.

## <a name="to-investigate-a-specific-users-activity-in-the-virtual-user-activity-chart"></a>Sanal kullanıcı aktivite grafiği, belirli bir kullanıcının etkinlik incelemek için

1. Grafikte belirli bir kullanıcının ayrıntılarını araştırmak istediğiniz alanı seçmek için **Sanal Kullanıcı etkinliği grafiğinin** alt kısmındaki zaman dilimini Yakınlaştır aracını kullanın.

2. Graftaki bir ayrıntı üzerinde gezdirin. Aşağıdaki bilgiler, araç ipucunda görüntülendiğini görürsünüz:

   - **Kullanıcı kimliği**

   - **Senaryo**

   - **Test**

   - **URL** (bir test veya işlemde görüntülenmez)

   - **Sonucu**

   - **Tarayıcı** (bir test veya işlemde görüntülenmez)

   - **Ağ**

   - **Başlangıç zamanı**

   - **Sürenin**

   - **Aracı**

   - **Test günlüğü** (test günlüğüne bağlantı)

     > [!NOTE]
     > Uygulamanızı hata ayıklamaya yardımcı olmak için, **Test günlüğü** bağlantısını, Web testi sonucunu veya günlük açma ile ilişkili birim testi sonucunu seçebilirsiniz.

     Sonra, **Sanal Kullanıcı Etkinlik grafiğinde**bulunan filtreleme ve vurgulama işlemlerini kullanabilirsiniz.

## <a name="to-use-filtering-options-in-the-virtual-user-activity-chart"></a>Sanal kullanıcı aktivite grafiği filtreleme seçeneklerini kullanmak için

1. **Ayrıntılar göstergesinde**, **Test**, **sayfa**veya **işlem**seçeneklerinden birini belirlemek için açılan listeyi kullanın.

    **Ayrıntılar gösterge bölmesi**

    ![Ayrıntı göstergesi panel](../test/media/ltest_detailslegend.png)

2. Hatalar, günlükleri, test, arama ve yük testi ile ilişkili aspx sayfaları için onay kutularının işaretini kaldırın veya seçin.

    **Sanal Kullanıcı etkinliği grafiği** buna uygun şekilde güncelleştirilir.

    **Sanal Kullanıcı etkinliği grafiği** , birkaç farklı ölçüte göre testleri, sayfaları ve işlemleri filtreleme yeteneği sağlar. Görünümden belirli testleri kaldırın veya tüm başarılı testleri kaldırın veya bazı hatalarla başarısız testleri Kaldır. Ayrıca, günlükleri olmayan tüm testleri de kaldırabilirsiniz.

    Örneğin, grafikteki tüm hataları kırmızı renkte görüntüleyen **(hataları vurgula)** seçeneğini belirleyebilirsiniz. Ayrıca, grafikte yeşil renkte renkli olan tüm test sonuçlarını görüntüleyen **(Günlükler ile sonuçları vurgula)** seçeneğini de belirleyebilirsiniz.

    **Filtre sonuçları paneli**

    ![Sonuçlar paneli Filtrele](../test/media/ltest_filterresults.png)

3. **Filtre sonuçlarında**aşağıdaki filtre seçeneklerinin onay kutularını seçin veya temizleyin:

   - **Yalnızca günlükleri olan sonuçları göster** Yalnızca bunlarla ilişkili test günlükleri olan test sonuçlarını görüntüler.

   - **Başarılı sonuçları göster** Başarılı sonuçları görüntüler.

   - **Hatalı sonuçları göster** Hata ayıklamada yardımcı olabilecek hatalar içeren sonuçları görüntüler.

     > [!NOTE]
     > **Sonuçları hatalara göre göster** düğümü altında listelenen hata türlerinin listesi, **Web performans test sonuçları Görüntüleyicisi** araç çubuğundaki **Tablolar** düğmesi seçilerek daha sonra araştırılır. Daha fazla bilgi için bkz. [Tablolar görünümünde Yük testi sonuçlarını ve hatalarını çözümleme](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

     **Sanal Kullanıcı etkinliği grafiği** buna uygun şekilde güncelleştirilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Ayrıntılar görünümündeki sanal kullanıcı etkinliğini çözümleme](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)
- [İzlenecek yol: sorunları yalıtmak için Sanal Kullanıcı etkinliği grafiğini kullanma](../test/walkthrough-use-the-virtual-user-activity-chart-to-isolate-issues.md)