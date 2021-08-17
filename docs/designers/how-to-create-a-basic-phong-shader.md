---
title: 'Nasıl Yapılır: Temel Phong Gölgelendiricisi Oluşturma'
description: Klasik Piser aydınlatma modelini uygulayan bir aydınlatma gölgelendiricisi oluşturmak için Gölgelendirici Tasarımcısı ve Yönlendirilen Graph Gölgelendirici Dili kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: c7c69da8-142b-4d3b-9be9-4be0d5970b25
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-designers
ms.workload:
- multiple
ms.openlocfilehash: a14e3739e7f869222bd16a1a5764c562ad07c977
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122035559"
---
# <a name="how-to-create-a-basic-phong-shader"></a>Nasıl: Temel P shader oluşturma

Bu makalede Gölgelendirici Tasarımcısı'nın ve Directed Graph Gölgelendirici Dili'nin (DGSL) klasik P classic P classic aydınlatma modelini uygulayan bir aydınlatma gölgelendiricisi oluşturması açıklanmıştır.

## <a name="the-phong-lighting-model"></a>Piser aydınlatma modeli

Piser aydınlatma modeli, Lambert aydınlatma modelini, bir yüzeyin yansıtıcı özelliklerinin benzetimini yapılan specular vurgulamayı içerecek şekilde genişlettir. Specular bileşeni, Lambert aydınlatma modelinde kullanılan aynı yönlü ışık kaynaklarından ek destek sağlar, ancak son renge olan katkısı farklı şekilde işlenir. Görünüm yönü arasındaki ilişkiye, ışık kaynaklarının yönüne ve yüzeyin yönüne bağlı olarak, görünümde yer alan her yüzeyi farklı şekilde vurgular. Bu, yüzeyin speculer rengi, speculer gücü ve yönü ile ışık kaynaklarının rengi, yoğunluğu ve yönünün bir ürünüdür. Doğrudan görüntüleyicide ışık kaynağını yansıtan yüzeyler en fazla speculer katkıyı alır ve görüntüleyiciden uzakta yer alan ışık kaynağını yansıtan yüzeyler herhangi bir katkı almaz. P lambda aydınlatma modeli altında, nesnede her nokta için specular vurgulamanın rengini ve yoğunluğunu belirlemek üzere bir veya daha fazla specular bileşen birleştirilmiştir ve ardından pikselin son rengini üretmek için Lambert aydınlatma modelinin sonuçlarına eklenir.

Lambert aydınlatma modeli hakkında daha fazla bilgi için [bkz. Nasıl kullanılır: Temel lambert gölgelendiricisi oluşturma.](../designers/how-to-create-a-basic-lambert-shader.md)

Başlamadan önce Özellikler penceresinin ve **Araç** Kutusunun **görüntülendiğinden emin** olun.

1. Nasıllı: Temel lambert gölgelendiricisi oluşturma konusunda açıklandığı gibi bir [Lambert gölgelendiricisi oluşturun.](../designers/how-to-create-a-basic-lambert-shader.md)

2. **Lambert düğümünün** Son Renk **düğümüyle bağlantısını** kesin. Lambert **düğümünün RGB** **terminalini seçin ve** ardından Bağlantıları **Kesme'yi seçin.** Bu, sonraki adımda eklenen düğüme yer sağlar.

3. **Grafiye** bir Düğüm ekle ekleyin. Araç **Kutusunda, Matematik'in** **altında** **Ekle'yi** seçin ve tasarım yüzeyine taşıyın.

4. **Grafiye bir Specular** düğüm ekleyin. Araç **Kutusunda, Yardımcı** **Program'ın altında** **Specular'ı** seçin ve tasarım yüzeyine taşıma.

5. Specular katkıyı ekleyin. **Specular** düğümün Çıkış **terminalini** Add düğümünün  **X** terminaline ve **ardından Lambert** düğümünün Çıkış **terminalini** Add düğümünün **Y** **terminaline** taşıma. Bu bağlantılar piksel için toplam yayma ve specular renk katkılarını birleştirir.

6. Bağlan renk değerini son renge göre değiştirir. Düğüm **ekle'nin** Çıkış **terminali'ni** Son Renk **düğümünün RGB** **terminaline** taşıma.

   Aşağıdaki çizimde tamamlanmış gölgelendirici grafı ve bir çaydanlık modeline uygulanan gölgelendiricinin önizlemesi gösterilmiştir.

> [!NOTE]
> Bu çizimde gölgelendiricinin etkisini daha iyi göstermek için gölgelendiricinin **MaterialDiffuse** parametresi kullanılarak turuncu renk belirtilmiştir ve **MaterialSpecular** ve **MaterialSpecularPower** parametreleri kullanılarak bir gölgelendirici gibi bir son belirtilmiştir. Malzeme parametreleri hakkında bilgi için Gölgelendirici Tasarımcısı'nda Gölgelendiricileri Önizleme [bölümüne bakın.](../designers/shader-designer.md)

![Gölgelendirici grafiği ve etkisinin önizlemesi](../designers/media/digit-lighting-graph.png)

Bazı şekiller bazı gölgelendiriciler için daha iyi önizlemeler sağlar. Gölgelendirici Tasarımcısı'nda gölgelendiricileri önizleme hakkında daha fazla bilgi için Gölgelendirici Tasarımcısı'nda Gölgelendiricileri Önizleme [bölümüne bakın](../designers/shader-designer.md)

Aşağıdaki çizimde, 3D modele uygulanan bu belgede açıklanan gölgelendirici gösterilmiştir. **MaterialSpecular** özelliği (1.00, 0.50, 0.20, 0.00) ve **MaterialSpecularPower** özelliği 16 olarak ayarlanır.

> [!NOTE]
> **MaterialSpecular** özelliği, yüzey malzemelerinin görünür sonlarını belirler. Cam veya perde gibi yüksek parlak bir yüzey, beyazın parlak bir tonu olan speculer bir renge sahiptir. Düz yüzey, düz renk rengine yakın bir speculer renge sahiptir. Düz bitişli bir yüzey, grinin koyu tonu olan speculer bir renge sahip olur.
>
> **MaterialSpecularPower** özelliği, belirli vurguların ne kadar yoğun olduğunu belirler. Yüksek specular güçler, daha yerelleştirilmiş vurguların benzetimini sağlar. Çok düşük speculer güçler, aşırı doygunluğa sahip olan ve yüzeyin tamamının rengini temizleyene yoğun, taramalı vurguların benzetimini sağlar.

![Modele uygulanan Pgam aydınlatması](../designers/media/digit-lighting-model.png)

Bir 3D modele gölgelendirici uygulama hakkında daha fazla bilgi için bkz. Nasıl [yapılır: 3D](../designers/how-to-apply-a-shader-to-a-3-d-model.md)modele gölgelendirici uygulama.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır. 3B modele gölgelendirici uygulama](../designers/how-to-apply-a-shader-to-a-3-d-model.md)
- [Nasıl: Gölgelendiriciyi dışarı aktarma](../designers/how-to-export-a-shader.md)
- [Nasıl yapılır: Temel Lambert gölgelendiricisi oluşturma](../designers/how-to-create-a-basic-lambert-shader.md)
- [Gölgelendirici Tasarımcısı](../designers/shader-designer.md)
- [Gölgelendirici Tasarımcısı düğümleri](../designers/shader-designer-nodes.md)
