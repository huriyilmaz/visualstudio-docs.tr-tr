---
title: 'Nasıl Yapılır: Temel Phong Gölgelendiricisi Oluşturma'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c7c69da8-142b-4d3b-9be9-4be0d5970b25
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f3059048f44524b9a838a8dfefc948ec4018dd05
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589493"
---
# <a name="how-to-create-a-basic-phong-shader"></a>Nasıl?

Bu makalede, klasik Phong aydınlatma modelini uygulayan bir aydınlatma gölgeleyici oluşturmak için Shader Designer ve Directed Graph Shader Language (DGSL) nasıl kullanılacağını göstermektedir.

## <a name="the-phong-lighting-model"></a>Phong aydınlatma modeli

Phong aydınlatma modeli, Lambert aydınlatma modelini, bir yüzeyin yansıtıcı özelliklerini simüle eden aynasal vurgulamayı içerecek şekilde genişletir. Aynasal bileşen, Lambert aydınlatma modelinde kullanılan aynı yönlü ışık kaynaklarından ek aydınlatma sağlar, ancak son renge katkısı farklı işlenir. Aynasal vurgulama, görünüm yönü, ışık kaynaklarının yönü ve yüzeyin yönü arasındaki ilişkiye bağlı olarak sahnedeki her yüzeyi farklı şekilde etkiler. Aynasal rengin, aynasal gücün ve yüzeyin yönünün, ışık kaynaklarının renginin, yoğunluğunun ve yönünün bir ürünüdür. Işık kaynağını doğrudan izleyiciye yansıtan yüzeyler maksimum aynasal katkıyı alır ve ışık kaynağını izleyiciden uzağa yansıtan yüzeyler hiçbir katkı almaz. Phong aydınlatma modeli altında, bir veya daha fazla aynasal bileşenleri renk ve nesne üzerinde her nokta için aynasal vurgulama yoğunluğunu belirlemek için birleştirilir ve daha sonra pikselin son rengini üretmek için Lambert aydınlatma modelinin sonucu eklenir .

Lambert aydınlatma modeli hakkında daha fazla bilgi için [bkz.](../designers/how-to-create-a-basic-lambert-shader.md)

Başlamadan önce **Özellikler** penceresinin ve **Araç Kutusunun** görüntülendiğinden emin olun.

1. Nasıl açıklandığı gibi bir Lambert gölgeleyici [oluşturun: Temel bir Lambert shader oluşturun.](../designers/how-to-create-a-basic-lambert-shader.md)

2. **Lambert** düğümündeki **Son Renk** düğümünden bağlantının kesilmesi. **Lambert** düğümünün **RGB** terminalini seçin ve ardından **Bağlantı Kesme'yi**seçin. Bu, bir sonraki adımda eklenen düğüm için yer sağlar.

3. Grafiğe **add** node ekleyin. Araç **Kutusunda,** **Matematik**altında **Ekle'yi** seçin ve tasarım yüzeyine taşıyın.

4. Grafiğe **bir Aynadüğüm** ekleyin. **Toolbox'ta,** **Utility**altında, **Specular'ı** seçin ve tasarım yüzeyine taşıyın.

5. Aynasal katkıyı da ekleyin. **Specular** düğümünün **Çıkış** terminalini **Ekle** düğümünün **X** terminaline taşıyın ve **ardından Lambert** düğümünün **Çıkış** terminalini **Ekle** düğümünün **Y** terminaline taşıyın. Bu bağlantılar piksel için toplam diffüz ve aynasal renk katkılarını birleştirir.

6. Hesaplanan renk değerini son renge bağlayın. **Ekle** düğümünün **Çıkış** terminalini **Son Renk** düğümünün **RGB** terminaline taşıyın.

   Aşağıdaki resimde tamamlanmış gölgeli grafik ve bir çaydanlık modeline uygulanan gölgeli bir önizleme gösterir.

> [!NOTE]
> Bu resimde gölgeleyicinin etkisini daha iyi göstermek için, **shader'in MaterialDiffuse** parametresi kullanılarak turuncu bir renk belirtilmiş ve **MaterialSpecular ve MaterialSpecularPower** parametreleri kullanılarak metalik görünümlü bir yüzey belirtilmiştir. **MaterialSpecularPower** Malzeme parametreleri hakkında bilgi için, [Shader Designer'daki Önizleme Shaders](../designers/shader-designer.md)bölümüne bakın.

![Shader grafiği ve etkisinin önizlemesi](../designers/media/digit-lighting-graph.png)

Bazı şekiller bazı gölgeliler için daha iyi önizlemeler sağlayabilir. Shader Designer'da gölgeli lerin önizlemesi hakkında daha fazla bilgi için, [Shader Designer'daki](../designers/shader-designer.md) Önizleme Gölgeleme bölümüne bakın

Aşağıdaki resimde, bu belgede açıklanan gölgeleyici bir 3B modele uygulanır. **MaterialSpecular** özelliği (1,00, 0,50, 0,20, 0,00) olarak ayarlanır ve **MaterialSpecularPower** özelliği 16 olarak ayarlanır.

> [!NOTE]
> **MaterialSpecular** özelliği yüzey malzemesinin görünür yüzeyini belirler. Cam veya plastik gibi parlak bir yüzey beyaz parlak bir gölge bir aynasal renk olma eğilimindedir. Metalik bir yüzey, dağınık rengine yakın bir aynasal renge sahip olma eğilimindedir. Bir sadan yüzeyi gri koyu bir gölge bir aynasal renk olma eğilimindedir.
>
> **MaterialSpecularPower** özelliği aynasal vurgular ne kadar yoğun olduğunu belirler. Yüksek aynasal güçler daha soluk, daha lokalize vurgular simüle. Çok düşük aynasal güçler, tüm yüzeyin rengini aşırı doygunlaştırabilen ve gizleyen yoğun, süpürme vurgularını simüle eder.

![Phong aydınlatma bir modele uygulanan](../designers/media/digit-lighting-model.png)

Bir 3B modele gölgeli nasıl uygulanacağı hakkında daha fazla bilgi için [bkz.](../designers/how-to-apply-a-shader-to-a-3-d-model.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır. 3B modele gölgelendirici uygulama](../designers/how-to-apply-a-shader-to-a-3-d-model.md)
- [Nasıl yapılır: Gölgeli dışa aktarma](../designers/how-to-export-a-shader.md)
- [Nasıl yapılır: Temel Lambert gölgelendiricisi oluşturma](../designers/how-to-create-a-basic-lambert-shader.md)
- [Shader Tasarımcısı](../designers/shader-designer.md)
- [Gölgeli Tasarımcı düğümleri](../designers/shader-designer-nodes.md)
