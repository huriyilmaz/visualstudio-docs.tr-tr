---
title: 'Nasıl yapılır: temel 3B model oluşturma'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: a0d97966-2df8-449b-a8cf-5a19684dc773
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 604847e5f9bf6111d548b9d3bbdc0a0e10301784
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72636727"
---
# <a name="how-to-create-a-basic-3d-model"></a>Nasıl yapılır: temel 3B model oluşturma

Bu makalede, temel bir 3B model oluşturmak için Model Düzenleyicisi 'nin nasıl kullanılacağı gösterilmektedir. Aşağıdaki etkinlikler ele alınmıştır:

- Sahneye nesne ekleme

- Yüzeyleri ve kenarları seçme

- Seçimleri çevirme

- Alt **bölüme** yüz ve **yükseltme** araçları 'nı kullanma

- **Üçgenlere ayır** komutunu kullanma

## <a name="create-a-basic-3d-model"></a>Temel 3B model oluşturma
Oyununuzun veya uygulamanızın 3B modellerini ve sahneleri oluşturmak ve değiştirmek için model düzenleyicisini kullanabilirsiniz. Aşağıdaki adımlarda, bir evin Basitleştirilmiş 3B modelini oluşturmak için Model Düzenleyicisi 'nin nasıl kullanılacağı gösterilmektedir. Basitleştirilmiş bir model, hala oluşturulmakta olan son resim varlıkları için, çarpışma algılaması için bir ağ olarak veya temsil ettiği nesne daha ayrıntılı işlemeden yararlanmak için çok uzakta bir model olarak kullanılabilir.

İşiniz bittiğinde, modelin şöyle görünmesi gerekir:

![Basitleştirilmiş evin tamamlanmış modeli](../designers/media/gfx_model_demo_house_final.png)

Başlamadan önce, **Özellikler** penceresi ve **araç kutusunun** görüntülendiğinden emin olun.

### <a name="to-create-a-simplified-3d-model-of-a-house"></a>Bir evin Basitleştirilmiş 3B modelini oluşturmak için

1. Çalışmak için bir 3B model oluşturun. Projenize bir model ekleme hakkında daha fazla bilgi için, bkz. [Model Düzenleyicisi](../designers/model-editor.md)'ndeki Başlarken bölümü.

2. Sahneye küp ekleyin. **Araç kutusu** penceresinde, **şekiller**altında **küp** ' i seçin ve tasarım yüzeyine taşıyın.

3. Yüz seçimine geçiş yapın. Model Düzenleyicisi araç çubuğunda **yüz seç**' i seçin.

4. Küpün üst kısmını alt bölümlere ayır. Yüz seçimi modunda, seçim için etkinleştirmek üzere küpü bir kez seçin ve ardından en üstteki yüzü seçmek için küpün en üstünü seçin. Model Düzenleyicisi araç çubuğunda alt **bölümlere**ayır ' ı seçin. Bu, küpün en üstüne, eşit olarak boyutlandırılmış dört bölüme bölünmüş yeni köşeler ekler.

    ![Küpün üst bölümü alt bölünmüştür](../designers/media/gfx_model_demo_house_subdiv.png)

5. Küpün iki bitişik tarafını — Örneğin, küpün ön ve sağ taraflarından yükseltme. Yüz seçimi modunda, seçim için etkinleştirmek üzere küpü bir kez seçtikten sonra küpün bir tarafını seçin. **CTRL** tuşunu basılı tutarak, önce seçtiğiniz tarafa bitişik olan küpün başka bir tarafını seçin ve ardından Model Düzenleyicisi araç çubuğunda, **yükseltme yüzü**' ni seçin.

    ![Küpün tarafları yükseltilmiş](../designers/media/gfx_model_demo_house_extrude.png)

6. Extrusbir kısmını genişletin. Az önce yükseltme yaptığınız yüzlerin birini seçin ve ardından Model Düzenleyicisi araç çubuğunda **çevir** aracını seçin ve çeviri işletini aynı yönde, aynı yönde taşıyın.

    ![Küpün bir tarafı daha fazla yükseltilmiş.](../designers/media/gfx_model_demo_house_extend.png)

7. Model üçgenlere ayır. Model Düzenleyicisi araç çubuğunda **gelişmiş**  > **Araçlar**  > **üçgenlere ayır**' ı seçin.

8. Evin çatı ' ini oluşturun. Model Düzenleyicisi araç çubuğunda **kenar Seç** ' i seçerek kenar seçimi moduna geçin ve sonra etkinleştirmek için küpü seçin. Burada gösterilen kenarları seçerken **CTRL** tuşuna basın ve basılı tutun:

    ![Tavan tepe düzeyini oluşturacak kenarlar](../designers/media/gfx_model_demo_house_edges.png)

    Kenarlar seçildiğinde, model **Düzenleyicisi araç çubuğunda çeviri aracını seçin** ve ardından evin çatı evini oluşturmak için çeviriyi yukarı doğru taşıyın.

   Basitleştirilmiş ev modeli tamamlanmıştır. Aşağıda, düz gölgeleme uygulanmış son model tekrar verilmiştir:

   ![Basitleştirilmiş evin tamamlanmış modeli](../designers/media/gfx_model_demo_house_final.png)

   Bir sonraki adım olarak, bu 3B modele bir gölgelendirici uygulayabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: 3B modele gölgelendirici uygulama](../designers/how-to-apply-a-shader-to-a-3-d-model.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: 3B arazi modeli oluşturma](../designers/how-to-model-3-d-terrain.md)
- [Model düzenleyicisi](../designers/model-editor.md)
- [Gölgelendirici tasarımcısı](../designers/shader-designer.md)
