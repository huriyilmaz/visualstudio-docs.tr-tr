---
title: 'Nasıl yapılır: 3B Terbotları modelleme'
description: Bir düzlemi ek yüz oluşturacak ve köşelerine göre düzenleyerek 3B teryağmur modeli oluşturmak için Model Düzenleyicisi 'ni nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: f779b1fd-82a9-4a11-8ab7-c1c9caabc883
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 969dd229d8d6cd6bdbe9d53eaabd63f1eedd6570
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99930856"
---
# <a name="how-to-model-3d-terrain"></a>Nasıl yapılır: 3B terbotları modelleme

Bu makalede, Model Düzenleyicisi 'nin 3B bir teryağmme modeli oluşturmak için nasıl kullanılacağı gösterilmektedir.

## <a name="create-a-3d-terrain-model"></a>3D teryağmur modeli oluşturma

Ek yüzler oluşturmak için bir düzlemi bölerek ve sonra da köşelerini düzenleyerek ilginç tere özellikleri oluşturacak şekilde 3B bir terle oluşturabilirsiniz.

İşiniz bittiğinde, modelin şöyle görünmesi gerekir:

![bir teryağmm modeli gösteren 3&#45;D sahneyi](../designers/media/digit-terrain-model.png)

Başlamadan önce, **Özellikler** penceresi ve **araç kutusunun** görüntülendiğinden emin olun.

1. Çalışmak için bir 3B model oluşturun. Projenize bir model ekleme hakkında daha fazla bilgi için, bkz. [Model Düzenleyicisi](../designers/model-editor.md)'ndeki Başlarken bölümü.

2. Sahneye bir düzlem ekleyin. **Araç kutusunda**, **şekiller** altında **düzlem** ' i seçin ve tasarım yüzeyine taşıyın.

    > [!TIP]
    > Düzlem nesnesinin ile çalışmayı kolaylaştırmak için, Tasarım yüzeyinde çerçeveye taşıyabilirsiniz. **Seç** modunda, düzlem nesnesini seçin ve ardından Model Düzenleyicisi araç çubuğunda **çerçeve nesnesi** düğmesini seçin.

3. Yüz seçimi modunu girin. Model Düzenleyicisi araç çubuğunda **yüz seç**' i seçin.

4. Düzlemi alt bölümlere ayır. Yüz seçimi modunda, seçim için etkinleştirmek üzere düzlemi bir kez seçtikten sonra tek yüzeyi seçmek için yeniden seçin. Model Düzenleyicisi araç çubuğunda alt **bölümlere** ayır ' ı seçin. Bu, düzlemi eşit olarak boyutlandırılmış dört bölüme bölünmüş yeni köşeler ekler.

5. Daha fazla alt bölüm oluşturun. Yeni yüzler hala seçili durumdayken alt **bölüyi** iki kez seçin. Bu, Toplam 64 yüz oluşturur. Daha fazla alt bölüm oluşturarak, daha fazla ayrıntı sağlayabilirsiniz.

6. Nokta seçimi modunu girin. Model Düzenleyicisi araç çubuğunda **nokta seç**' i seçin.

7. Bir noktayı bir teryağmi özelliği oluşturacak şekilde değiştirin. Nokta seçimi modunda noktalarından birini seçin ve ardından Model Düzenleyicisi araç çubuğunda **çevir** aracını seçin. Tasarım yüzeyinde, noktayı temsil eden bir kutu görüntülenir. Kutuyu taşımak için yeşil oku kullanın ve bu nedenle noktanın yüksekliğini değiştirin. İlginç teryağmur özellikleri oluşturmak için bu adımı farklı noktalara tekrarlayın.

    > [!TIP]
    > Tek seferde çeşitli noktaları seçerek tek tek seçebilirsiniz.

Teryağma modeli tamamlanmıştır. İşte Phong gölgeleme uygulanmış son model:

![bir teryağmm modeli gösteren 3&#45;D sahneyi](../designers/media/digit-terrain-model.png)

[Nasıl yapılır: geometri tabanlı Gradyan Gölgelendirici Oluşturma](../designers/how-to-create-a-geometry-based-gradient-shader.md)bölümünde açıklanan gradyan gölgelendiricisi efektini göstermek için bu teryağmur modelini kullanabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Model düzenleyicisi](../designers/model-editor.md)
