---
title: Yük Testlerini Çözümlemek için Grafik Görünümü Göstergesini Kullanma
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Load Test Analyzer, graphs view legend
- load tests, graphs view legend
ms.assetid: 0f6ba8e4-1343-419c-8a9f-240cf50efed7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1455c67c3cb6d8dc99aeab91a7bfa63cce009c51
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590806"
---
# <a name="use-the-graphs-view-legend-to-analyze-load-tests"></a>Yük testlerini analiz etmek için Grafikler görünüm göstergesini kullanma

Yük Testi Çözümleyicisinin Grafikler görünümü, şu anda seçili grafikle ilişkili her performans sayacı için bilgi görüntüleyen bir gösterge paneli içerir.

![Grafikler görünüm göstergesi](../test/media/load_viewlegend.png)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Aşağıdaki bilgiler gösterge içinde yer almaktadır:

- **Grafikte göster:** **Kullanıcı yükü** veya **Hatalar/Sn**gibi belirli bir sayaç için satırın grafikte çizilip çizilemediğini belirtmek için onay kutularını kullanın. Çizginin grafikte çizilmesini istiyorsanız bir onay kutusu seçin. Çizim satırını grafikten kaldırmak için bir onay kutusunu temizleyin. Bir çizim satırı kaldırıldığında, sayaç istatistikleri göstergede görüntüalmaya devam edin.

- **Aralık:** Bu sütun, performans sayacının y ekseni aralığını görüntüler. Varsayılan olarak, örnek veri aralığı değiştikçe bu değer otomatik olarak ayarlanır. Otomatik olarak ayarlanmış bir aralık her zaman Max değerinden 10 daha büyük bir sonraki güç olacaktır; bu on olumsuz güçler içerir. Grafik, her biri farklı bir aralıkta olan çeşitli sayaçlar içerebilir. Bu nedenle, y ekseni belirli bir aralıkla etiketlenmez, ancak bunun yerine her sayaç için toplam aralığın yüzdesini temsil eden 0-100 değerleri ile etiketlenir. Örneğin, 1000 aralığı olan bir sayaç için, y ekseninde 60'lık bir veri noktası sayaç için 600 değerine karşılık gelir.

    > [!NOTE]
    > Aralığı belirli bir değere kilitleyerek otomatik aralık değeri ayarını kapatabilirsiniz. Aralık kilitlendiğinde, aralığı aşan değerler grafiğin üst kısmında belirttiğiniz en yüksek değer olarak görüntülenir. Aralığı belirli bir değerde kilitlemek için **Çizim Seçenekleri** iletişim kutusunu kullanın.

- **Sayaç:** **Sayaç,** **Örnek,** **Kategori**ve **Bilgisayar** adlı dört sütun birlikte performans sayacını benzersiz olarak tanımlar.

- **Renk:** **Renk** sütunu, performans sayacı için çizilen çizginin rengini ve çizgi stilini gösterir. Grafikteki performans sayacının rengini veya satır stilini değiştirmek için **Çizim Seçenekleri** iletişim kutusunu kullanın. **Çizim Seçenekleri** iletişim kutusu, göstergenin kısayol menüsünden kullanılabilir.

- **İstatistikler:** **Min**, **Max**, **Avg** ve **Son** sütunlar performans sayacı için ilgili istatistikleri gösterir. Bu değerler, grafiğin görünür bölgesinde görüntülenen verilere karşılık gelir. Örneğin, bir çalışma bölgesine yakınlaştırırsanız, gösterge istatistikleri yalnızca yakınlaştırılmış alan için değerleri yansıtır. "Son" sütunu, en son tamamlanan örnekleme aralığındaki performans sayacının değeridir.

    > [!NOTE]
    > Son sütun yalnızca Yük Testi Çözümleyicisi'nin Göstergesi'nde yük testi çalışırken görüntülenir.

     Daha fazla bilgi için [bkz: Grafiğin bir bölgesini yakınlaştırın.](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md)

Göstergede bir öğe seçmek aşağıdakileri yapar:

- Öğenin hem göstergeden hem de grafikten kaldırılmasını sağlar. Öğeyi sağ tıklatın ve **Sil'i**seçin veya **Sil** tuşuna basın.

- Grafikte çizilen çizgiyi vurgular.

- Veri ızgarasının seçili öğenin verilerini görüntülemesine neden olur.

- Sayaç için **Çizim Seçenekleri** iletişim kutusuna erişmenizi sağlar.

> [!TIP]
> **Yük Testi Çözümleyici** araç çubuğunda **Grafik Seçenekleri açılır** düğmesini kullanabilir ve grafik görünümüyle ilişkili **Gösterge** panelini göstermek veya gizlemek için **Göstergegöster'i** seçebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapilir: Grafiğin bir bölgesini yakınlaştırın](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md)
- [Grafikler görünümünde yük testi sonuçlarını analiz edin](../test/analyze-load-test-results-in-the-graphs-view.md)
