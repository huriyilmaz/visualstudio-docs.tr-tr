---
title: 'Nasıl yapılır: geometri tabanlı Gradyan Gölgelendirici Oluşturma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 4b204405-ba95-4c5e-bd51-ec033a3ebfb6
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1d9bfa9a6e9be1a97b3a606aa302defd12a8d062
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72664517"
---
# <a name="how-to-create-a-geometry-based-gradient-shader"></a>Nasıl Yapılır: Geometri Tabanlı Gradyan Gölgelendirici Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu belgede, geometri tabanlı bir gradyan gölgelendiricisi oluşturmak için Gölgelendirici Tasarımcısının ve yönlendirilmiş grafik gölgelendirici dilinin nasıl kullanılacağı gösterilir. Bu gölgelendirici, bir sabit RGB renk değerini, dünya alanındaki bir nesne noktasının yüksekliğine göre ölçeklendirir.

 Bu belge Şu etkinlikleri gösterir:

- Gölgelendirici grafiğine düğüm ekleme

- Düğüm özelliklerini ayarlama

- Düğümlerin bağlantısı kesiliyor

- Düğümleri bağlama

## <a name="creating-a-geometry-based-gradient-shader"></a>Geometri tabanlı gradyan gölgelendiricisi oluşturma
 Pikselin konumunu gölgelendiricinize ekleyerek geometri temelli bir gölgelendirici uygulayabilirsiniz. Gölgeleme dillerinde, bir piksel, yalnızca bir 2-b ekrandaki renk ve konumlarından daha fazla bilgi içerir. Bazı sistemlerde *parça* olarak bilinen bir piksel, bir piksele karşılık gelen yüzeyi tanımlayan bir değerler koleksiyonudur. Bu belgede açıklanan gölgelendirici, dünyanın son çıkış rengini etkilemek için dünya alanındaki 3-b nesnesinin her bir pikselin yüksekliğini kullanır.

 Başlamadan önce, **Özellikler** penceresinin ve **araç kutusunun** görüntülendiğinden emin olun.

#### <a name="to-create-a-geometry-based-gradient-shader"></a>Geometri tabanlı bir gradyan gölgelendiricisi oluşturmak için

1. Birlikte çalışmak için bir DGSL gölgelendiricisi oluşturun. Projenize bir DGSL gölgelendiricisi ekleme hakkında daha fazla bilgi için bkz. [gölgelendirici tasarımcısında](../designers/shader-designer.md)Başlarken bölümü.

2. **Son renk** düğümündeki **nokta rengi** düğümünün bağlantısını kesin. **Nokta rengi** düğümünün **RGB** terminalini seçin ve ardından **Bağlantıları Kes**' i seçin. Bu, bir sonraki adımda eklenen düğüm için yer açar.

3. Grafiğe **çarpma** düğümü ekleyin. **Araç kutusunda**, **matematik**altında **çarp** ' ı seçin ve tasarım yüzeyine taşıyın.

4. Grafiğe bir **maske vektör** düğümü ekleyin. **Araç kutusu**' nda, **yardımcı program**altında **maske vektörü** ' nı seçin ve tasarım yüzeyine taşıyın.

5. **Maske vektör** düğümü için maske değerlerini belirtin. **Seç** modunda, **maske vektörü** düğümünü seçin ve ardından **Özellikler** penceresinde **yeşil/Y** özelliğini **doğru**olarak ayarlayın ve ardından **kırmızı/X**, **mavi/Z** ve **Alfa/W** özelliklerini yanlış olarak ayarlayın. Bu örnekte, **kırmızı/X**, **yeşil/Y**ve **mavi/Z** özellikleri **Dünya konumu** düğümünün X, Y ve Z bileşenlerine karşılık gelir ve **Alfa/W** kullanılmıyor. Yalnızca **yeşil/Y** **doğru**olarak ayarlandığı için, yalnızca giriş vektörünün Y bileşeni maskelendikten sonra kalır.

6. Grafiğe bir **Dünya konumu** düğümü ekleyin. **Araç kutusunda**, **sabitler**altında **Dünya konumu** ' nu seçin ve tasarım yüzeyine taşıyın.

7. Parçanın dünya alanı konumunu maskeleyin. **Seç** modunda, **World Position** düğümünün **Çıkış** terminalini **maske vektör** düğümünün **vektör** terminaline taşıyın. Bu bağlantı, parçaların konumunu x ve z bileşenlerini yok saymak için maskeler.

8. RGB renk sabitini, maskelenmiş dünya alanı konumuna göre çarpın. **Nokta rengi** düğümünün **RGB** terminalini **çarp** düğümünün **Y** terminaline taşıyın ve ardından **maske vektörü** düğümünün **Çıkış** terminalini **çarpma** düğümünün **X** terminaline taşıyın. Bu bağlantı, renk değerini, dünya alanındaki pikselin yüksekliğine ölçeklendirir.

9. Ölçeklendirilmiş renk değerini son renge bağlayın. **Çarp** düğümünün **Çıkış** terminalini **son renk** düğümünün **RGB** terminaline taşıyın.

   Aşağıdaki çizimde, tamamlanmış gölgelendirici grafiği ve bir sphere öğesine uygulanan gölgelendirici önizlemesi gösterilmektedir.

> [!NOTE]
> Bu çizimde, gölgelendirici efektini daha iyi göstermek için turuncu bir renk belirtilmiştir, ancak önizleme şekli dünya alanında bir konum olmadığından, gölgelendirici, gölgelendirici tasarımcısında tam olarak önizlenemez. Tam efekti göstermek için gölgelendirici gerçek bir sahnede önizlenmelidir.

 ![Gölgelendirici Grafiği ve efektinin önizlemesi](../designers/media/digit-gradient-effect-graph.png "Basamak-gradyan-efekt-grafik")

 Bazı biçimler bazı gölgelendiriciler için daha iyi önizleme sağlayabilir. Gölgelendirici tasarımcısında gölgelendiricilerin önizlemesi hakkında daha fazla bilgi için bkz. [gölgelendirici tasarımcısında](../designers/shader-designer.md) **gölgelendiricilerin** önizlemesi

 Aşağıdaki çizimde, bu belgede açıklanan gölgelendirici, [nasıl yapılır: model 3-b](../designers/how-to-model-3-d-terrain.md)' de gösterilen 3-b sahneye uygulanan gölgelendiricisi gösterilmektedir. Rengin yoğunluğu, dünyanın içindeki noktanın yüksekliğiyle artar.

 ![3&#45;D teryağma modeline uygulanan gradyan efekti](../designers/media/digit-gradient-effect-result.png "Basamak-gradyan-efekt-sonuç")

 3B modele gölgelendirici uygulama hakkında daha fazla bilgi için bkz. [nasıl yapılır: bir gölgelendiriciyi 3-b modele uygulama](../designers/how-to-apply-a-shader-to-a-3-d-model.md).

## <a name="see-also"></a>Ayrıca Bkz.
 [Nasıl yapılır: 3B modele gölgelendirici uygulama](../designers/how-to-apply-a-shader-to-a-3-d-model.md) [nasıl yapılır: gölgelendirici dışarı aktarma](../designers/how-to-export-a-shader.md) nasıl yapılır: [model 3-b Teryağmur](../designers/how-to-model-3-d-terrain.md) [nasıl yapılır: gri tonlamalı doku gölgelendirici](../designers/how-to-create-a-grayscale-texture-shader.md) [gölgelendirici tasarımcı](../designers/shader-designer.md) [gölgelendirici tasarımcı düğümleri](../designers/shader-designer-nodes.md) oluşturma
