---
title: Yük Testlerini Çözümlemek için Grafik Görünümü Göstergesini Kullanma
description: Seçilen graf için performans sayaçları bilgilerini görüntüleyen bir gösterge paneli içeren Yük Testi Çözümleyicisi'nin Graflar görünümü hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Load Test Analyzer, graphs view legend
- load tests, graphs view legend
ms.assetid: 0f6ba8e4-1343-419c-8a9f-240cf50efed7
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: da9b45ce5406ed0a686a4837b9a605145c810ca0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122100341"
---
# <a name="use-the-graphs-view-legend-to-analyze-load-tests"></a>Yük testlerini analiz etmek için Graflar görünüm göstergesini kullanma

Yük Testi Çözümleyicisi'nin Graflar görünümü, seçili olan grafikle ilişkili her bir performans sayacına ilişkin bilgileri görüntüleyen bir gösterge paneli içerir.

![Graflar görünüm gösterge](../test/media/load_viewlegend.png)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Aşağıdaki bilgiler açıklamanın içinde yer alan bilgilerdir:

- **Grafikte göster:** Kullanıcı yükü veya **Hatalar/Sn** gibi belirli bir  sayacın çizgisinin grafikte çizip çizil olmadığını belirtmek için onay kutularını kullanın. Çizginin grafikte çizilen bir onay kutusu seçin. Grafikten çizim çizgilerini kaldırmak için bir onay kutusunun işaretini kaldırın. Çizim çizgisi kaldırıldığı zaman sayacın istatistikleri göstergede görüntülenmeye devam eder.

- **Aralık:** Bu sütunda performans sayacının y ekseni aralığı görüntülenir. Varsayılan olarak, örnek veri aralığı değiştiksinde bu değer otomatik olarak ayarlanır. Otomatik olarak ayarlanmış bir aralık her zaman En yüksek değerden sonraki 10 güç olur; Bu on negatif gücü içerir. Graf, her biri farklı bir aralıkta olan çeşitli sayaçlar içerebilir. Bu nedenle y ekseni belirli bir aralıkla etiketlenmiş değil, bunun yerine her sayaç için toplam aralığın yüzdesini temsil eden 0-100 arasında değerlerle etiketlenmiş. Örneğin, 1000 aralığına sahip bir sayaç için y ekseninde 60 olan bir veri noktası, sayaç için 600 değerine karşılık gelen bir değerdir.

    > [!NOTE]
    > Aralığı belirli bir değere kilitleyerek otomatik aralık değer ayarlamasını kapatmış olursanız. Aralık kilitliyken, aralığı aşan tüm değerler grafiğin en üstünde belirttiğiniz maksimum değer olarak görüntülenir. Aralığı **belirli bir değerde** kilitlemek için Çizim Seçenekleri iletişim kutusunu kullanın.

- **Sayaç:** Counter , **Instance** , **Category** ve Computer adlı **dört sütun,** performans sayacını benzersiz bir şekilde tanımladı.

- **Renk:** Color **sütunu,** performans sayacı için çizilen çizginin rengini ve çizgi stilini gösterir. Grafikte **bir performans** sayacının rengini veya çizgi stilini değiştirmek için Çizim Seçenekleri iletişim kutusunu kullanın. Çizim **Seçenekleri** iletişim kutusu, göstergenin kısayol menüsünden kullanılabilir.

- **İstatistikler:** Min , **Max**, **Avg** ve **Last sütunları** performans sayacı için ilgili istatistikleri gösterir. Bu değerler grafiğin görünür bölgesinde görüntülenen verilere karşılık gelir. Örneğin, bir çalıştırmanın bir bölgesiyle yakınlaştırsanız gösterge istatistikleri yalnızca yakınlaştırılmış alan için değerleri yansıtacak. "Son" sütunu, en son tamamlanan örnekleme aralığındaki performans sayacının değeridir.

    > [!NOTE]
    > Son sütun yalnızca yük testi çalışırken Yük Testi Çözümleyicisi'nin Göstergesinde görüntülenir.

     Daha fazla bilgi [için, bkz. How to: Zoom in a region of the graph](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md).

Göstergede bir öğe seçmek şunları yapar:

- Öğenin hem göstergeden hem de grafikten kaldırılmasına izin verir. Öğeye sağ tıklayın ve Sil'i **seçin** veya Sil **tuşuna** basın.

- Grafikte çizilen satırı vurgular.

- Veri kılavuzunda seçilen öğenin verileri görüntülemesine neden olur.

- Sayacın Çizim **Seçenekleri iletişim** kutusuna erişmenizi sağlar.

> [!TIP]
> Yük Testi **Graph** araç çubuğundaki Graph Seçenekleri açılan düğmesini kullanabilir  ve grafik görünümüyle ilişkili Gösterge panelini göstermek veya gizlemek için Göstergeyi Göster'i seçebilirsiniz.  

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl gösterilir: Grafın bir bölgesi üzerinde yakınlaştırma](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md)
- [Graflar görünümünde yük testi sonuçlarını analiz etme](../test/analyze-load-test-results-in-the-graphs-view.md)
