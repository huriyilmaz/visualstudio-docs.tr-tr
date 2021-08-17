---
title: MS Word kullanarak yük testi performans raporu oluşturma
description: yük Test Sonuçları özet görünümü ve grafikler görünümünden verileri kopyalayıp yapıştırarak Microsoft Word yük testi raporlarını el ile oluşturmayı öğrenin.
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
ms.openlocfilehash: dd31dde1e484f7223e50ab552c0eeebfa28a963b6a66122963e04e3a2bdc0b8e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121395217"
---
# <a name="how-to-manually-create-a-load-test-performance-report-using-microsoft-word"></a>Nasıl yapılır: Microsoft Word kullanarak el Ile yük testi performans raporu oluşturma

yük Test Sonuçları özet görünümü ve grafikler görünümünden verileri kopyalayıp yapıştırarak Microsoft Word yük testi raporları el ile oluşturabilirsiniz. Özet görünümü ve grafikler görünümünde sunulan veriler, kopyalanırken HTML biçiminde uygulanır.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!TIP]
> ayrıntılar görünümündeki tablo görünümü ve ekran görüntüleri arasından düz metin kopyalayabilir Microsoft Word, ancak HTML biçiminde uygulanmaz ve ek biçimlendirme ve düzenlemeler gerekir.

> [!TIP]
> ayrıca düzenlenmiş Microsoft Excel raporlarını otomatik olarak oluşturabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: kullanarak yük testi performans raporları oluşturma Microsoft Excel](../test/how-to-create-load-test-performance-reports-using-microsoft-excel.md).

## <a name="copy-summary-view-data"></a>Özet görünümü verilerini Kopyala

1. **Yük test sonuçları**, Özet görünümü şu anda görüntülenmiyorsa, araç çubuğunda **Özet** ' e tıklayın.

2. Özet görünümünde, sağ tıklayın ve **Tümünü Seç**' i seçin.

3. Özet görünümünde, sağ tıklayın ve **Kopyala**' yı seçin. Bu, Özet Görünüm verilerini Pano 'ya HTML biçimi olarak işler.

4. Microsoft Word, özet görünümü verilerini istenen konuma yapıştırın.

5. Artık, raporlama ihtiyaçlarınızı karşılamak için kopyalanmış içeriğin yönlerini değiştirebilir, biçimlendirebilir ve silebilirsiniz.

## <a name="copy-graph-view-data"></a>Grafik görünümü verilerini Kopyala

1. **Yük test sonuçları**, grafik görünümü şu anda görüntülenmiyorsa, araç çubuğunda **grafikler** ' i seçin.

2. Seçim aşağıdaki çizimde gösterildiği gibi Microsoft Word belgenize kopyalamak istediğiniz belirli grafiği yakınlaştırın. Daha fazla bilgi için bkz. [nasıl yapılır: grafiğin bir bölgesini yakınlaştırma](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md).

     ![Graph görünümü yakınlaştırma denetimi](../test/media/ltest_zoomcontrol.png)

3. Microsoft Word belgenize kopyalamak istediğiniz grafikte, sağ tıklayıp **kopyala**' yı seçin.

4. Microsoft Word, grafiği ve ilişkili tablo verilerini istenen konuma yapıştırın.

    > [!WARNING]
    > Grafiği uzak bir masaüstünden kopyalayamazsınız ve grafik görüntüsü değil yalnızca grafikle ilişkili tablo bilgileri kopyalanacağından başka bir makineye yapıştıramazsınız. Graf görüntüsü, kopyalandığı makinedeki geçici dizinde depolanır ve ikinci makine o dizine başvuramaz.

## <a name="see-also"></a>Ayrıca bkz.

- [Test karşılaştırmaları veya eğilim analizi için yük testi sonuçlarını raporla](../test/compare-load-test-results.md)
- [Nasıl yapılır: Microsoft Excel kullanarak yük testi performans raporları oluşturma](../test/how-to-create-load-test-performance-reports-using-microsoft-excel.md)
