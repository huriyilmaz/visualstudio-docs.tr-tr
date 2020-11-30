---
title: Yük Testlerini Çözümlemek için Grafik Görünümü Göstergesini Kullanma
description: Seçilen bir grafik için performans sayaçlarıyla ilgili bilgileri görüntüleyen bir gösterge paneli içeren Yük Testi Çözümleyicisinin grafik görünümü hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Load Test Analyzer, graphs view legend
- load tests, graphs view legend
ms.assetid: 0f6ba8e4-1343-419c-8a9f-240cf50efed7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 25200b691e0bebf2e3bd1c6252efb371ed9caeb2
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96330075"
---
# <a name="use-the-graphs-view-legend-to-analyze-load-tests"></a>Yük testlerini çözümlemek için grafik görünümü göstergesini kullanın

Yük Testi Çözümleyicisi 'nin grafik görünümü, seçili grafik ile ilişkili her performans sayacı için bilgileri görüntüleyen bir gösterge paneli içerir.

![Grafik görünümü göstergesi](../test/media/load_viewlegend.png)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Aşağıdaki bilgiler gösterge içinde bulunur:

- **Grafikte göster:** Grafik üzerinde **Kullanıcı yükleme** veya **hatalar/sn** gibi belirli bir sayaca ait çizginin çizilip çizilmeyeceğini belirtmek için onay kutularını kullanın. Çizginin grafikte çizilmesini istiyorsanız onay kutusunu işaretleyin. Çizim çizgisini grafikten kaldırmak için onay kutusunu temizleyin. Bir çizim çizgisi kaldırıldığında, sayacın istatistikleri göstergede görüntülenmeye devam eder.

- **Aralık:** Bu sütun, performans sayacının y ekseni aralığını görüntüler. Varsayılan olarak, bu değer örnek veri değişikliği aralığı olarak otomatik olarak ayarlar. Otomatik olarak ayarlanmış bir Aralık, her zaman 10 ' un en büyük değerden sonraki kuvveti olacaktır; Bu, 10 ' un negatif üslerini içerir. Grafik, her biri farklı aralığa sahip çeşitli sayaçlar içerebilir. Bu nedenle, y ekseni belirli bir aralıkla etiketlenemez, ancak bunun yerine her sayaç için toplam aralığın yüzdesini temsil eden 0-100 değerleriyle etiketlidir. Örneğin, 1000 aralığına sahip bir sayaç için y ekseninde 60 veri noktası sayaç için bir 600 değerine karşılık gelir.

    > [!NOTE]
    > Aralığı belirli bir değere kilitleyerek otomatik Aralık değer ayarlamayı devre dışı bırakabilirsiniz. Aralık kilitlendiğinde, aralığı aşan tüm değerler grafiğin en üstünde belirttiğiniz en büyük değer olarak görüntülenir. Aralığı belirli bir değerde kilitlemek için **Çizim seçenekleri** iletişim kutusunu kullanın.

- **Sayaç:** **Sayaç**, **örnek**, **Kategori** ve **bilgisayar** adlı dört sütun, performans sayacını benzersiz şekilde tanımlar.

- **Renk:** **Renk** sütunu, performans sayacı için çizilen çizginin rengini ve çizgi stilini gösterir. Grafikteki bir performans sayacının rengini veya çizgi stilini değiştirmek için **Çizim seçenekleri** iletişim kutusunu kullanın. **Çizim seçenekleri** iletişim kutusu, göstergenin kısayol menüsünden kullanılabilir.

- **İstatistikler:** **Min**, **Max**, **AVG** ve **Last** sütunları, performans sayacı için ilgili istatistikleri gösterir. Bu değerler, grafiğin görünür bölgesinde görüntülenen verilere karşılık gelir. Örneğin, bir çalıştırmanın bir bölgesine yakınlaştırırsanız, gösterge istatistikleri yalnızca yakınlaştırılmış alanın değerlerini yansıtır. "Son" sütun, en son tamamlanan Örnekleme aralığındaki performans sayacının değeridir.

    > [!NOTE]
    > Son sütun, yük testi çalışırken yalnızca Yük Testi Çözümleyicisi 'nin göstergesinde görüntülenir.

     Daha fazla bilgi için bkz. [nasıl yapılır: grafiğin bir bölgesini yakınlaştırma](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md).

Göstergedeki bir öğenin seçilmesi şunları yapar:

- Öğenin hem göstergeden hem de grafikten kaldırılmasına izin verir. Öğeye sağ tıklayın ve **Sil**' i seçin ya da **Sil** tuşuna basın.

- Grafikteki çizili çizgiyi vurgular.

- Veri kılavuzunun seçili öğe için verileri görüntülemesine neden olur.

- Sayacın **Çizim seçenekleri** iletişim kutusuna erişmenizi sağlar.

> [!TIP]
> **Yük Testi Çözümleyicisi** araç çubuğunda **grafik seçenekleri açılan** düğmesini kullanabilir ve grafik görünümüyle ilişkili **gösterge** panelini göstermek veya gizlemek için **Göstergeyi Göster** ' i seçebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: grafiğin bir bölgesine yakınlaştırma](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md)
- [Grafik görünümünde Yük testi sonuçlarını çözümleme](../test/analyze-load-test-results-in-the-graphs-view.md)
