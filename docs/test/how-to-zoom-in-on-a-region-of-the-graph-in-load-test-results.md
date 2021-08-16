---
title: Yük testi sonuç grafiklerini yakınlaştırma
description: Grafın bir bölgesinde yakınlaştırmak ve kaydırmak için yakınlaştırma çubukları kullanarak yük testi çalıştırması sırasında oluşturulan verileri daha ayrıntılı bir şekilde incelemeyi öğrenin.
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
ms.technology: vs-ide-test
ms.openlocfilehash: ee81f279f82ee4803a5ac188b5d647769f8a148bb6e7a73328f6c36236d6318c
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121366542"
---
# <a name="how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results"></a>Nasıl gösterilir: Yük testi sonuçlarında grafın bir bölgesinde yakınlaştırma

Yük testi tamam olduktan sonra yakınlaştırma çubuklarını kullanarak grafın bir bölgesiyle yakınlaştırabilir ve kaydırabilirsiniz. Yakınlaştırarak, bir yük testi çalıştırması sırasında oluşturulan verileri daha ayrıntılı bir şekilde inceebilirsiniz.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Yakınlaştırma yalnızca tamamlanan bir yük testinin sonuçlarını analiz ederken kullanılabilir, çalışan bir testin sonuçlarını gözlemlerken kullanılamaz.

Yakınlaştırma denetimi, bir yük testi **sonuçlarını yakınlaştırma modunda** görüntüleye yalnızca Yük Testi Çözümleyicisi'ne görünür. Yakınlaştırma modu, Graph testi tamamlandığında veya daha önce çalıştırılan bir yük testi yüklendiğinde yakınlaştırma modu kurulur. Araç çubuğundaki Yakınlaştırma Denetimlerini Göster'i kullanarak graflarda **yakınlaştırma denetimlerini gösterebilir veya** gizleyebilirsiniz.

Yük **testi sırasında belirli zaman** dönemlerini analiz etmek için yatay x ekseni yakınlaştırması ayarlanabilir. Dikey **y ekseni yakınlaştırması,** grafiye dahil edilen sayaçlar için belirli değer aralıklarını analiz etmek için ayarlanabilir.

Hem **yatay zaman** çizelgesi **hem de dikey değer aralığı** yakınlaştırma denetimleri fare kullanılarak ayarlanabilir. Yatay **zaman çizelgesi** denetimi, sol ve sağ ok tuşları kullanılarak da ayarlanabilir. Yakınlaştırma denetiminde ok tuşlarını kullanarak windows aralığını aynı anda 1 örnekleme aralığına ayarlayabilirsiniz. Shift ve **ok** tuşlarını kullanarak 10 örnekleme aralığı ayarlaması yapılır.

Ok tuşunu kullanarak yakınlaştırma denetimi ayarlamak için önce Sekme tuşunu kullanarak yakınlaştırma denetimine **odaklanın.** Sol kaydırıcı odakta olduğunda ok tuşları yakınlaştırma penceresinin başlangıç sınırını 1 aralık sola veya sağa hareket ettirecek. Odak orta kaydırıcıda olduğunda, yakınlaştırma penceresinin boyutunu değiştirmeden yakınlaştırma penceresini sola veya sağ 1 örnekleme aralığına kaydırmak için ok tuşlarını kullanabilirsiniz. Son olarak, sağ taraf kaydırıcı hareket eder, yakınlaştırma penceresinin sonundaki aralığı 1 örnekleme aralığı genişleterek veya azaltarak.

Tam zaman çizelgesini ve değer aralıklarını göstermek üzere yatay ve  dikey yakınlaştırma denetimlerini geri dönmek için  grafın açılır menüsünde Yatay Yakınlaştır seçeneğini, Dikeyi Uzaklaştır seçeneğini veya Her ikisini de Yakınlaştır seçeneğini kullanabilirsiniz. 

> [!TIP]
> Otomatik yatay yakınlaştırma **eşitlemesini açma veya** kapatma için araç çubuğunda Yatay Yakınlaştırma Denetimlerini Eşitle'yi kullanabilirsiniz. Eşitleme açıkken, bir grafiye uygulayan tüm yakınlaştırmalar, Graflar görünümündeki diğer tüm grafiklere de uygulanır.

![Graph yakınlaştırma denetimi görüntüleme](../test/media/ltest_zoomcontrol.png)

Önceki çizimde, Eşik **sorunlarını araştırmak için Test** grafı altındaki Sistem yakınlaştırıldı. Eşik ihlalleri, araç çubuğundaki Graph Seçenekleri açılan **menüsünden** Graph Eşik **İhlallerini** Göster seçeneği kullanılarak etkinleştirildi.

Daha fazla bilgi için [Bkz. Graflar görünümünde yük testi sonuçlarını analiz etme.](../test/analyze-load-test-results-in-the-graphs-view.md)

## <a name="display-graphs"></a>Grafikleri görüntüleme

Yakınlaştırarak veya uzaklaştırarak veya kaydırarak grafın display'ini değiştirmeden önce, grafikleri görüntülemek için bu yordamı izleyin.

Grafikleri görüntülemek için:

1. Tamamlanana kadar bir yük testi çalıştırın.

2. Yük testi çalıştırması sonunda,  yük testi sonuçları deposu sonuçlarını görüntülemeyi soran iletişim kutusunda Evet'i seçin.

     \- veya -

     Daha önce çalıştırılan bir yük testinin ayrıntılarını görüntüleme. Daha fazla bilgi için, [bkz. How to: Access load test results for analysis](../test/how-to-access-load-test-results-for-analysis.md).

3. **Graflar** görüntülenmezse Graflar'ı seçin.

4. Yakınlaştırma çubukları görüntülenlenmiyorsa Yakınlaştırma Denetimlerini **Göster'i seçin.**

     Her grafik için iki yakınlaştırma çubukları mevcuttur. Dikey ölçeği kontrol eden yakınlaştırma çubuğu grafiğin sol tarafından görünür. Yatay ölçeği kontrol eden yakınlaştırma çubuğu grafiğin altında görünür.

     Her yakınlaştırma çubuğunun iki tanıtıcısı vardır. Tutamaç, yakınlaştırma çubuğunun her ucunda dikdörtgen bir alandır.

## <a name="zoom-and-scroll"></a>Yakınlaştırma ve kaydırma

Birden çok grafik görüntülendiğinde, yük testi çalıştırması için aynı bölümü görüntülemeleri için bunları eşitlenmiş durumda tutabilirsiniz.

### <a name="to-synchronize-zooming-and-scrolling"></a>Yakınlaştırma ve kaydırmayı eşitlemek için

1. Yük Testi **Çözümleyicisi'de** Yatay Yakınlaştırma **Denetimlerini Eşitle'yi seçin.**

     Yatay **Yakınlaştırma Denetimlerini** Eşitle düğmesi seçildiğinde, tek bir grafiğin zaman ölçeğini yakınlaştırmak ve kaydırmak, diğer grafiklerin zaman ölçeğini de yakınlaştırıp kaydırabilir.

2. Yine Yatay Yakınlaştırma **Denetimlerini Eşitle'yi seçin.**

     Yatay **Yakınlaştırma Denetimlerini Eşitle** düğmesi seçili değilken, tek bir grafın zaman ölçeğini yakınlaştırmak ve kaydırmak yalnızca bu grafiği etkiler.

### <a name="to-zoom-and-scroll-to-a-region-of-the-graph"></a>Grafiği yakınlaştırmak ve bir bölgeye kaydırmak için

1. Grafın altındaki yakınlaştırma çubuğunda, sol tarafındaki tutamacı sağa sürükleyin.

     Bu, test çalıştırması için ikinci bölümü yakınlaştırıyor. Benzer şekilde, sağ tarafındaki tutamacı sola sürüklemek, test çalıştırması'nın önceki kısımlarında yakınlaştırma sağlar.

2. Belirli bir alanı yakınlaştırmak için her iki tutamacı da grafiğin merkezine doğru kaydırın.

     İki tutamaç birbirine ne kadar yakınsa, yük testinin daha kısa ve daha ince segmentlerini görüntülemek için o kadar yakınlaştırabilirsiniz.

     Yakınlaştırma çubuğunun orta kısmını seçin ve ardından onu sürükleyerek yük testinde belirli bir noktaya kaydırın.

### <a name="to-zoom-to-a-region-of-the-graph-by-choosing-and-dragging"></a>Seçip sürükleyerek grafiğin belirli bir bölgesine yakınlaştırmak için

1. Yakınlaştırma alanının bir ucunda bulunan bir grafiği seçin.

2. Fare işaretçisini yakınlaştırma alanına sürükleyin.

3. Fare düğmesini bırakın.

    Bu, seçip sürükleyerek tanımladığınız alanı büyütür.

   Aşağıdaki yordamda yakınlaştırma çubuğunun uçlarını ayarlamak zorunda kalmadan nasıl hızlı bir şekilde uzaklaştırmak istediğiniz açık edilmektedir.

### <a name="to-zoom-out"></a>Uzaklaştırmak için

1. Yakınlaştırmalı bir grafiye sağ tıklayın.

2. Kısayol menüsünde Yatay **Yakınlaştır'ı seçin.**

     Bu, yük testi çalıştırması süresinin tamamını göstermek için uzaklaştırıyor.

## <a name="see-also"></a>Ayrıca bkz.

- [Graflar görünümünde yük testi sonuçlarını analiz etme](../test/analyze-load-test-results-in-the-graphs-view.md)
- [Yük testi sonuçlarını analiz etme](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Nasıl gösterilir: Graflara sayaç ekleme ve silme](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md)
