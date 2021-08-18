---
title: 'Nasıl Yapılır: Temel Lambert Gölgelendiricisi Oluşturma'
description: Klasik Lambert aydınlatma modelini uygulayan bir aydınlatma gölgelendiricisi oluşturmak için Gölgelendirici Tasarımcısı ve Yönlendirilen Graph Gölgelendirici Dili kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: ec5c10fb-9600-4240-8280-d59451ea1d68
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-designers
ms.workload:
- multiple
ms.openlocfilehash: 28f373fd289b5265c18b9d2ec3e92958cb154fcb
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122112080"
---
# <a name="how-to-create-a-basic-lambert-shader"></a>Nasıl yapılır: Temel Lambert gölgelendiricisi oluşturma

Bu makalede, klasik Lambert aydınlatma modelini uygulayan bir aydınlatma gölgelendiricisi oluşturmak için Gölgelendirici Tasarımcısı'nın ve Yönlendirilen Graph Gölgelendirici Dili'nin (DGSL) nasıl kullanımı açıklanmıştır.

## <a name="the-lambert-lighting-model"></a>Lambert aydınlatma modeli

Lambert aydınlatma modeli, 3D bir sahnedeki nesneleri gölgelendirmek için ortam ve yönlü aydınlatmayı içerir. Ortam bileşenleri, 3D sahnesinde temel bir taban düzeye sahiptir. Yönlü bileşenler, yönlü (uzak) ışık kaynaklarından ek bir kaynak sağlar. Ortam etkisi, yönlerinden bağımsız olarak sahnenin tüm yüzeylerini eşit olarak etkiler. Verilen bir yüzey için, yüzeyin çevresel renginin ve sahnenin ortam aydınlatmasının rengi ve yoğunluğunun bir ürünüdür. Yönlü aydınlatma, ışık kaynağının yönüne göre yüzeyin yönüne bağlı olarak sahnenin her yüzeyini farklı şekilde etkiler. Yüzeyin düz renginin ve yönünün, ışık kaynaklarının rengi, yoğunluğu ve yönünün bir ürünüdür. Doğrudan ışık kaynağına doğru yüz yüze gelen yüzeyler en yüksek katkıyı alır ve doğrudan uzakta olan yüzeyler herhangi bir katkı almaz. Lambert aydınlatma modeli altında, nesnede her nokta için toplam renkli katkıyı belirlemek üzere ortam bileşeni ve bir veya daha fazla yönlü bileşen bir araya geldi.

Başlamadan önce Özellikler penceresinin ve **Araç** Kutusunun **görüntülendiğinden emin** olun.

1. Birlikte çalışacak bir DGSL gölgelendiricisi oluşturun. Projenize DGSL gölgelendiricisi ekleme hakkında bilgi için Gölgelendirici Tasarımcısı'Başlarken bölümüne [bakın.](../designers/shader-designer.md)

2. Nokta Rengi **düğümünün** Son Renk **düğümünün bağlantısını** kesin. Nokta Rengi **düğümünün RGB** **terminalini ve** ardından Bağlantıları **Kesme'yi seçin.** Alfa **terminali** bağlı bırakın.

3. **Grafiye bir Lambert** düğümü ekleyin. Araç **Kutusunda, Yardımcı** **Program'ın altında** **Lambert'ı** seçin ve tasarım yüzeyine taşıyın. Lambert düğümü, ortam ve yayma aydınlatma parametrelerine göre pikselin toplam renk katkısını hesaplar.

4. Bağlan **Nokta Rengi düğümünü** **Lambert düğümüne** seçin. Seç **modunda,** Nokta Rengi **düğümünün RGB** **terminali'ni** Lambert düğümünün **En** Küçük Renk **terminaline** hareket ettirin. Bu bağlantı, lambert düğümüne pikselin irdelenmiş renklerini sağlar.

5. Bağlan renk değerini son renge göre değiştirir. Lambert **düğümünün** Çıkış **terminali'ni** Son Renk **düğümünün RGB** **terminaline** taşıma.

   Aşağıdaki çizimde tamamlanmış gölgelendirici grafı ve bir çaydanlık modeline uygulanan gölgelendiricinin önizlemesi gösterilmiştir.

> [!NOTE]
> Bu çizimde gölgelendiricinin etkisini daha iyi göstermek için gölgelendiricinin **MaterialDiffuse** parametresi kullanılarak turuncu renk belirtilmiştir. Bir oyun veya uygulama, her nesne için benzersiz bir renk değeri sağlamak üzere bu parametreyi kullanabilir. Malzeme parametreleri hakkında bilgi için Gölgelendirici Tasarımcısı'nda Gölgelendiricileri Önizleme [bölümüne bakın.](../designers/shader-designer.md)

![Gölgelendirici grafiği ve etkisinin önizlemesi.](../designers/media/digit-lambert-effect-graph.png)

Bazı şekiller bazı gölgelendiriciler için daha iyi önizlemeler sağlar. Gölgelendirici Tasarımcısı'nda gölgelendiricileri önizleme hakkında daha fazla bilgi için Gölgelendirici Tasarımcısı'nda Gölgelendiricileri Önizleme [bölümüne bakın.](../designers/shader-designer.md)

Aşağıdaki çizimde, 3D modele uygulanan bu belgede açıklanan gölgelendirici gösterilmiştir.

![Modele uygulanan lambert aydınlatması.](../designers/media/digit-lambert-effect-result.png)

Bir 3D modele gölgelendirici uygulama hakkında daha fazla bilgi için bkz. Nasıl [yapılır: 3D](../designers/how-to-apply-a-shader-to-a-3-d-model.md)Modele Gölgelendirici Uygulama.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: 3D Modele Gölgelendirici Uygulama](../designers/how-to-apply-a-shader-to-a-3-d-model.md)
- [Nasıl Yapılır: Gölgelendiriciyi Dışarı Aktarma](../designers/how-to-export-a-shader.md)
- [Nasıl Yapılır: Temel Phong Gölgelendiricisi Oluşturma](../designers/how-to-create-a-basic-phong-shader.md)
- [Gölgelendirici Tasarımcısı](../designers/shader-designer.md)
- [Gölgelendirici Tasarımcısı Düğümleri](../designers/shader-designer-nodes.md)
