---
title: 'Nasıl yapılır: MIP Düzeyleri Oluşturma ve Değiştirme'
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: f64d4369-2307-4175-a39a-2e45506f7fa1
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0e9764bdfb476d9e2c4aa8ab2c04ee3aaa4f222a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85769062"
---
# <a name="how-to-create-and-modify-mip-levels"></a>Nasıl yapılır: MIP düzeyleri oluşturma ve değiştirme
Bu belgede, doku alanı ayrıntı düzeyi (LoD) için *MIP düzeylerini* oluşturmak ve değiştirmek üzere **Görüntü Düzenleyicisi** 'nin nasıl kullanılacağı gösterilir.

## <a name="generating-mip-levels"></a>MıP düzeyleri oluşturma
Msunucudan *eşleme* , farklı boyutlarda dokuların birkaç kopyasını önceden hesaplayarak ve depolayarak, işleme hızını artırmak ve dokulu nesnelerdeki diğer ad yapılarını azaltmak için kullanılan bir tekniktir. MıP düzeyi olarak bilinen her kopya, önceki kopyanın genişliğinin ve yüksekliğinin yarısı. Bir doku nesnenin yüzeyinde işlendiğinde, dokulu yüzeyin ekran alanı alanına en yakın şekilde karşılık gelen MıP düzeyi otomatik olarak seçilir. Bu, grafik donanımının tutarlı görsel kalite sağlamak için büyük dokuları filtrelemeniz gerekmediği anlamına gelir. MıP düzeylerini depolamanın bellek maliyeti orijinal dokudan daha fazla yüzde 33 daha büyük olsa da, performans ve görüntü kalitesi kazançları bunu kolaylaştırır.

#### <a name="to-generate-mip-levels"></a>MıP düzeyleri oluşturmak için

1. [Nasıl yapılır: temel doku oluşturma](../designers/how-to-create-a-basic-texture.md)bölümünde açıklandığı gibi temel bir dokuyla başlayın. En iyi sonuçlar için, boyutun boyutunun iki üssü olan genişlik ve yüksekliğe sahip bir doku belirtin, örneğin, 256, 512, 1024 vb.

2. MıP düzeylerini oluşturun. **Görüntü Düzenleyicisi Modu** araç çubuğunda, **Gelişmiş**  >  **Araçlar**  >  **MIPS oluştur**' u seçin.

     **Sonraki MIP düzeyine git** ve **önceki MIP düzeyine git** düğmeleri artık **Görüntü Düzenleyicisi Modu** araç çubuğunda görünmediğine dikkat edin. **Özellikler** penceresi görüntülenirse, salt okuma özellikleri **MIP düzeyi** ve **MIP düzeyi sayısı** ' nın artık görüntü özelliklerinde göründüğünü de unutmayın.

## <a name="modifying-mip-levels"></a>MıP düzeylerini değiştirme
Özel etkileri elde etmek veya belirli ayrıntı düzeylerinde görüntü kalitesini artırmak için her MıP düzeyini tek tek değiştirebilirsiniz. Örneğin, bir uzaklıktan farklı bir görünüme (daha fazla mesafe daha küçük MıP düzeylerine karşılık gelir) göre dokulu bir nesneye izin verebilir veya metin veya sembolleri içeren dokuların daha küçük MıP düzeylerinde bile okunabilir olmasını sağlayabilirsiniz.

#### <a name="to-modify-an-individual-mip-level"></a>Tek bir MıP düzeyini değiştirmek için

1. Değiştirmek istediğiniz MıP düzeyini seçin. **Görüntü Düzenleyicisi Modu** araç çubuğunda, sonraki MIP **düzeyine git** ' i kullanın ve MIP düzeyleri arasında ilerlemek Için **önceki MIP düzeyi düğmelerine gidin** .

2. Değiştirmek istediğiniz MıP düzeyini seçtikten sonra, diğer MıP düzeylerinin içeriğini değiştirmeden değiştirmek için çizim araçlarını kullanabilirsiniz. Çizim araçları, **Görüntü Düzenleyicisi** araç çubuğunda bulunur. Bir araç seçtikten sonra **Özellikler penceresinde özelliklerini** değiştirebilirsiniz. Çizim araçları ve özellikleri hakkında bilgi için bkz. [görüntü düzenleyici](../designers/image-editor.md).

> [!NOTE]
> Ayrı ayrı MıP düzeylerinin içeriğini değiştirmeniz gerekmiyorsa — belirli etkileri elde etmek gibi, kaynak dokusundaki de derleme zamanında MIP haritaları oluşturmanızı öneririz. Bu, MıP seviyesindeki değişiklikler diğer düzeylere otomatik olarak yayılmadığından, MıP düzeylerinin kaynak dokuyla eşitlenmiş durumda kalmasını sağlamaya yardımcı olur. Derleme zamanında mı haritaları oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: mı haritaları içeren dokuyu dışarı aktarma](../designers/how-to-export-a-texture-that-contains-mipmaps.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Temel doku oluşturma](../designers/how-to-create-a-basic-texture.md)
