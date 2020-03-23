---
title: Yük testi sonuç grafiklerini yakınlaştırma
ms.date: 10/19/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.monitor.graphzoom
helpviewer_keywords:
- graphs, analyzing load tests
- load tests, zooming with graphs
ms.assetid: 729b4c30-4bc3-4698-91b3-17a676897443
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a22f1a9b6aa772224b217b5de4136687df1462a1
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75594376"
---
# <a name="how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results"></a>Nasıl yapilir: Yük testi sonuçlarında grafiğin bir bölgesini yakınlaştırın

Yükleme testi tamamlandıktan sonra, yakınlaştırma ve grafiğin bir bölgesine kaydırmak için yakınlaştırma çubuklarını kullanabilirsiniz. Yakınlaştırarak, bir yük testi sırasında oluşturulan verileri daha ince ayrıntılarla inceleyebilirsiniz.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Yakınlaştırma, yalnızca çalışan bir testin sonuçlarını gözlemlerken değil, tamamlanmış bir yük testinin sonucunu analiz ettiğinizde kullanılabilir.

Yakınlaştırma modunda bir yük testi sonucunu görüntülediğinizde, yakınlaştırma denetimi yalnızca **Yük Testi Çözümleyicisi'nde** görünür. Bir yük testi tamamlandığında veya daha önce çalıştırılan bir yük testi yüklendiğinde Grafik görünümünde yakınlaştırma modu oluşturulur. Araç çubuğundaki **Yakınlaştırma Denetimlerini Göster'i** kullanarak grafiklerdeki yakınlaştırma denetimlerini gösterebilir veya gizleyebilirsiniz.

**Yatay x ekseni yakınlaştırma,** yük testi sırasında belirli zaman periyotlarını analiz etmek için ayarlanabilir. **Dikey y ekseni yakınlaştırma,** grafikte yer alan sayaçların belirli değer aralıklarını çözümlemek için ayarlanabilir.

Hem **yatay zaman çizelgesi** hem de **dikey değer aralığı** yakınlaştırma kontrolleri fare kullanılarak ayarlanabilir. **Yatay zaman çizelgesi denetimi** de sol ve sağ ok tuşları kullanılarak ayarlanabilir. Yakınlaştırma denetimini ayarlamak için ok tuşlarını kullanarak, windows aralığını bir seferde 1 örnekleme aralığına göre ayarlayabilirsiniz. **Shift** ve ok tuşlarını kullanarak 10 örnekleme aralıkları ayarlamaları yapar.

Ok tuşunu kullanarak yakınlaştırma denetimini ayarlamak için, önce **Sekme** tuşunu kullanarak yakınlaştırma denetimine odaklanın. Sol kaydırıcı odaklandığında, ok tuşları yakınlaştırma penceresinin başlangıç sınırını 1 aralık sola veya sağa hareket ettirecektir. Odak merkezi kaydırıcıüzerindeyken, yakınlaştırma penceresinin boyutunu değiştirmeden sola veya sağ 1 örnekleme aralığını kaydırmak için ok tuşlarını kullanabilirsiniz. Ve son olarak, sağ taraftakaydırıcı hareket eder, uzlaştırma penceresinin sonundaki aralığı 1 örnekleme aralığıyla uzatır veya azaltır.

Tam zaman çizelgesi ve değer aralıklarını göstermek için yatay ve dikey yakınlaştırma denetimlerini döndürmek için, Grafikteki açılır menüde **Yatay'ı Uzaklaştır** seçeneğini, Dikey **Ilüğü Uzaklaştır** seçeneğini veya **UzaklaştırmaYı Uzaklaştır** seçeneğini kullanabilirsiniz.

> [!TIP]
> Otomatik yatay yakınlaştırma senkronizasyonunu açmak veya kapatmak için araç çubuğunda **Yatay Yakınlaştırma Denetimlerini Senkronize** Etme'yi kullanabilirsiniz. Senkronizasyon yapılırken, grafiğe uyguladığınız herhangi bir yakınlaştırma Grafikler görünümündeki diğer grafiklere de uygulanır.

![Grafik görünümü yakınlaştırma denetimi](../test/media/ltest_zoomcontrol.png)

Önceki resimde, Test grafiği **altındaki Sistem** eşik sorunlarını araştırmak için yakınlaştırılmıştı. Eşik ihlalleri, araç çubuğundaki **Grafik Seçenekleri** açılır tarafından **Grafikte Eşik İhlallerini Göster** kullanılarak etkinleştirilmiştir.

Daha fazla bilgi için bkz: [Grafikler görünümünde yük testi sonuçlarını analiz](../test/analyze-load-test-results-in-the-graphs-view.md)et.

## <a name="display-graphs"></a>Grafik leri görüntüleme

Yakınlaştırarak veya kaydırarak veya kaydırarak grafiğin ekranını değiştirmeden önce grafikleri görüntülemek için bu yordamı izleyin.

Grafikleri görüntülemek için:

1. Tamamlanana kadar bir yük testi çalıştırın.

2. Yük testi çalışmasının sonunda, yük testi sonuçları deposundan sonuçları görüntüleme hakkında soru soran iletişim kutusunda **Evet'i** seçin.

     \-veya -

     Daha önce çalıştırılanan bir yük testinin ayrıntılarını görüntüleyin. Daha fazla bilgi için [bkz: Çözümleme için yük testi sonuçlarına erişin.](../test/how-to-access-load-test-results-for-analysis.md)

3. Grafikleriniz görüntülenmiyorsa **Grafikler'i** seçin.

4. Yakınlaştırma çubukları görüntülenmiyorsa, **Yakınlaştırma Denetimlerini Göster'i**seçin.

     Her grafik için iki yakınlaştırma çubuğu mevcuttur. Dikey ölçeği kontrol eden yakınlaştırma çubuğu grafiğin solunda görünür. Yatay ölçeği kontrol eden yakınlaştırma çubuğu grafiğin altında görünür.

     Her yakınlaştırma çubuğunun iki tutamacı vardır. Tutamaç, yakınlaştırma çubuğunun her iki ucundaki dikdörtgen bir alandır.

## <a name="zoom-and-scroll"></a>Yakınlaştırma ve kaydırma

Birden çok grafiğiniz görüntülendiğinde, bunları eşitlenmiş olarak tutabilirsiniz, böylece yük testi çalışmasının aynı bölümünü görüntüleyebilirsiniz.

### <a name="to-synchronize-zooming-and-scrolling"></a>Yakınlaştırma ve kaydırmayı senkronize etmek için

1. Yük **Testi Çözümleyicisi'nde,** **Yatay Yakınlaştırma Denetimlerini Senkronize Et'i**seçin.

     Yatay **Yakınlaştırma Denetimlerini Eşitle** düğmesi seçildiğinde, tek bir grafiğin zaman ölçeğini yakınlaştırır ve kaydırır, diğer grafiklerin zaman ölçeğini de yakınlaştırır ve kaydırır.

2. Yine, **Yatay Yakınlaştırma Denetimlerini Eşitle'yi**seçin.

     Yatay **Yakınlaştırma Denetimlerini Eşitle** düğmesi seçilmediğinde, tek bir grafiğin zaman ölçeğini yakınlaştırma ve kaydırma yalnızca bu grafiği etkiler.

### <a name="to-zoom-and-scroll-to-a-region-of-the-graph"></a>Grafiğin bir bölgesini yakınlaştırmak ve kaydırmak için

1. Grafiğin altındaki yakınlaştırma çubuğunda sol tarafı sağa sürükleyin.

     Bu, test çalışmasının ikinci bölümünü yakınlaştırır. Benzer şekilde, sağ tarafı tutamacı sola sürükleme, test çalışmasının önceki bölümlerinde yakınlaştırır.

2. Belirli bir alanı yakınlaştırmak için her iki tutamacı da grafiğin ortasına doğru kaydırın.

     İki tutamaç birbirine ne kadar yakınsa, yük testinin daha kısa ve ince kesimlerini görüntülemek için o kadar yakınlaştırırsınız.

     Yakınlaştırma çubuğunun orta kısmını seçin ve ardından onu sürükleyerek yük testinde belirli bir noktaya kaydırın.

### <a name="to-zoom-to-a-region-of-the-graph-by-choosing-and-dragging"></a>Seçip sürükleyerek grafiğin belirli bir bölgesine yakınlaştırmak için

1. Yakınlaştırma alanının bir ucunda bulunan bir grafiği seçin.

2. Fare işaretçisini yakınlaştırma alanının diğer ucuna sürükleyin.

3. Fare düğmesini bırakın.

    Bu, seçip sürükleyerek tanımladığınız alanı büyütür.

   Aşağıdaki yordam, yakınlaştırma çubuğunun uçlarını ayarlamak zorunda kalmadan nasıl hızla uzaklaştırmak için açıklanır.

### <a name="to-zoom-out"></a>Uzaklaştırmak için

1. Yakınlaştırılmış bir grafiği sağ tıklatın.

2. Kısayol menüsünde **Yatay'ı Uzaklaştır'ı**seçin.

     Bu, yük testi çalışmasının tüm süresini göstermek için uzaklaştırır.

## <a name="see-also"></a>Ayrıca bkz.

- [Grafikler görünümünde yük testi sonuçlarını analiz edin](../test/analyze-load-test-results-in-the-graphs-view.md)
- [Yük testi sonuçlarını analiz edin](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Nasıl yapılır: Grafiklerdeki sayaçları ekleme ve silme](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md)
