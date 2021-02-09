---
title: 'Nasıl Yapılır: Temel Lambert Gölgelendiricisi Oluşturma'
description: Gölgelendirici tasarımcısını ve yönlendirilebilir grafik gölgelendirici dilini kullanarak klasik Lambert aydınlatma modelini uygulayan bir aydınlatma gölgelendiricisi oluşturma hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: ec5c10fb-9600-4240-8280-d59451ea1d68
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2aa4f3676708a99abba0a4706ecb524f1c14b212
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99917033"
---
# <a name="how-to-create-a-basic-lambert-shader"></a>Nasıl yapılır: Temel Lambert gölgelendiricisi oluşturma

Bu makalede, klasik Lambert aydınlatma modelini uygulayan bir aydınlatma gölgelendiricisi oluşturmak için Gölgelendirici Tasarımcısının ve yönlendirilmiş Graf gölgelendirici dilinin (DGSL) nasıl kullanılacağı gösterilmektedir.

## <a name="the-lambert-lighting-model"></a>Lambert aydınlatma modeli

Lambert aydınlatma modeli, 3B sahnede nesneleri gölgelendirmek için çevresel ve yönlü aydınlatma özelliklerini içerir. Çevresel bileşenler 3B sahnede temel bir aydınlatma düzeyi sağlar. Yönlü bileşenler, yönlü (en uzakta) ışık kaynaklarından daha fazla aydınlatma sağlar. Çevresel aydınlatma, kendi yönüne bakılmaksızın sahnenin tüm yüzeylerini eşit olarak etkiler. Belirli bir yüzey için, yüzeyde ortam renginin bir ürünüdür ve sahneye ait çevresel aydınlatma renk ve yoğunluğu vardır. Yönlü aydınlatma, yüzdeki her yüzeyi, ışık kaynağının yönlerine göre yüzey yönüne göre farklı şekilde etkiler. Bu, yüzeyi dağıtma renginin ve yönlerinin yanı sıra ışık kaynaklarının rengi, yoğunluğu ve yönlerinin bir ürünüdür. Işık kaynağına doğrudan ulaşan yüzeyler, doğrudan katkı almamak için en yüksek katkı ve yüzeyleri alır. Lambert aydınlatma modeli altında, ortam bileşeni ve bir veya daha fazla yönlü bileşen, nesne üzerindeki her bir nokta için toplam dağıtma rengi katkısını belirlemede birleştirilir.

Başlamadan önce, **Özellikler** penceresinin ve **araç kutusunun** görüntülendiğinden emin olun.

1. Çalışmak için bir DGSL gölgelendiricisi oluşturun. Projenize bir DGSL gölgelendiricisi ekleme hakkında daha fazla bilgi için bkz. [gölgelendirici tasarımcısında](../designers/shader-designer.md)Başlarken bölümü.

2. **Son renk** düğümündeki **nokta rengi** düğümünün bağlantısını kesin. **Nokta rengi** düğümünün **RGB** terminalini seçin ve ardından **Bağlantıları Kes**' i seçin. **Alfa** terminalini bağlı bırakın.

3. Grafiğe **Lambert** düğümü ekleyin. **Araç kutusu**' nda, **yardımcı program** altında **Lambert** ' yi seçin ve tasarım yüzeyine taşıyın. Lambert düğümü, çevresel ve Dağıtılmış aydınlatma parametrelerine göre pikselin toplam dağıtma rengi katkısını hesaplar.

4. **Nokta rengi** düğümünü **Lambert** düğümüne bağlayın. **Seç** modunda, **nokta rengi** düğümünün **RGB** terminalini **Lambert** düğümünün **dağıtma rengi** terminaline taşıyın. Bu bağlantı, pikselin ara değerli dağıtma rengi ile Lambert düğümünü sağlar.

5. Hesaplanan renk değerini son renge bağlayın. **Lambert** düğümünün **Çıkış** terminalini **son renk** düğümünün **RGB** terminaline taşıyın.

   Aşağıdaki çizimde, tamamlanmış gölgelendirici grafiği ve bir ekip modeline uygulanan gölgelendirici önizlemesi gösterilmektedir.

> [!NOTE]
> Bu çizimde gölgelendirici etkisini daha iyi göstermek için, gölgelendiricinin **Materialdağıt** parametresi kullanılarak turuncu bir renk belirtilmiştir. Bir oyun veya uygulama, her bir nesne için benzersiz bir renk değeri sağlamak üzere bu parametreyi kullanabilir. Malzeme parametreleri hakkında daha fazla bilgi için bkz. [gölgelendirici tasarımcısında](../designers/shader-designer.md)gölgelendiricilerin önizlemesi bölümü.

![Gölgelendirici Grafiği ve efektinin önizlemesi.](../designers/media/digit-lambert-effect-graph.png)

Bazı biçimler bazı gölgelendiriciler için daha iyi önizleme sağlayabilir. Gölgelendirici tasarımcısında gölgelendiricilerin önizlemesi hakkında daha fazla bilgi için, [gölgelendirici tasarımcısında](../designers/shader-designer.md)gölgelendiricilerin önizlemesi bölümüne bakın.

Aşağıdaki çizimde, bu belgede bir 3B modele uygulanan gölgelendirici gösterilmektedir.

![Bir modele uygulanan Lambert aydınlatma.](../designers/media/digit-lambert-effect-result.png)

3D modele gölgelendirici uygulama hakkında daha fazla bilgi için bkz. [nasıl yapılır: bir gölgelendiriciyi bir gölgelendirici uygulama](../designers/how-to-apply-a-shader-to-a-3-d-model.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: 3B modele gölgelendirici uygulama](../designers/how-to-apply-a-shader-to-a-3-d-model.md)
- [Nasıl Yapılır: Gölgelendiriciyi Dışarı Aktarma](../designers/how-to-export-a-shader.md)
- [Nasıl Yapılır: Temel Phong Gölgelendiricisi Oluşturma](../designers/how-to-create-a-basic-phong-shader.md)
- [Gölgelendirici Tasarımcısı](../designers/shader-designer.md)
- [Gölgelendirici Tasarımcısı düğümleri](../designers/shader-designer-nodes.md)
