---
title: 'Nasıl yapılır: MIP Düzeyleri Oluşturma ve Değiştirme'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f64d4369-2307-4175-a39a-2e45506f7fa1
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 793d730df3942608451e7dbc329819b98c451973
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76113287"
---
# <a name="how-to-create-and-modify-mip-levels"></a>Nasıl yapılır: MIP düzeyleri oluşturma ve değiştirme
Bu belge, *MiP düzeylerini* doku alanı Ayrıntı Düzeyi (LoD) için oluşturmak ve değiştirmek için Görüntü Düzenleyicisi'nin nasıl kullanılacağını gösterir. **Image Editor**

## <a name="generating-mip-levels"></a>MIP düzeyleri oluşturma
*Mipmapping,* bir dokunun farklı boyutlardaki birkaç kopyasını önceden hesaplayarak ve depolayarak işleme hızını artırmak ve dokulu nesneler üzerindeki diğer adları azaltmak için kullanılan bir tekniktir. MIP düzeyi olarak bilinen her kopya, önceki kopyanın genişliğinin ve yüksekliğinin yarısıdır. Bir doku nesnenin yüzeyinde işlendiğinde, dokulu yüzeyin ekran alanı alanına en yakın olan MIP düzeyi otomatik olarak seçilir. Bu, grafik donanımı tutarlı görsel kalitesini korumak için büyük boyutlu dokuları filtrelemek zorunda olmadığı anlamına gelir. MIP düzeylerini depolamanın bellek maliyeti tek başına orijinal dokudan yaklaşık yüzde 33 daha fazla olsa da, performans ve görüntü kalitesi kazançları bunu haklı çıkarır.

#### <a name="to-generate-mip-levels"></a>MIP düzeyleri oluşturmak için

1. Nasıl açıklandığı gibi temel bir doku ile [başlayın: Temel bir doku oluşturun.](../designers/how-to-create-a-basic-texture.md) En iyi sonuçlar için, 256, 512, 1024 ve benzeri iki boyutu nda bir güce sahip bir doku belirtin.

2. MIP düzeylerini oluşturun. Görüntü **Düzenleyici modu** araç çubuğunda Gelişmiş**Araçlar** > **Mips oluştur'u** **seçin.** > 

     **Sonraki Mip Düzeyine Git** ve **Önceki Mip Düzeyine Git** düğmelerinin artık Görüntü **Düzenleyicisi Modu** araç çubuğunda göründüğüne dikkat edin. **Özellikler** penceresi görüntülenirse, resim özelliklerinde **mip düzeyi** ve **Mip Düzey Sayısı** artık salt okunur özelliklerinin de göründüğünü unutmayın.

## <a name="modifying-mip-levels"></a>MIP düzeylerini değiştirme
Özel efektler elde etmek veya belirli ayrıntı düzeylerinde görüntü kalitesini artırmak için her MIP düzeyini tek tek değiştirebilirsiniz. Örneğin, dokulu bir nesneye uzakta farklı bir görünüm verebilirsiniz (daha uzaklık daha küçük MIP düzeylerine karşılık gelir) veya metin veya sembol içeren dokuların daha küçük MIP düzeylerinde bile okunaklı kalmasını sağlayabilirsiniz.

#### <a name="to-modify-an-individual-mip-level"></a>Tek bir MIP düzeyini değiştirmek için

1. Değiştirmek istediğiniz MIP düzeyini seçin. Görüntü **Düzenleyicimodu** araç çubuğunda, MIP düzeyleri arasında ilerlemek **için Sonraki MIP Düzeyine Git** ve Önceki **MIP Düzeyine Git** düğmelerini kullanın.

2. Değiştirmek istediğiniz MIP düzeyini seçtikten sonra, diğer MIP düzeylerinin içeriğini değiştirmeden değiştirmek için çizim araçlarını kullanabilirsiniz. Çizim araçları **Resim Düzenleyicisi** araç çubuğunda mevcuttur. Bir araç seçtikten sonra, **Özellikler** penceresindeki özelliklerini değiştirebilirsiniz. Çizim araçları ve özellikleri hakkında bilgi için [Resim Düzenleyicisi'ne](../designers/image-editor.md)bakın.

> [!NOTE]
> Belirli efektleri elde etmek için yapabileceğiniz gibi, tek tek MIP düzeylerinin içeriğini değiştirmeniz gerekmiyorsa, yapı zamanında kaynak dokudan mipmaps oluşturmanızı öneririz. Bu, MIP düzeyindeyapılan değişiklikler otomatik olarak diğer düzeylere yayılmadığından, MIP düzeylerinin kaynak dokuyla eşit kalmasını sağlamaya yardımcı olur. Oluşturma zamanında mipmaps oluşturma hakkında daha fazla bilgi için [bkz: Mipmaps içeren bir doku dışa aktarma.](../designers/how-to-export-a-texture-that-contains-mipmaps.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Temel doku oluşturma](../designers/how-to-create-a-basic-texture.md)
