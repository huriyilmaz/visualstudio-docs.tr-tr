---
title: Microsoft Word'u Kullanarak Yük Testi Performans Raporu Oluşturma
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, reporting
- load tests, creating Word reports
ms.assetid: 3b864c75-2699-48c1-a2b4-9651f108c267
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c3deee8d35f06e50dbe22001e8a2fa81b41563e0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76113436"
---
# <a name="how-to-manually-create-a-load-test-performance-report-using-microsoft-word"></a>Nasıl yapIlir: Microsoft Word'ü kullanarak bir yük testi performans raporu el ile oluşturma

Yük Testi Sonuçları özet görünümünden ve grafik görünümünden verileri kopyalayıp yapıştırarak Microsoft Word yükleme testi raporlarını el ile oluşturabilirsiniz. Özet görünümünde ve grafik görünümünde sunulan veriler kopyalandığında HTML biçiminde uygulanır.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!TIP]
> Tablolar görünümünden ve ekran görüntülerinden microsoft word'e düz metin kopyalayabilirsiniz, ancak HTML biçiminde uygulanmaz ve ek biçimlendirme ve düzenleme gerektirir.

> [!TIP]
> Ayrıca, düzenli Microsoft Excel raporları da otomatik olarak oluşturabilirsiniz. Daha fazla bilgi için [bkz: Microsoft Excel'i kullanarak yük testi performans raporları oluşturun.](../test/how-to-create-load-test-performance-reports-using-microsoft-excel.md)

## <a name="copy-summary-view-data"></a>Özet görünüm verilerini kopyalama

1. Load **Test Sonuçları'nda**, özet görünümü şu anda görüntülenmiyorsa, araç çubuğunda **Özet'i** tıklatın.

2. Özet görünümünde, sağ tıklayın ve **Tümünü Seç'i**seçin.

3. Özet görünümünde, sağ tıklatın ve **Kopyala'yı**seçin. Bu, özet görünüm verilerini panoya HTML biçimi olarak işler.

4. Microsoft Word'de, özet görünüm verilerini istenilen konuma yapıştırın.

5. Artık raporlama ihtiyaçlarınızı karşılamak için kopyalanan içeriğin yönlerini değiştirebilir, biçimlendirebilir ve silebilirsiniz.

## <a name="copy-graph-view-data"></a>Grafik görünümü verilerini kopyalama

1. Yük **Testi Sonuçlarında,** grafik görünümü şu anda görüntülenmiyorsa, araç çubuğundaki **Grafikler'i** seçin.

2. (İsteğe bağlı) Aşağıdaki resimde gösterildiği gibi, Microsoft Word belgenize kopyalamak istediğiniz belirli grafiği yakınlaştırın. Daha fazla bilgi için [bkz: Grafiğin bir bölgesini yakınlaştırın.](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md)

     ![Grafik görünümü yakınlaştırma denetimi](../test/media/ltest_zoomcontrol.png)

3. Microsoft Word belgenize kopyalamak istediğiniz grafikte, Sağ tıklatın ve **Kopyala'yı**seçin.

4. Microsoft Word'de, grafiği ve ilişkili tablo verilerini istenilen konuma yapıştırın.

    > [!WARNING]
    > Grafiği uzak bir masaüstünden kopyalayıp başka bir makineye yapıştıramazsınız, çünkü grafik görüntüsüyle değil, yalnızca grafikle ilişkili tablo bilgileri kopyalanır. Graf görüntüsü, kopyalandığı makinedeki geçici dizinde depolanır ve ikinci makine o dizine başvuramaz.

## <a name="see-also"></a>Ayrıca bkz.

- [Test karşılaştırmaları veya eğilim analizi için rapor yükü testleri sonuçları](../test/compare-load-test-results.md)
- [Nasıl? Microsoft Excel'i kullanarak yük testi performans raporları oluşturma](../test/how-to-create-load-test-performance-reports-using-microsoft-excel.md)
