---
title: 'Nasıl Yapılır: Temel Phong Gölgelendiricisi Oluşturma'
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: c7c69da8-142b-4d3b-9be9-4be0d5970b25
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 718607d74be1a74a799f8de9f4883e1df9fb7ef5
ms.sourcegitcommit: f27084e64c79e6428746a20dda92795df996fb31
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85769184"
---
# <a name="how-to-create-a-basic-phong-shader"></a>Nasıl yapılır: temel bir Phong gölgelendiricisi oluşturma

Bu makalede, klasik Phong aydınlatma modelini uygulayan bir aydınlatma gölgelendiricisi oluşturmak için Gölgelendirici Tasarımcısının ve yönlendirilmiş Graf gölgelendirici dilinin (DGSL) nasıl kullanılacağı gösterilmektedir.

## <a name="the-phong-lighting-model"></a>Phong aydınlatma modeli

Phong aydınlatma modeli, bir yüzey 'nin yansıtıcı özelliklerini taklit eden yansımalı vurgulama 'i içerecek şekilde lambda Yansımalı bileşen Lambert aydınlatma modelinde kullanılan aynı yönlü ışık kaynaklarından ek aydınlatma sağlar, ancak nihai renge olan katkı farklı şekilde işlenir. Yansımalı vurgulama, Görünüm yönü, hafif kaynakların yönü ve yüzey yönü arasındaki ilişkiye bağlı olarak sahnenin her yüzeyi farklı şekilde etkiler. Bu, yüzeysel renk, yüzeysel güç, yüzey yönü ve açık kaynakların rengi, yoğunluğu ve yönü hakkında bir üründür. Açık kaynağı doğrudan görüntüleyicide yansıtan yüzeyler, görüntüleyicideki ışık kaynağını yansıtan maksimum yansımalı katkı ve yüzeyleri, hiçbir katkı almaz. Phong aydınlatma modeli kapsamında, bir veya daha fazla yansımalı bileşen, nesne üzerindeki her bir nokta için yansımalı Vurgulamanın rengini ve yoğunluğunu belirleyip, ardından pikselin nihai rengini oluşturmak için Lambert aydınlatma modelinin sonucuna eklenir.

Lambert aydınlatma modeli hakkında daha fazla bilgi için bkz. [nasıl yapılır: temel Lambert gölgelendiricisi oluşturma](../designers/how-to-create-a-basic-lambert-shader.md).

Başlamadan önce, **Özellikler** penceresinin ve **araç kutusunun** görüntülendiğinden emin olun.

1. [Nasıl yapılır: temel Lambert gölgelendiricisi oluşturma](../designers/how-to-create-a-basic-lambert-shader.md)bölümünde açıklandığı gibi bir Lambert gölgelendiricisi oluşturun.

2. **Son renk** düğümünden **Lambert** düğümünün bağlantısını kesin. **Lambert** düğümünün **RGB** terminalini seçin ve ardından **Bağlantıları Kes**' i seçin. Bu, bir sonraki adımda eklenen düğüm için yer açar.

3. Grafiğe **ekleme** düğümü ekleyin. **Araç kutusunda**, **matematik**altında **Ekle** ' yi seçin ve tasarım yüzeyine taşıyın.

4. Grafiğe **Yansımalı** bir düğüm ekleyin. **Araç kutusu**' nda, **yardımcı program**altında **Yansımalı** ' ı seçin ve tasarım yüzeyine taşıyın.

5. Yansımalı katkı ekleyin. **Yansımalı** düğümün **Çıkış** terminalini **Add** düğümünün **X** terminaline taşıyın ve ardından **Lambert** düğümünün **Çıkış** terminalini **Add** düğümünün **Y** terminaline taşıyın. Bu bağlantılar piksel için toplam dağıtma ve yansımalı renk katkıları birleştirir.

6. Hesaplanan renk değerini son renge bağlayın. **Add** düğümünün **çıktı** terminalini **son renk** düğümünün **RGB** terminaline taşıyın.

   Aşağıdaki çizimde, tamamlanmış gölgelendirici grafiği ve bir ekip modeline uygulanan gölgelendirici önizlemesi gösterilmektedir.

> [!NOTE]
> Bu çizimde gölgelendirici etkisini daha iyi göstermek için, gölgelendiricinin **Materialdağıt** parametresi kullanılarak turuncu bir renk belirtilmiştir ve **Materialspecsel** ve **Materialspeculargüç** parametreleri kullanılarak metalik görünümlü bir bitiş belirtilir. Malzeme parametreleri hakkında daha fazla bilgi için bkz. [gölgelendirici tasarımcısında](../designers/shader-designer.md)gölgelendiricilerin önizlemesi bölümü.

![Gölgelendirici Grafiği ve efektinin önizlemesi](../designers/media/digit-lighting-graph.png)

Bazı biçimler bazı gölgelendiriciler için daha iyi önizleme sağlayabilir. Gölgelendirici tasarımcısında gölgelendiriciler önizlemesi hakkında daha fazla bilgi için bkz. [gölgelendirici tasarımcısında](../designers/shader-designer.md) gölgelendiricilerin önizlemesi bölümü

Aşağıdaki çizimde, bu belgede bir 3B modele uygulanan gölgelendirici gösterilmektedir. **Materialspecsel** özelliği (1,00, 0,50, 0,20, 0,00) olarak ayarlanır ve **MaterialSpecularPower** özelliği 16 olarak ayarlanmıştır.

> [!NOTE]
> **Materialspecsel** özelliği, yüzey malzemelerinin görünen bitişini belirler. Cam veya plastik gibi yüksek parlak bir yüzey, parlak bir beyaz gölgeye sahip olan yansımalı bir renge sahiptir. Metalik bir yüzey, kendi dağıtma rengine yakın bir yansımalı renge sahip olacak şekilde eğilimi gösterir. Bir tam bitiş yüzeyi, koyu bir gri gölge olan yansımalı bir renge sahip olma eğilimi gösterir.
>
> **MaterialSpecularPower** özelliği, Yansımalı vurguların ne kadar kuvvetli olduğunu belirler. Yüksek yansımalı güçler, daha fazla yerelleştirilmiş vurguları taklit etmez. Çok düşük yansımalı güçler, tüm yüzeyin rengini açığa çıkaran ve gizlemek için yoğun ve keskin vurguları taklit edebilir.

![Bir modele uygulanan Phong aydınlatma](../designers/media/digit-lighting-model.png)

3D modele gölgelendirici uygulama hakkında daha fazla bilgi için bkz. [nasıl yapılır: bir gölgelendiriciyi bir gölgelendirici uygulama](../designers/how-to-apply-a-shader-to-a-3-d-model.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır. 3B modele gölgelendirici uygulama](../designers/how-to-apply-a-shader-to-a-3-d-model.md)
- [Nasıl yapılır: gölgelendiriciyi dışarı aktarma](../designers/how-to-export-a-shader.md)
- [Nasıl yapılır: Temel Lambert gölgelendiricisi oluşturma](../designers/how-to-create-a-basic-lambert-shader.md)
- [Gölgelendirici Tasarımcısı](../designers/shader-designer.md)
- [Gölgelendirici Tasarımcısı düğümleri](../designers/shader-designer-nodes.md)
