---
title: 'Nasıl Yapılır: Gri Tonlamalı Doku Gölgelendiricisi Oluşturma'
description: Doku örneğinin RGB renk değerini değiştiren bir gri tonlamalı doku gölgelendiricisi oluşturmak için Gölgelendirici Tasarımcısı ve Yönlendirilen Graph Gölgelendirici Dili kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 79181d81-44af-445e-9a18-03483dd70260
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-designers
ms.workload:
- multiple
ms.openlocfilehash: 99eaab8bc8d248ae36d8ec6c2b475b2e09d4c2ca
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122104852"
---
# <a name="how-to-create-a-grayscale-texture-shader"></a>Nasıl edilir: Gri tonlamalı doku gölgelendiricisi oluşturma

Bu makalede Gölgelendirici Tasarımcısı'nın ve Yönlendirilen Graph Gölgelendirici Dili'nin (DGSL) kullanarak gri tonlamalı doku gölgelendiricisi oluşturması gösterilir. Bu gölgelendirici doku örneğinin RGB renk değerini değiştirir ve ardından son rengi ayarlamak için değiştirilmemiş alfa değeriyle birlikte kullanır.

## <a name="create-a-grayscale-texture-shader"></a>Gri tonlamalı doku gölgelendiricisi oluşturma

Son çıkış rengine yazmadan önce doku örneğinin renk değerini değiştirerek gri tonlamalı doku gölgelendiricisi gerçekleştirebilirsiniz.

Başlamadan önce Özellikler penceresinin ve **Araç** Kutusunun **görüntülendiğinden emin** olun.

1. Nasıl edilir: Temel doku gölgelendiricisi oluşturma konusunda açıklandığı [gibi temel doku gölgelendiricisi oluşturun.](../designers/how-to-create-a-basic-texture-shader.md)

2. Doku Örneği **düğümünün RGB** **terminali ile** Son Renk **düğümünün RGB** **terminali bağlantısını** kesin. Seç **modunda** Doku Örneği **düğümünün RGB** **terminalini ve** ardından Bağlantıları **Kesme'yi seçin.** Bu, sonraki adımda eklenen düğüme yer sağlar.

3. **Grafiye bir Desaturate** düğümü ekleyin. Araç **Kutusunda, Filtreler'in** **altında** **Doygunluğu Çıkar'ı** seçin ve tasarım yüzeyine taşıyın.

4. **Desaturate** düğümünü kullanarak gri tonlamalı değeri hesap. Seç **modunda** Doku Örneği **düğümünün RGB** **terminali'ni** Doygunluğu Azaltma **düğümünün RGB** **terminaline** hareket ettirin.

    > [!NOTE]
    > Varsayılan olarak, **Desaturate** düğümü giriş renginin doymalarını tamamen değiştirir ve gri tonlamalı dönüştürme için standart renk ağırlıklarını kullanır. **Luminance** özelliğinin değerini değiştirerek veya giriş renginin yalnızca kısmen doygunluk değerini değiştirerek **Doygunluğu** Azaltma düğümünün nasıl davranacağını değiştirebilirsiniz. Giriş rengini kısmen doygunluğu sağlamak için[0,1) aralığında Doygunluğun **Desaturate** düğümünün Yüzde **terminaline** bir skaler değer sağlar.

5. Bağlan tonlamalı renk değerini son renge dönüştür. **Desaturate düğümünün Çıkış terminali'ni** Son Renk **düğümünün RGB** **terminaline** taşıma. 

Aşağıdaki çizimde tamamlanmış gölgelendirici grafı ve bir kübüne uygulanan gölgelendiricinin önizlemesi gösterilir.

> [!NOTE]
> Bu çizimde, önizleme şekli olarak bir düzlem kullanılır ve gölgelendiricinin etkisini daha iyi göstermek için bir doku belirtilmiştir.

![Gölgelendirici grafiği ve etkisinin önizlemesi](../designers/media/digit-grayscale-effect.png)

Bazı şekiller bazı gölgelendiriciler için daha iyi önizlemeler sağlar. Gölgelendirici Tasarımcısı'nda gölgelendiricileri önizleme hakkında daha fazla bilgi için bkz. [Gölgelendirici Tasarımcısı.](../designers/shader-designer.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır. 3B modele gölgelendirici uygulama](../designers/how-to-apply-a-shader-to-a-3-d-model.md)
- [Nasıl: Gölgelendiriciyi dışarı aktarma](../designers/how-to-export-a-shader.md)
- [Görüntü Düzenleyicisi](../designers/image-editor.md)
- [Gölgelendirici Tasarımcısı](../designers/shader-designer.md)
- [Gölgelendirici Tasarımcısı düğümleri](../designers/shader-designer-nodes.md)
