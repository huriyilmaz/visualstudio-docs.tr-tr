---
title: MS Word kullanarak yük testi performans raporu oluşturma
description: Load Test Sonuçları Özet görünümü ve Grafikler görünümünden verileri kopyalayıp yapıştırarak Microsoft Word yük testi raporlarını el ile oluşturmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, reporting
- load tests, creating Word reports
ms.assetid: 3b864c75-2699-48c1-a2b4-9651f108c267
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2bddd2585d3bc88821fb2c265f21bfda84ed7bef
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2020
ms.locfileid: "95441006"
---
# <a name="how-to-manually-create-a-load-test-performance-report-using-microsoft-word"></a>Nasıl yapılır: Microsoft Word kullanarak yük testi performans raporu el Ile oluşturma

Load Test Sonuçları Özet görünümü ve grafik görünümünden veri kopyalayıp yapıştırarak Microsoft Word yük testi raporlarını el ile oluşturabilirsiniz. Özet görünümü ve grafikler görünümünde sunulan veriler, kopyalanırken HTML biçiminde uygulanır.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!TIP]
> Ayrıntılar görünümündeki Tablo görünümündeki ve ekran görüntülerinin düz metnini Microsoft Word 'e kopyalayabilir, ancak HTML biçiminde uygulanmaz ve ek biçimlendirme ve düzenlemeler gerekir.

> [!TIP]
> Ayrıca, düzenli olarak düzenlenmiş Microsoft Excel raporları da oluşturabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: Microsoft Excel kullanarak yük testi performans raporları oluşturma](../test/how-to-create-load-test-performance-reports-using-microsoft-excel.md).

## <a name="copy-summary-view-data"></a>Özet görünümü verilerini Kopyala

1. **Yük test sonuçları**, Özet görünümü şu anda görüntülenmiyorsa, araç çubuğunda **Özet** ' e tıklayın.

2. Özet görünümünde, sağ tıklayın ve **Tümünü Seç**' i seçin.

3. Özet görünümünde, sağ tıklayın ve **Kopyala**' yı seçin. Bu, Özet Görünüm verilerini Pano 'ya HTML biçimi olarak işler.

4. Microsoft Word 'de, Özet görünümü verilerini istenen konuma yapıştırın.

5. Artık, raporlama ihtiyaçlarınızı karşılamak için kopyalanmış içeriğin yönlerini değiştirebilir, biçimlendirebilir ve silebilirsiniz.

## <a name="copy-graph-view-data"></a>Grafik görünümü verilerini Kopyala

1. **Yük test sonuçları**, grafik görünümü şu anda görüntülenmiyorsa, araç çubuğunda **grafikler** ' i seçin.

2. Seçim Aşağıdaki çizimde gösterildiği gibi, Microsoft Word belgenize kopyalamak istediğiniz belirli bir grafiği yakınlaştırın. Daha fazla bilgi için bkz. [nasıl yapılır: grafiğin bir bölgesini yakınlaştırma](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md).

     ![Grafik görünümü yakınlaştırma denetimi](../test/media/ltest_zoomcontrol.png)

3. Microsoft Word belgenize kopyalamak istediğiniz grafikte, sağ tıklayıp **Kopyala**' yı seçin.

4. Microsoft Word 'de grafiği ve ilişkili tablo verilerini istenen konuma yapıştırın.

    > [!WARNING]
    > Grafiği uzak bir masaüstünden kopyalayamazsınız ve grafik görüntüsü değil yalnızca grafikle ilişkili tablo bilgileri kopyalanacağından başka bir makineye yapıştıramazsınız. Graf görüntüsü, kopyalandığı makinedeki geçici dizinde depolanır ve ikinci makine o dizine başvuramaz.

## <a name="see-also"></a>Ayrıca bkz.

- [Test karşılaştırmaları veya eğilim analizi için yük testi sonuçlarını raporla](../test/compare-load-test-results.md)
- [Nasıl yapılır: Microsoft Excel kullanarak yük testi performans raporları oluşturma](../test/how-to-create-load-test-performance-reports-using-microsoft-excel.md)
