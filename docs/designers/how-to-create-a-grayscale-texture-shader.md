---
title: 'Nasıl Yapılır: Gri Tonlamalı Doku Gölgelendiricisi Oluşturma'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 79181d81-44af-445e-9a18-03483dd70260
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1b74e956a74ff4c04dbc5a1c990fab708937d8f5
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76112619"
---
# <a name="how-to-create-a-grayscale-texture-shader"></a>Nasıl yapılsın: Gri tonlama doku shader oluşturma

Bu makalede, gri tonlamalı doku gölgeleyici oluşturmak için Shader Designer ve Directed Graph Shader Language (DGSL) nasıl kullanılacağı nı göstermektedir. Bu gölgelendirme doku örneğinin RGB renk değerini değiştirir ve son rengi ayarlamak için değiştirilmemiş alfa değeriyle birlikte kullanır.

## <a name="create-a-grayscale-texture-shader"></a>Gri tonlamalı doku gölgelendiricisi oluşturma

Son çıktı rengine yazmadan önce doku örneğinin renk değerini değiştirerek gri tonlama doku gölgeleyicisi uygulayabilirsiniz.

Başlamadan önce **Özellikler** penceresinin ve **Araç Kutusunun** görüntülendiğinden emin olun.

1. Nasıl açıklandığı gibi temel bir doku gölgeleyici [oluşturun: Temel bir doku gölgeleyici oluşturun.](../designers/how-to-create-a-basic-texture-shader.md)

2. **Doku Örneği** düğümünün **RGB** terminalini **Son Renk** düğümünün **RGB** terminalinden ayırın. **Select** modunda, **Doku Örneği** düğümünün **RGB** terminalini seçin ve ardından **Bağlantıları Kır'ı**seçin. Bu, bir sonraki adımda eklenen düğüm için yer sağlar.

3. Grafiğe bir **Desaturate** düğümü ekleyin. **Toolbox'ta,** **Filtreler** **altında, Desaturate'yi** seçin ve tasarım yüzeyine taşıyın.

4. **Desaturate** düğüm kullanarak gri ölçek değerini hesaplayın. **Select** modunda, **Doku Örneği** düğümünün **RGB** terminalini **Desaturate** düğümünün **RGB** terminaline taşıyın.

    > [!NOTE]
    > Varsayılan olarak, **Desaturate** düğümü giriş rengini tamamen eşitler ve gri tonlama için standart parlaklık ağırlıklarını kullanır. **Desaturate** düğümünün nasıl bir şekilde nasıl **olduğunu, Parlaklık** özelliğinin değerini değiştirerek veya giriş rengini kısmen desaturating ederek değiştirebilirsiniz. Giriş rengini kısmen doygunluk taslamak için, **Desaturate** düğümünün **Yüzde** terminaline [0,1) aralığında skaler bir değer sağlayın.

5. Gri tonlama renk değerini son renge bağlayın. **Desaturate** düğümünün **Çıkış** terminalini **Son Renk** düğümünün **RGB** terminaline taşıyın.

Aşağıdaki resimde tamamlanmış gölgeli grafik ve bir küp uygulanan gölgeli bir önizleme gösterir.

> [!NOTE]
> Bu resimde, önizleme şekli olarak bir düzlem kullanılır ve gölgelinin etkisini daha iyi göstermek için bir doku belirtilmiştir.

![Shader grafiği ve etkisinin önizlemesi](../designers/media/digit-grayscale-effect.png)

Bazı şekiller bazı gölgeliler için daha iyi önizlemeler sağlayabilir. Shader Designer'da gölgeli lerin önizlemesi hakkında daha fazla bilgi [için](../designers/shader-designer.md)Bkz.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır. 3B modele gölgelendirici uygulama](../designers/how-to-apply-a-shader-to-a-3-d-model.md)
- [Nasıl yapılır: Gölgeli dışa aktarma](../designers/how-to-export-a-shader.md)
- [Görüntü Düzenleyici](../designers/image-editor.md)
- [Shader Tasarımcısı](../designers/shader-designer.md)
- [Gölgeli Tasarımcı düğümleri](../designers/shader-designer-nodes.md)
