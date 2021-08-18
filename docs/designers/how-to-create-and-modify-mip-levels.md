---
title: 'Nasıl yapılır: MIP Düzeyleri Oluşturma ve Değiştirme'
description: Doku alanı Ayrıntı Düzeyi için MIP düzeyleri oluşturmak ve değiştirmek üzere Görüntü Düzenleyicisi'ni kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: f64d4369-2307-4175-a39a-2e45506f7fa1
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-designers
ms.workload:
- multiple
ms.openlocfilehash: 035fba623bfa9c90476698a04cdd194d0cf3c8e4
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122104748"
---
# <a name="how-to-create-and-modify-mip-levels"></a>Nasıl yapılır: MIP düzeyleri oluşturma ve değiştirme
Bu belgede, Doku-Boşluk  Ayrıntı Düzeyi (LoD) için *MIP düzeyleri* oluşturmak ve değiştirmek için Görüntü Düzenleyicisi'nin nasıl kullanacağız?

## <a name="generating-mip-levels"></a>MIP düzeyleri oluşturma
*Mipmapping,* dokuların birkaç kopyasını farklı boyutlarda önceden hesaplayarak ve depolayarak işleme hızını artırmak ve doku yapıtları üzerinde diğer ad oluşturma yapıtlarını azaltmak için kullanılan bir tekniktir. MIP düzeyi olarak bilinen her kopya, önceki kopyanın genişliğinin ve yüksekliğinin yarısıdır. Bir nesnenin yüzeyinde doku işlenirse, doku yüzeyin ekran alanıyla en yakından ilgili MIP düzeyi otomatik olarak seçilir. Bu, grafik donanımının tutarlı görsel kalitesini korumak için fazla büyük dokuları filtrelemek zorunda olmadığını anlamına gelir. MIP düzeylerini depolamanın bellek maliyeti yalnızca özgün dokudan yaklaşık yüzde 33 daha fazla olsa da performans ve görüntü kalitesi bunu doğrular.

#### <a name="to-generate-mip-levels"></a>MIP düzeyleri oluşturmak için

1. Nasıl yapılır: Temel doku oluşturma [konusunda açıklandığı gibi temel dokuyla başlama.](../designers/how-to-create-a-basic-texture.md) En iyi sonuçlar için genişliği ve yüksekliği iki güçten (örneğin, 256, 512, 1024 gibi) olan bir doku belirtin.

2. MIP düzeylerini oluşturma. Görüntü Düzenleyicisi **Modu araç çubuğunda** Gelişmiş **AraçlarPs**  >    >  **Oluştur'a tıklayın.**

     Sonraki  **Mip Düzeyine Git ve Önceki Mip** Düzeyine Git düğmelerinin artık Görüntü Düzenleyicisi Modu araç çubuğunda **görüntüleyebilirsiniz.** Özellikler **penceresi görüntülenirse,** görüntü özelliklerinde **mip** Düzeyi ve **Mip** Düzeyi Sayısı salt okunur özelliklerinin de görüntüde görüntülendiğinden de dikkat görüntülenebilir.

## <a name="modifying-mip-levels"></a>MIP düzeylerini değiştirme
Özel etkiler elde etmek veya belirli ayrıntı düzeylerinde görüntü kalitesini artırmak için her MIP düzeyini tek tek değiştirebilirsiniz. Örneğin, dokusal bir nesneye bir uzaklıkta farklı bir görünüm (daha büyük mesafe daha küçük MIP düzeylerine karşılık gelen) veya metin veya simge içeren dokuların daha küçük MIP düzeylerinde bile okunaklı kalmasını silebilirsiniz.

#### <a name="to-modify-an-individual-mip-level"></a>Tek bir MIP düzeyini değiştirmek için

1. Değiştirmek istediğiniz MIP düzeyini seçin. Görüntü Düzenleyicisi **Modu araç çubuğunda,** MIP düzeyleri arasında geçiş yapmak için Sonraki **MIP** Düzeyine Git ve Önceki **MIP** Düzeyine Git düğmelerini kullanın.

2. Değiştirmek istediğiniz MIP düzeyini seçmenizin ardından çizim araçlarını kullanarak diğer MIP düzeylerinin içeriğini değiştirmeden değiştirebilirsiniz. Çizim araçları Görüntü Düzenleyicisi araç **çubuğunda** kullanılabilir. Bir aracı seçmenizin ardından Özellikler penceresinde bu aracın özelliklerini **değiştirebilirsiniz.** Çizim araçları ve özellikleri hakkında bilgi için bkz. [Görüntü Düzenleyicisi.](../designers/image-editor.md)

> [!NOTE]
> Belirli etkiler elde etmek için gerçekleştirdiğiniz gibi tek tek MIP düzeylerinin içeriklerini değiştirmenize gerek yoksa, derleme zamanında kaynak dokudan mipmap'ler oluşturmanız önerilir. Bu, MIP düzeyinde yapılan değişiklikler otomatik olarak diğer düzeylere yayılmay olduğundan MIP düzeylerinin kaynak dokuyla eşitlenmiş durumda kalmasını sağlamaya yardımcı olur. Derleme zamanında mipmap'ler oluşturma hakkında daha fazla bilgi için bkz. Nasıl [edilir: mipmap'leri içeren dokuyu dışarı aktarma.](../designers/how-to-export-a-texture-that-contains-mipmaps.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Temel doku oluşturma](../designers/how-to-create-a-basic-texture.md)
