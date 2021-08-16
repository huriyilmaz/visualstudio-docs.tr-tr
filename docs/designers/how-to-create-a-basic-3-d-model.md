---
title: 'Nasıl: Temel 3D Model Oluşturma'
description: Model Düzenleyicisi'ni kullanarak bir sahneye nesne ekleme, seçimleri ve diğer etkinlikleri dönüştürme gibi temel bir 3D model oluşturma hakkında bilgi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: a0d97966-2df8-449b-a8cf-5a19684dc773
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-designers
ms.workload:
- multiple
ms.openlocfilehash: 11d99d94a972f14ca0945d7e405dbb372724a7d15c0a2697c21d3403852abdde
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121403690"
---
# <a name="how-to-create-a-basic-3d-model"></a>Nasıl yapılır: Temel 3B model oluşturma

Bu makalede, temel bir 3D modeli oluşturmak için Model Düzenleyicisi'ni nasıl kullanabileceğiniz gösterir. Aşağıdaki etkinlikler ele almaktadır:

- Bir sahneye nesne ekleme

- Yüzleri ve kenarları seçme

- Seçimleri çeviri

- Alt **yüz ve Extrude** **yüz araçlarını** kullanma

- **Triangulate komutunu** kullanma

## <a name="create-a-basic-3d-model"></a>Temel 3B model oluşturma
Oyun veya uygulamanıza yönelik 3D modelleri ve sahneleri oluşturmak ve değiştirmek için Model Düzenleyicisi'ni kullanabilirsiniz. Aşağıdaki adımlarda, bir evin basitleştirilmiş 3D modelini oluşturmak için Model Düzenleyicisi'nin nasıl kullanacağız? Basitleştirilmiş model, hala oluşturulan son resim varlıkları için bir destek olarak, çakışma algılama için bir örgü olarak veya temsil ettiği nesne daha ayrıntılı işlemeden yararlanacak kadar uzakta olduğunda kullanılacak düşük ayrıntılı bir model olarak kullanılabilir.

Bitirdikten sonra modelin şöyle olması gerekir:

![Basitleştirilmiş evin tamamlanmış modeli](../designers/media/gfx_model_demo_house_final.png)

Başlamadan önce Özellikler penceresinin ve **Araç Kutusunun** **görüntülendiğinden** emin olun.

### <a name="to-create-a-simplified-3d-model-of-a-house"></a>Bir evin basitleştirilmiş 3D modelini oluşturmak için

1. Birlikte çalışacak bir 3D model oluşturun. Projenize model ekleme hakkında bilgi için Model Düzenleyicisi'nde Başlarken bölümüne [bakın.](../designers/model-editor.md)

2. Sahneye bir küp ekleyin. Araç Kutusu **penceresindeki** **Şekiller'in altında** **Küp'e** tıklayın ve tasarım yüzeyine sürükleyin.

3. Yüz seçimine geçiş yapın. Model Düzenleyicisi araç çubuğunda Yüz **Seç'i seçin.**

4. Küpün üst kısmında altlık olarak yer alan. Yüz seçimi modunda küpü bir kez seçerek seçim için etkinleştirin ve ardından küpün üst yüzü seçerek üst yüzü seçin. Model Düzenleyicisi araç çubuğunda Alt **yüz'i seçin.** Bu, küpü eşit boyutlu dört bölüme bölen küpün en üstüne yeni köşeler ekler.

    ![Küpün üst kısmında alt bölü](../designers/media/gfx_model_demo_house_subdiv.png)

5. Küpün iki bitişik tarafını (örneğin, küpün ön ve sağ taraflarını) ekstrude. Yüz seçimi modunda, küpü seçim için etkinleştirmek için bir kez seçin ve ardından küpün bir tarafını seçin. **Ctrl** tuşuna basın ve basılı tutun, küpün ilk olarak seçtiğiniz kenarla bitişik olan başka bir tarafını seçin ve ardından Model Düzenleyicisi araç çubuğunda Yüzü **göster'i seçin.**

    ![Küpün kenarları eksildi](../designers/media/gfx_model_demo_house_extrude.png)

6. Eklerden birini genişletin. Az önce çıkarmış olduğunuz yüzlerden birini seçin ve ardından Model Düzenleyicisi  araç çubuğunda Çevir aracını seçin ve çeviri manipülatörünü kaldırma ile aynı yönde hareket ettirin.

    ![Küpün bir tarafı daha fazla eksildi.](../designers/media/gfx_model_demo_house_extend.png)

7. Modeli üçgene alın. Model Düzenleyicisi araç çubuğunda Gelişmiş Araçlar **Üçle'yi**  >    >  **seçin.**

8. Evin çatısını oluşturun. Model Düzenleyicisi araç çubuğunda  Kenar Seç'i ve ardından etkinleştirmek için küpü seçerek kenar seçimi moduna geçiş yapın. Burada gösterilen kenarları **seçmek için Ctrl** tuşuna basın ve basılı tutun:

    ![Tavanın tepe noktası olacak kenarlar](../designers/media/gfx_model_demo_house_edges.png)

    Kenarlar seçildiğinde, Model Düzenleyicisi araç çubuğunda Çevir  aracını seçin ve ardından çeviri manipülatörünü yukarı doğru hareket ettirerek evin çatısını oluşturun.

   Basitleştirilmiş ev modeli tamamlandı. Düz gölgelendirme uygulanmış şekilde son model şöyledir:

   ![Basitleştirilmiş evin tamamlanmış modeli](../designers/media/gfx_model_demo_house_final.png)

   Sonraki adım olarak, bu 3D modele gölgelendirici uygulayabilirsiniz. Bilgi için [bkz. Nasıl yapılır: 3D modele gölgelendirici uygulama.](../designers/how-to-apply-a-shader-to-a-3-d-model.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılıyor: 3D arazi modelleme](../designers/how-to-model-3-d-terrain.md)
- [Model düzenleyicisi](../designers/model-editor.md)
- [Gölgelendirici tasarımcısı](../designers/shader-designer.md)
