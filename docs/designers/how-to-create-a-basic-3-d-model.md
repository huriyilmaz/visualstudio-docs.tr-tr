---
title: Nasıl?
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: a0d97966-2df8-449b-a8cf-5a19684dc773
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ce16e436172a7d369f2df8342f6b027b574056ab
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589532"
---
# <a name="how-to-create-a-basic-3d-model"></a>Nasıl yapılır: Temel 3B model oluşturma

Bu makalede, temel bir 3B model oluşturmak için Model Düzenleyicisi nasıl kullanılacağı nı gösterin. Aşağıdaki faaliyetler kapsanmaktadır:

- Sahneye nesne ekleme

- Yüzleri ve kenarları seçme

- Seçimleri çevirme

- **Subdivide yüz** ve **Ekstrüzyon yüz** araçlarını kullanma

- **Üçgenkomutunu** kullanma

## <a name="create-a-basic-3d-model"></a>Temel 3B model oluşturma
Model Düzenleyicisi'ni kullanarak oyununuz veya uygulamanız için 3B modeller ve sahneler oluşturabilir ve değiştirebilirsiniz. Aşağıdaki adımlar, bir evin basitleştirilmiş 3B modelini oluşturmak için Model Düzenleyicisi'nin nasıl kullanılacağını gösterir. Basitleştirilmiş bir model, hala oluşturulmakta olan son sanat varlıkları için stand-in, çarpışma algılama için bir kafes olarak veya temsil ettiği nesne daha ayrıntılı işlemeden yararlanamayacak kadar uzakta olduğunda kullanılacak düşük ayrıntılı bir model olarak kullanılabilir.

Bitirdikten sonra, model aşağıdaki gibi görünmelidir:

![Basitleştirilmiş evin tamamlanmış modeli](../designers/media/gfx_model_demo_house_final.png)

Başlamadan önce **Özellikler** penceresinin ve **Araç Kutusunun** görüntülendiğinden emin olun.

### <a name="to-create-a-simplified-3d-model-of-a-house"></a>Bir evin basitleştirilmiş 3B modelini oluşturmak için

1. Çalışmak için bir 3B model oluşturun. Projenize nasıl bir model ekleyeceğiniz hakkında bilgi için Model Düzenleyicisi'ndeki Başlangıç Bölümü'ne bakın. [Model Editor](../designers/model-editor.md)

2. Sahneye bir küp ekleyin. **Toolbox** penceresinde, **Şekiller** **altında, Küp'ü** seçin ve ardından tasarım yüzeyine taşıyın.

3. Yüz seçimine geçin. Model Düzenleyicisi araç çubuğunda **Yüzü Seç'i**seçin.

4. Küpün üst kısmını böl. Yüz seçimi modunda, seçim için etkinleştirmek için küpü bir kez seçin ve ardından üst yüzü seçmek için küpün üst ünü seçin. Model Düzenleyicisi araç **çubuğunda, Alt Bölme yüzü'ni**seçin. Bu, küpün üst kısmına eşit büyüklüktedört bölüme bölen yeni tepe ler ekler.

    ![Küpün üst kısmı bölündü](../designers/media/gfx_model_demo_house_subdiv.png)

5. Küpün iki bitişik tarafını (örneğin, küpün ön ve sağ taraflarını) ekstrüzyon. Yüz seçim modunda, seçim için etkinleştirmek için küpü bir kez seçin ve ardından küpün bir tarafını seçin. **Ctrl** tuşuna basın ve basılı tutun, önce seçtiğiniz tarafa bitişik olan küpün başka bir tarafını seçin ve ardından Model Düzenleyiciaraç çubuğunda **Ekstrüzyon yüzünü**seçin.

    ![Küpün kenarları ekstrüzyon edildi.](../designers/media/gfx_model_demo_house_extrude.png)

6. Ekstrüzyonlardan birini uzatın. Az önce ekstrüzyon yaptığınız yüzlerden birini seçin ve ardından Model Düzenleyiciaraç çubuğunda **Çeviri** aracını seçin ve çeviri manipülatörü ekstrüzyonla aynı yönde hareket ettirin.

    ![Küpün bir tarafı daha fazla ekstrüzyon olmuştur.](../designers/media/gfx_model_demo_house_extend.png)

7. Modeli üçgen. Model Düzenleyicisi araç çubuğunda **Gelişmiş** > **Araçları** > **Üçgen'i**seçin.

8. Evin çatısını oluşturun. Model Düzenleyicisi araç çubuğunda **Kenar Seç'i** seçerek kenar seçim moduna geçin ve ardından etkinleştirmek için küpü seçin. Burada gösterilen kenarları seçerken **Ctrl** tuşuna basın ve basılı tutun:

    ![Çatının zirvesini oluşturacak kenarlar](../designers/media/gfx_model_demo_house_edges.png)

    Kenarlar seçildiğinde, Model Düzenleyicisi araç çubuğunda Çeviri **aracını** seçin ve ardından evin çatısını oluşturmak için çeviri manipülatörü yukarı doğru hareket ettirin.

   Basitleştirilmiş ev modeli tamamlandı. Burada düz gölgeleme uygulanan, yine son model:

   ![Basitleştirilmiş evin tamamlanmış modeli](../designers/media/gfx_model_demo_house_final.png)

   Bir sonraki adım olarak, bu 3B modele bir gölge uygulayabilirsiniz. Bilgi için [bkz: 3B modele gölgeuygulayın.](../designers/how-to-apply-a-shader-to-a-3-d-model.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılsın: Model 3D arazi](../designers/how-to-model-3-d-terrain.md)
- [Model düzenleyici](../designers/model-editor.md)
- [Gölgelendirici tasarımcısı](../designers/shader-designer.md)
