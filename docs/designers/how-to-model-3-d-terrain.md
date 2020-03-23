---
title: 'Nasıl: Model 3D Arazi'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f779b1fd-82a9-4a11-8ab7-c1c9caabc883
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a863834790683b229c17ad55b9930a2b382c027b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589428"
---
# <a name="how-to-model-3d-terrain"></a>Nasıl yapılsın: Model 3D arazi

Bu makalede, model düzenleyicisi nasıl kullanılacağını bir 3B arazi modeli oluşturmak için gösterir.

## <a name="create-a-3d-terrain-model"></a>3B arazi modeli oluşturma

Ek yüzler yapmak için bir düzlemi bölerek ve ardından ilginç arazi özellikleri oluşturmak için ön bölmelerini manipüle ederek bir 3B arazi oluşturabilirsiniz.

Bitirdikten sonra, model aşağıdaki gibi görünmelidir:

![Bir arazi modelini gösteren 3&#45;D sahnesi](../designers/media/digit-terrain-model.png)

Başlamadan önce **Özellikler** penceresinin ve **Araç Kutusunun** görüntülendiğinden emin olun.

1. Çalışmak için bir 3B model oluşturun. Projenize nasıl bir model ekleyeceğiniz hakkında bilgi için [Model düzenleyicisinde](../designers/model-editor.md)Başlangıç Bölümü'ne bakın.

2. Olay yerine bir uçak ekleyin. **Toolbox'ta** **Shapes'in**altında **Düzlem'i** seçin ve tasarım yüzeyine taşıyın.

    > [!TIP]
    > Düzlem nesnesinin daha kolay çalışAbilmek için, tasarım yüzeyine çerçeveleyebilirsiniz. **Select** modunda düzlem nesnesini seçin ve ardından Model Düzenleyicisi araç çubuğunda **Çerçeve Nesnesi** düğmesini seçin.

3. Yüz seçim modunu girin. Model Düzenleyicisi araç çubuğunda **Yüzü Seç'i**seçin.

4. Uçağı böl. Yüz seçim modunda, seçim için etkinleştirmek için bir kez düzlemi seçin ve sonra tek yüzünü seçmek için yeniden seçin. Model Düzenleyicisi araç **çubuğunda, Alt Bölme yüzü'ni**seçin. Bu, düzlemi eşit büyüklüktedört bölüme bölen düzleme yeni tepeler ekler.

5. Daha fazla alt bölüm oluşturun. Yeni yüzler hala seçiliyken, **Subdivide yüzünü** iki kez daha seçin. Bu toplam 64 yüz oluşturur. Daha fazla alt bölüm oluşturarak, araziye daha fazla ayrıntı verebilirsiniz.

6. Nokta seçim modunu girin. Model Düzenleyicisi araç çubuğunda **Point'i seçin.**

7. Arazi özelliği oluşturmak için bir noktayı değiştirin. Nokta seçimi modunda, noktalardan birini seçin ve ardından Model Düzenleyicisi araç çubuğunda **Çevir** aracını seçin. Noktayı temsil eden bir kutu tasarım yüzeyinde görünür. Kutuyu taşımak ve ardından noktanın yüksekliğini değiştirmek için yeşil oku kullanın. İlginç arazi özellikleri oluşturmak için farklı noktalar için bu adımı yineleyin.

    > [!TIP]
    > Tek tip bir şekilde değiştirmek için aynı anda birkaç nokta seçebilirsiniz.

Arazi modeli tamamlandı. İşte phong gölgeleme uygulanan ile, yine son model:

![Bir arazi modelini gösteren 3&#45;D sahnesi](../designers/media/digit-terrain-model.png)

Bu arazi modelini, [nasıl açıklanabilir: Geometri tabanlı degrade shader oluşturma'da](../designers/how-to-create-a-geometry-based-gradient-shader.md)açıklanan degrade gölgeleyicinin etkisini göstermek için kullanabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Model düzenleyici](../designers/model-editor.md)
