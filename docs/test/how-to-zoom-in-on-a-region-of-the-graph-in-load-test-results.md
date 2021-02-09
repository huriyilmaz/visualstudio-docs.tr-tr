---
title: Yük testi sonuç grafiklerini Yakınlaştır
description: Bir yük testi sırasında oluşturulan verileri, yakınlaştırmak ve grafiğin bir bölgesine kaydırmak için yakınlaştırma çubuklarını kullanarak daha ayrıntılı bir şekilde nasıl inceleyeceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
f1_keywords:
- vs.test.load.monitor.graphzoom
helpviewer_keywords:
- graphs, analyzing load tests
- load tests, zooming with graphs
ms.assetid: 729b4c30-4bc3-4698-91b3-17a676897443
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: af780af58e3efa2aff7dc58971bfbbb881967c40
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99879546"
---
# <a name="how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results"></a>Nasıl yapılır: yük testi sonuçlarında grafiğin bir bölgesini yakınlaştırma

Bir yük testi tamamlandıktan sonra yakınlaştırma çubuklarını kullanarak grafiğin bir bölgesine yakınlaştırıp kaydırma yapabilirsiniz. ' İ yakınlaştırarak, yük testi sırasında oluşturulan verileri daha ayrıntılı bir şekilde inceleyebilirsiniz.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Yakınlaştırma yalnızca, tamamlanan bir yük testinin sonucunu analiz ederken, çalışan bir testin sonuçlarını gözlemleyerek değil, kullanılabilir.

Yakınlaştırma denetimi, bir yük testi sonucunu yakınlaştırma modunda görüntülediğinizde yalnızca **Yük Testi Çözümleyicisi** 'nde görünür. Yükleme testi tamamlandığında veya daha önce çalıştırılan bir yük testi yüklendiğinde yakınlaştırma modu grafik görünümünde oluşturulur. Araç çubuğundaki **Yakınlaştırma denetimlerini göster** ' i kullanarak Grafiklerde yakınlaştırma denetimlerini gösterebilir veya gizleyebilirsiniz.

**Yatay x ekseni yakınlaştırması** , yük testi sırasında belirli zaman aralıklarını çözümlemek üzere ayarlanabilir. **Dikey y ekseni yakınlaştırması** , grafiğe dahil edilen sayaçların belirli değer aralıklarını çözümlemek üzere ayarlanabilir.

Hem **Yatay zaman çizelgesi** hem de **Dikey değer aralığı** yakınlaştırma denetimleri, fare kullanılarak ayarlanabilir. **Yatay zaman çizelgesi denetimi** de sol ve sağ ok tuşları kullanılarak ayarlanabilir. Yakınlaştırma denetimini ayarlamak için ok tuşlarını kullanarak, Windows aralığını tek seferde 1 örnekleme aralığına göre ayarlayabilirsiniz. **SHIFT** ve ok tuşlarının kullanılması 10 örnekleme aralığının ayarlamalarını yapar.

Ok tuşunu kullanarak yakınlaştırma denetimini ayarlamak için, önce **Tab** tuşunu kullanarak yakınlaştırma denetimindeki odağı ayarlayın. Sol kaydırıcı odağa sahip olduğunda, ok tuşları yakınlaştırma penceresinin başlangıç sınırını 1 Aralık sola veya sağa taşır. Odak Merkez kaydırıcıdayken, yakınlaştırma penceresinin boyutunu değiştirmeden sola veya sağa 1 örnekleme aralığını kaydırmak için ok tuşlarını kullanabilirsiniz. Son olarak, sağ kenar kaydırıcı, yakınlaştırma penceresinin sonundaki aralığı 1 örnekleme aralığına genişleterek veya azaltarak hareket eder.

Tüm zaman çizelgesini ve değer aralıklarını göstermek üzere yatay ve dikey yakınlaştırma denetimlerini döndürmek için **yatay Yakınlaştır** seçeneğini, **Dikey uzaklaştır** seçeneğini veya grafikteki açılır menüdeki **her iki öğeyi de uzaklaştır** seçeneğini kullanabilirsiniz.

> [!TIP]
> Otomatik yatay yakınlaştırma eşitlemesini açıp kapatmak için araç çubuğundaki **Yatay Yakınlaştırma Denetimlerini Eşitle** ' ye geçebilirsiniz. Eşitlemeyle birlikte, grafik için uyguladığınız tüm yakınlaştırmanın grafikleri görünümündeki diğer grafiklere de uygulanması gerekir.

![Grafik görünümü yakınlaştırma denetimi](../test/media/ltest_zoomcontrol.png)

Önceki çizimde, **Test grafiği altındaki sistem** eşik sorunlarını araştırmak için yakınlaştırıldı. Eşik ihlalleri, araç çubuğunda **grafik seçenekleri** açılır listesinden **Eşik ihlallerini göster** kullanılarak etkinleştirildi.

Daha fazla bilgi için bkz. [Grafik görünümünde Yük testi sonuçlarını çözümleme](../test/analyze-load-test-results-in-the-graphs-view.md).

## <a name="display-graphs"></a>Grafikleri görüntüle

Bir grafiği yakınlaştırarak veya uzaklaştırarak veya kaydırarak ekran görüntüsünü değiştirmeden önce, grafikleri göstermek için bu yordamı izleyin.

Grafikleri göstermek için:

1. Tamamlanana kadar bir yük testi çalıştırın.

2. Yük testi çalıştırmasının sonunda, yük testi sonuçları deposundan sonuçları görüntülemeyi soran iletişim kutusunda **Evet** ' i seçin.

     \- veya

     Daha önce çalıştırılan bir yük testinin ayrıntılarını görüntüleyin. Daha fazla bilgi için bkz. [nasıl yapılır: çözümleme için yük testi sonuçlarına erişme](../test/how-to-access-load-test-results-for-analysis.md).

3. Grafiklerinizin görüntülenmediğini **grafikler** ' i seçin.

4. Yakınlaştırma çubukları görüntülenmiyorsa, **Yakınlaştırma denetimlerini göster**' i seçin.

     Her grafik için iki yakınlaştırma çubuğu bulunur. Dikey ölçeği denetleyen yakınlaştırma çubuğu grafiğin solunda görünür. Yatay ölçeklendirmeyi denetleyen yakınlaştırma çubuğu grafiğin altında görünür.

     Her yakınlaştırma çubuğunun iki tutamacı vardır. Tutamaç, Yakınlaştırma çubuğunun her ucundaki dikdörtgen bir alandır.

## <a name="zoom-and-scroll"></a>Yakınlaştır ve Kaydır

Birden çok grafik görüntülendiğinde, yük testi çalıştırmasının aynı bölümünü görüntülemesi için onları eşitlenmiş halde tutabilirsiniz.

### <a name="to-synchronize-zooming-and-scrolling"></a>Yakınlaştırmayı ve kaydırmayı eşleştirmek için

1. **Yük Testi Çözümleyicisi**'Nde **yatay yakınlaştırma denetimlerini eşitler**' ı seçin.

     **Yatay yakınlaştırma denetimlerini senkronize** et düğmesi seçildiğinde, tek bir grafiğin zaman ölçeğini yakınlaştırmak ve kaydırmak, diğer grafiklerin zaman ölçeğini de büyütür ve kaydırır.

2. Yine, **yatay yakınlaştırma denetimlerini eşitler**' ı seçin.

     **Yatay yakınlaştırma denetimlerini zamanla** düğmesi seçili olmadığında, tek bir grafiğin zaman ölçeğini yakınlaştırmak ve kaydırmak yalnızca o grafiği etkiler.

### <a name="to-zoom-and-scroll-to-a-region-of-the-graph"></a>Grafiğin bir bölgesine yakınlaştırmak ve kaydırmak için

1. Grafik altındaki Yakınlaştırma çubuğunda, sol taraftaki tutamacı sağa sürükleyin.

     Bu, Test çalıştırmasının ikinci bölümünde yakınlaştırılır. Benzer şekilde, sağ taraftaki tutamacı sola sürükleyerek Test çalıştırmasının önceki bölümlerinde yakınlaştırın.

2. Belirli bir alanı yakınlaştırmak için her iki tutamacı de grafiğin ortasına kaydırın.

     İki tutamacı birbirlerine yaklaştırırsanız, yük testinin daha kısa ve daha iyi segmentlerini göstermek için daha fazla yakınlaştırmanız gerekir.

     Yakınlaştırma çubuğunun orta kısmını seçin ve ardından onu sürükleyerek yük testinde belirli bir noktaya kaydırın.

### <a name="to-zoom-to-a-region-of-the-graph-by-choosing-and-dragging"></a>Seçip sürükleyerek grafiğin belirli bir bölgesine yakınlaştırmak için

1. Yakınlaştırma alanının bir ucunda bulunan bir grafiği seçin.

2. Fare işaretçisini yakınlaştırma alanının diğer ucuna sürükleyin.

3. Fare düğmesini bırakın.

    Bu, seçip sürükleyerek tanımladığınız alanı büyütür.

   Aşağıdaki yordamda Yakınlaştırma çubuğunun uçlarını ayarlamak zorunda kalmadan hızlı bir şekilde yakınlaştırmanın nasıl yapılacağı açıklanmaktadır.

### <a name="to-zoom-out"></a>Uzaklaştırmak için

1. Yakınlaştırılmış bir grafiğe sağ tıklayın.

2. Kısayol menüsünde **Yatay Uzaklaştır**' ı seçin.

     Bu, yük testi çalıştırmasının tüm süresini göstermek için uzaklaşır.

## <a name="see-also"></a>Ayrıca bkz.

- [Grafik görünümünde Yük testi sonuçlarını çözümleme](../test/analyze-load-test-results-in-the-graphs-view.md)
- [Yük testi sonuçlarını çözümle](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Nasıl yapılır: grafiklerde sayaç ekleme ve silme](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md)
