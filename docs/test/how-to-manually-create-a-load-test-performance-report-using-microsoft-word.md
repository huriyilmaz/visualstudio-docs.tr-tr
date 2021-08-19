---
title: MS Word kullanarak yük testi perf raporu oluşturma
description: Yük testi raporlarını Microsoft Word özet görünümünden verileri kopyalayıp yapıştırarak el ile Test Sonuçları test raporları oluşturma hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, reporting
- load tests, creating Word reports
ms.assetid: 3b864c75-2699-48c1-a2b4-9651f108c267
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: 45844370a3a43c0d2a8f580e43bb5fd685f4d45b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122122988"
---
# <a name="how-to-manually-create-a-load-test-performance-report-using-microsoft-word"></a>Nasıl yapılır: Yük testi performans raporunu el ile Microsoft Word

Yük testi Microsoft Word ve graflar görünümünden verileri kopyalayıp yapıştırarak Test Sonuçları el ile oluşturabilirsiniz. Özet görünümü ve graflar görünümünde sunulan veriler, kopyalanan HTML biçiminde uygulanır.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!TIP]
> Ayrıntılar görünümünden tablolar görünümünden ve ekran görüntülerinden düz metin kopyalayıp Microsoft Word html biçiminde uygulanmaz ve ek biçimlendirme ve düzenleme gerektirir.

> [!TIP]
> Ayrıca, otomatik olarak düzenli Microsoft Excel de oluşturabilirsiniz. Daha fazla bilgi için, [bkz. How to: Create load test performance reports using using Microsoft Excel.](../test/how-to-create-load-test-performance-reports-using-microsoft-excel.md)

## <a name="copy-summary-view-data"></a>Özet görünümü verilerini kopyalama

1. Yükleme **menüsünde Test Sonuçları** görünümü görüntülenmezse araç çubuğunda **Özet'e** tıklayın.

2. Özet görünümünde sağ tıklayın ve Hepsini **Seç'i seçin.**

3. Özet görünümünde sağ tıklayın ve Kopyala'yı **seçin.** Bu, özet görünümü verilerini panoya HTML biçimi olarak işler.

4. Bu Microsoft Word özet görünümü verilerini istediğiniz konuma yapıştırın.

5. Artık, rapor ihtiyaçlarını karşılamak için kopyalanan içeriğin yönlerini değiştirebilir, biçimlendirebilirsiniz ve silebilirsiniz.

## <a name="copy-graph-view-data"></a>Graf görünümü verilerini kopyalama

1. Yükleme **ve Test Sonuçları** grafik görünümü şu anda görüntülenemedi ise araç çubuğunda **Grafikler'i** seçin.

2. (İsteğe bağlı) Aşağıdaki çizimde gösterildiği gibi, Microsoft Word belgenize kopyalamak istediğiniz grafiği yakınlaştırın. Daha fazla bilgi [için, bkz. How to: Zoom in a region of the graph](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md).

     ![Graph yakınlaştırma denetimi görüntüleme](../test/media/ltest_zoomcontrol.png)

3. Microsoft Word belgenize kopyalamak istediğiniz grafikte sağ tıklayın ve Kopyala'yı **seçin.**

4. Bu Microsoft Word, grafı ve ilişkili tablo verilerini istenen konuma yapıştırın.

    > [!WARNING]
    > Grafiği uzak masaüstünden kopyalayıp başka bir makineye yapıştıramazsınız çünkü grafik görüntüsü kopyalanmaz, yalnızca grafikle ilişkili tablo bilgileri kopyalanır. Graf görüntüsü, kopyalandığı makinedeki geçici dizinde depolanır ve ikinci makine o dizine başvuramaz.

## <a name="see-also"></a>Ayrıca bkz.

- [Test karşılaştırmaları veya eğilim analizi için yük testleri sonuçlarını bildirme](../test/compare-load-test-results.md)
- [Nasıl Microsoft Excel kullanarak yük testi performans raporları oluşturma](../test/how-to-create-load-test-performance-reports-using-microsoft-excel.md)
