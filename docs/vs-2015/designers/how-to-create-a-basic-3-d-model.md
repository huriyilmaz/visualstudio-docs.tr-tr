---
title: 'Nasıl yapılır: temel 3B model oluşturma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: a0d97966-2df8-449b-a8cf-5a19684dc773
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4b4db5b54f39a0be6de184b609e672b1f0173890
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72664602"
---
# <a name="how-to-create-a-basic-3-d-model"></a>Nasıl Yapılır: Temel 3B Model Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu belgede, temel bir 3-b modeli oluşturmak için Model Düzenleyicisi 'nin nasıl kullanılacağı gösterilir.

 Bu belge Şu etkinlikleri gösterir:

- Sahneye nesne ekleme

- Yüzeyleri ve kenarları seçme

- Seçimleri çevirme

- Alt **bölüme** yüz ve **yükseltme** araçları 'nı kullanma

- **Üçgenlere ayır** komutunu kullanma

## <a name="creating-a-basic-3-d-model"></a>Temel 3-b modeli oluşturma
 Oyun veya uygulamanız için 3B modelleri ve sahneleri oluşturmak ve değiştirmek üzere model düzenleyicisini kullanabilirsiniz. Aşağıdaki adımlarda, bir evin Basitleştirilmiş 3-b modelini oluşturmak için Model Düzenleyicisi 'nin nasıl kullanılacağı gösterilmektedir. Basitleştirilmiş bir model, hala oluşturulmakta olan son resim varlıkları için, çarpışma algılaması için bir ağ olarak veya temsil ettiği nesne daha ayrıntılı işlemeden yararlanmak için çok uzakta bir model olarak kullanılabilir.

 İşiniz bittiğinde, modelin şöyle görünmesi gerekir:

 ![Basitleştirilmiş evin tamamlanmış modeli](../designers/media/gfx-model-demo-house-final.png "gfx_model_demo_house_final")

 Başlamadan önce, **Özellikler** penceresi ve **araç kutusunun** görüntülendiğinden emin olun.

#### <a name="to-create-a-simplified-3-d-model-of-a-house"></a>Bir evin Basitleştirilmiş 3-b modelini oluşturmak için

1. Birlikte çalışmak için 3-b model oluşturun. Projenize bir model ekleme hakkında daha fazla bilgi için, bkz. [Model Düzenleyicisi](../designers/model-editor.md)'ndeki Başlarken bölümü.

2. Sahneye küp ekleyin. **Araç kutusu** penceresinde, **şekiller**altında **küp** ' i seçin ve tasarım yüzeyine taşıyın.

3. Yüz seçimine geçiş yapın. Model Düzenleyicisi araç çubuğunda **yüz seç**' i seçin.

4. Küpün üst kısmını alt bölümlere ayır. Yüz seçimi modunda, seçim için etkinleştirmek üzere küpü bir kez seçin ve ardından en üstteki yüzü seçmek için küpün en üstünü seçin. Model Düzenleyicisi araç çubuğunda alt **bölümlere**ayır ' ı seçin. Bu, küpün en üstüne, eşit olarak boyutlandırılmış dört bölüme bölünmüş yeni köşeler ekler.

    ![Küpün üst bölümü alt bölünmüştür](../designers/media/gfx-model-demo-house-subdiv.png "gfx_model_demo_house_subdiv")

5. Küpün iki bitişik tarafını — Örneğin, küpün ön ve sağ taraflarından yükseltme. Yüz seçimi modunda, seçim için etkinleştirmek üzere küpü bir kez seçtikten sonra küpün bir tarafını seçin. Denetim tuşunu basılı tutarak, önce seçtiğiniz tarafa bitişik olan küpün başka bir tarafını seçin ve ardından Model Düzenleyicisi araç çubuğunda, **yükseltme yüzü**' ni seçin.

    ![Küpün tarafları yükseltilmiş](../designers/media/gfx-model-demo-house-extrude.png "gfx_model_demo_house_extrude")

6. Extrusbir kısmını genişletin. Az önce yükseltme yaptığınız yüzlerin birini seçin ve ardından Model Düzenleyicisi araç çubuğunda **çevir** aracını seçin ve çeviri işletini aynı yönde, aynı yönde taşıyın.

    ![Küpün bir tarafı daha fazla yükseltilmiş.](../designers/media/gfx-model-demo-house-extend.png "gfx_model_demo_house_extend")

7. Model üçgenlere ayır. Model Düzenleyicisi araç çubuğunda **Gelişmiş**, **Araçlar**, **üçgenlere ayır**' yi seçin.

8. Evin çatı ' ini oluşturun. Model Düzenleyicisi araç çubuğunda **kenar Seç** ' i seçerek kenar seçimi moduna geçin ve sonra etkinleştirmek için küpü seçin. Burada gösterilen kenarları seçerken denetim tuşuna basın ve basılı tutun:

    ![Tavan tepe düzeyini oluşturacak kenarlar](../designers/media/gfx-model-demo-house-edges.png "gfx_model_demo_house_edges")

    Kenarlar seçildiğinde, model **Düzenleyicisi araç çubuğunda çeviri aracını seçin** ve ardından evin çatı evini oluşturmak için çeviriyi yukarı doğru taşıyın.

   Basitleştirilmiş ev modeli tamamlanmıştır. Aşağıda, düz gölgeleme uygulanmış son model tekrar verilmiştir:

   ![Basitleştirilmiş evin tamamlanmış modeli](../designers/media/gfx-model-demo-house-final.png "gfx_model_demo_house_final")

   Bir sonraki adım olarak, bu 3-b modeline bir gölgelendirici uygulayabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: 3B modele gölgelendirici uygulama](../designers/how-to-apply-a-shader-to-a-3-d-model.md).

## <a name="see-also"></a>Ayrıca Bkz.
 [Nasıl yapılır: model 3-b Teryağmm](../designers/how-to-model-3-d-terrain.md) [Model Düzenleyicisi](../designers/model-editor.md) [Gölgelendirici Tasarımcısı](../designers/shader-designer.md)
