---
title: 'Nasıl Yapılır: Geometri Tabanlı Gradyan Gölgelendirici Oluşturma'
description: gölgelendirici tasarımcısını ve yönlendirilen Graph gölgelendirici dilini kullanarak sabit bir RGB renk değerini ölçeklendirilen geometri tabanlı bir gradyan gölgelendiricisi oluşturma hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 4b204405-ba95-4c5e-bd51-ec033a3ebfb6
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-designers
ms.workload:
- multiple
ms.openlocfilehash: 4abfa5057c0b9f634f7524fd8421ae44e24fbe0896a520dd65902699881c0299
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121263328"
---
# <a name="how-to-create-a-geometry-based-gradient-shader"></a>Nasıl yapılır: Geometri tabanlı gradyan gölgelendirici oluşturma

bu makalede, geometri tabanlı bir gradyan gölgelendirici oluşturmak için gölgelendirici tasarımcısının ve yönlendirilmiş Graph gölgelendirici dilinin nasıl kullanılacağı gösterilmektedir. Bu gölgelendirici, bir sabit RGB renk değerini, dünya alanındaki bir nesne noktasının yüksekliğine göre ölçeklendirir.

## <a name="create-a-geometry-based-gradient-shader"></a>Geometri tabanlı gradyan gölgelendirici oluşturma

Pikselin konumunu gölgelendiricinize ekleyerek geometri temelli bir gölgelendirici uygulayabilirsiniz. Gölgeleme dillerinde, bir piksel, 2B ekranda yalnızca kendi renginden ve konumlarından daha fazla bilgi içerir. Bazı sistemlerde *parça* olarak bilinen bir piksel, bir piksele karşılık gelen yüzeyi tanımlayan bir değerler koleksiyonudur. Bu belgede açıklanan gölgelendirici, parçanın nihai çıkış rengini etkilemek için dünya alanındaki bir 3B nesnenin her bir pikselin yüksekliğini kullanır.

Başlamadan önce, **Özellikler** penceresinin ve **araç kutusunun** görüntülendiğinden emin olun.

1. Çalışmak için bir DGSL gölgelendiricisi oluşturun. Projenize bir DGSL gölgelendiricisi ekleme hakkında daha fazla bilgi için bkz. [gölgelendirici tasarımcısında](../designers/shader-designer.md)Başlarken bölümü.

2. **Son renk** düğümündeki **nokta rengi** düğümünün bağlantısını kesin. **Nokta rengi** düğümünün **RGB** terminalini seçin ve ardından **Bağlantıları Kes**' i seçin. Bu, bir sonraki adımda eklenen düğüm için yer açar.

3. Grafiğe **çarpma** düğümü ekleyin. **Araç kutusunda**, **matematik** altında **çarp** ' ı seçin ve tasarım yüzeyine taşıyın.

4. Grafiğe bir **maske vektör** düğümü ekleyin. **Araç kutusu**' nda, **yardımcı program** altında **maske vektörü** ' nı seçin ve tasarım yüzeyine taşıyın.

5. **Maske vektör** düğümü için maske değerlerini belirtin. **Seç** modunda, **maske vektörü** düğümünü seçin ve ardından **Özellikler** penceresinde **yeşil/Y** özelliğini **doğru** olarak ayarlayın ve ardından **kırmızı/X**, **mavi/Z** ve **Alfa/W** özelliklerini **yanlış** olarak ayarlayın. Bu örnekte, **kırmızı/X**, **yeşil/Y** ve **mavi/Z** özellikleri **Dünya konumu** düğümünün X, Y ve Z bileşenlerine karşılık gelir ve **Alfa/W** kullanılmıyor. Yalnızca **yeşil/Y** **doğru** olarak ayarlandığı için, yalnızca giriş vektörünün Y bileşeni maskelendikten sonra kalır.

6. Grafiğe bir **Dünya konumu** düğümü ekleyin. **Araç kutusunda**, **sabitler** altında **Dünya konumu** ' nu seçin ve tasarım yüzeyine taşıyın.

7. Parçanın dünya alanı konumunu maskeleyin. **Seç** modunda, **World Position** düğümünün **Çıkış** terminalini **maske vektör** düğümünün **vektör** terminaline taşıyın. Bu bağlantı, parçaların konumunu x ve z bileşenlerini yok saymak için maskeler.

8. RGB renk sabitini, maskelenmiş dünya alanı konumuna göre çarpın. **Nokta rengi** düğümünün **RGB** terminalini **çarp** düğümünün **Y** terminaline taşıyın ve ardından **maske vektörü** düğümünün **Çıkış** terminalini **çarpma** düğümünün **X** terminaline taşıyın. Bu bağlantı, renk değerini, dünya alanındaki pikselin yüksekliğine ölçeklendirir.

9. ölçeklendirilmiş renk değerini son renge Bağlan. **Çarp** düğümünün **Çıkış** terminalini **son renk** düğümünün **RGB** terminaline taşıyın.

Aşağıdaki çizimde, tamamlanmış gölgelendirici grafiği ve bir sphere öğesine uygulanan gölgelendirici önizlemesi gösterilmektedir.

> [!NOTE]
> Bu çizimde, gölgelendirici efektini daha iyi göstermek için turuncu bir renk belirtilmiştir, ancak önizleme şekli dünya alanında bir konum olmadığından, gölgelendirici, gölgelendirici tasarımcısında tam olarak önizlenemez. Tam efekti göstermek için gölgelendirici gerçek bir sahnede önizlenmelidir.

![Gölgelendirici Grafiği ve efektinin önizlemesi](../designers/media/digit-gradient-effect-graph.png)

Bazı biçimler bazı gölgelendiriciler için daha iyi önizleme sağlayabilir. Gölgelendirici tasarımcısında gölgelendiricilerin önizlemesi hakkında daha fazla bilgi için bkz. [gölgelendirici tasarımcısında](../designers/shader-designer.md) **gölgelendiricilerin** önizlemesi.

Aşağıdaki çizim, bu belgede açıklanan gölgelendiriciyi, [nasıl yapılır: modellemenin nasıl yapıldığını](../designers/how-to-model-3-d-terrain.md)gösteren 3B sahneye uygulanacağını gösterir. Rengin yoğunluğu, dünyanın içindeki noktanın yüksekliğiyle artar.

![3&#45;D teryağma modeline uygulanan gradyan efekti](../designers/media/digit-gradient-effect-result.png)

3D modele gölgelendirici uygulama hakkında daha fazla bilgi için bkz. [nasıl yapılır: bir gölgelendiriciyi bir gölgelendirici uygulama](../designers/how-to-apply-a-shader-to-a-3-d-model.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır. 3B modele gölgelendirici uygulama](../designers/how-to-apply-a-shader-to-a-3-d-model.md)
- [Nasıl yapılır: gölgelendiriciyi dışarı aktarma](../designers/how-to-export-a-shader.md)
- [Nasıl yapılır: 3B terbotları modelleme](../designers/how-to-model-3-d-terrain.md)
- [Nasıl yapılır: gri tonlamalı doku gölgelendiricisi oluşturma](../designers/how-to-create-a-grayscale-texture-shader.md)
- [Gölgelendirici Tasarımcısı](../designers/shader-designer.md)
- [Gölgelendirici Tasarımcısı düğümleri](../designers/shader-designer-nodes.md)
