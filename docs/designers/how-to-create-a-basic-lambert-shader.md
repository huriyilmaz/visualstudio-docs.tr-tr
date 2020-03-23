---
title: 'Nasıl Yapılır: Temel Lambert Gölgelendiricisi Oluşturma'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ec5c10fb-9600-4240-8280-d59451ea1d68
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d78bc6e1b384f339d80e09fec81d42c1ab8ed103
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589506"
---
# <a name="how-to-create-a-basic-lambert-shader"></a>Nasıl yapılır: Temel Lambert gölgelendiricisi oluşturma

Bu makalede, klasik Lambert aydınlatma modelini uygulayan bir aydınlatma gölgeleyici oluşturmak için Shader Designer ve Directed Graph Shader Language (DGSL) nasıl kullanılacağını göstermektedir.

## <a name="the-lambert-lighting-model"></a>Lambert aydınlatma modeli

Lambert aydınlatma modeli 3D sahnede gölge nesneleri ortam ve yön aydınlatma içerir. Ortam bileşenleri, 3B sahnede temel bir aydınlatma düzeyi sağlar. Yönlü bileşenler, yönlü (uzak) ışık kaynaklarından ek aydınlatma sağlar. Ortam aydınlatması, oryantasyonları ne olursa olsun, sahnedeki tüm yüzeyleri eşit olarak etkiler. Belirli bir yüzey için, yüzeyin ortam renginin ve sahnedeki ortam aydınlatmasının renginin ve yoğunluğunun bir ürünüdür. Yönlü aydınlatma, ışık kaynağının yönüne göre yüzeyin yönünü temel alınarak sahnedeki her yüzeyi farklı şekilde etkiler. Yüzeyin dağınık renginin ve yönünün, ışık kaynaklarının renginin, yoğunluğunun ve yönünün bir ürünüdür. Doğrudan ışık kaynağına doğru gelen yüzeyler maksimum katkıyı alır ve doğrudan uzakta karşı karşıya olan yüzeyler hiçbir katkı almaz. Lambert aydınlatma modeli altında, ortam bileşeni ve bir veya daha fazla yönlü bileşenleri nesne üzerinde her nokta için toplam dağınık renk katkısını belirlemek için birleştirilir.

Başlamadan önce **Özellikler** penceresinin ve **Araç Kutusunun** görüntülendiğinden emin olun.

1. Çalışmak için bir DGSL gölgeleyici oluşturun. Projenize DGSL shader nasıl ekleyeceğiniz hakkında bilgi [için, Shader Designer'daki](../designers/shader-designer.md)Başlarken bölümüne bakın.

2. Nokta **Rengi** düğümünden **Son Renk** düğümünden bağlantı nı kesin. **Nokta Rengi** düğümünün **RGB** terminalini seçin ve ardından **Bağlantıları Kır'ı**seçin. **Alfa** terminalini bağlı bırakın.

3. Grafiğe bir **Lambert** düğümü ekleyin. **Toolbox,** **Utility**altında, **Lambert** seçin ve tasarım yüzeyine taşıyın. Lambert düğümü, ortam ve dağınık aydınlatma parametrelerine bağlı olarak pikselin toplam dağınık renk katkısını hesaplar.

4. Nokta **Rengi** düğümünü **Lambert** düğümüne bağlayın. **Select** modunda, **Point Color** düğümünün **RGB** terminalini **Lambert** düğümünün **Diffüz Renk** terminaline taşıyın. Bu bağlantı, pikselin enterpolasyonlu diffüz rengiile lambert düğüm sağlar.

5. Hesaplanan renk değerini son renge bağlayın. **Lambert** düğümünün **Çıkış** terminalini **Son Renk** düğümünün **RGB** terminaline taşıyın.

   Aşağıdaki resimde tamamlanmış gölgeli grafik ve bir çaydanlık modeline uygulanan gölgeli bir önizleme gösterir.

> [!NOTE]
> Bu resimde gölgeleyicinin etkisini daha iyi göstermek için, gölgeleyicinin **MaterialDiffuse** parametresi kullanılarak turuncu bir renk belirtilmiştir. Bir oyun veya uygulama, her nesne için benzersiz bir renk değeri sağlamak için bu parametreyi kullanabilir. Malzeme parametreleri hakkında bilgi için, [Shader Designer'daki Önizleme Shaders](../designers/shader-designer.md)bölümüne bakın.

![Gölgeli grafik ve etkisinin önizlemesi.](../designers/media/digit-lambert-effect-graph.png)

Bazı şekiller bazı gölgeliler için daha iyi önizlemeler sağlayabilir. Shader Designer'da gölgelilerin önizlemesi hakkında daha fazla bilgi için, [Shader Designer'daki](../designers/shader-designer.md)Önizleme Gölgeleme bölümüne bakın.

Aşağıdaki resimde, bu belgede açıklanan gölgeleyici bir 3B modele uygulanır.

![Lambert aydınlatma bir model e ki.](../designers/media/digit-lambert-effect-result.png)

Bir 3B modele gölgeli nasıl uygulanacağı hakkında daha fazla bilgi için [bkz.](../designers/how-to-apply-a-shader-to-a-3-d-model.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: 3B Modele Shader Uygulama](../designers/how-to-apply-a-shader-to-a-3-d-model.md)
- [Nasıl Yapılır: Gölgelendiriciyi Dışarı Aktarma](../designers/how-to-export-a-shader.md)
- [Nasıl Yapılır: Temel Phong Gölgelendiricisi Oluşturma](../designers/how-to-create-a-basic-phong-shader.md)
- [Shader Tasarımcısı](../designers/shader-designer.md)
- [Gölgelendirici Tasarımcısı Düğümleri](../designers/shader-designer-nodes.md)
