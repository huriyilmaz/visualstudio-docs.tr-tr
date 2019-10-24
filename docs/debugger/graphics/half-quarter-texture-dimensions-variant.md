---
title: Yarı çeyrek doku boyutları varyantı | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 282e9bbb-51aa-4cd0-8e5c-0901268c29e5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f4c82836f5a80fae421a30721d8c3ee4c3d6893d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72735390"
---
# <a name="halfquarter-texture-dimensions-variant"></a>Yarı/Çeyrek Doku Boyutları Çeşidi
İşleme hedefi olmayan dokuların doku boyutlarını azaltır.

## <a name="interpretation"></a>Korunur
 Küçük dokular daha az bellek kaplar ve bu nedenle daha az bellek bant genişliği tüketir ve GPU 'nun doku önbelleğinde basınç azalır. Ancak, özellikle de 3-b sahnede yakından görüntülendiklerinde veya büyütme bölümünde görüntülenirken, daha az ayrıntı, daha az görüntü kalitesine neden olabilir.

 Bu çeşit büyük bir performans kazancı gösteriyorsa, uygulamanızın çok fazla bellek bant genişliği tükettiğini, doku önbelleğinin yeterince veya her ikisini de kullandığını gösterebilir. Ayrıca dokularınızın kullanılabilir olandan daha fazla GPU belleği kapladığını belirtebilir ve bu da dokuların sistem belleğine disk belleğine alınmasına neden olur.

 Uygulamanız çok fazla bellek bant genişliği kullanıyorsa veya doku önbelleğini yeterince tercih edebiliyorsa, dokularınızın boyutunu azaltmayı göz önünde bulundurun, ancak yalnızca uygun dokular için MIP haritalarını etkinleştirmeyi düşünün. Daha küçük dokulara benzer şekilde, MIP eşlenmiş dokular, daha fazla GPU belleği kaplamakla birlikte daha az bellek bant genişliği tüketir ve önbellek kullanımını artırabilir, ancak doku ayrıntılarını azaltmazlar. Yüksek bellek kullanımı, dokuların sistem belleğine disk belleğine alınmasına neden olmadığı durumlarda MIP haritaları öneririz.

 Dokularınız kullanılabilir olandan daha fazla GPU belleği kapladığında dokuların boyutunu azaltmayı göz önünde bulundurun, ancak yalnızca uygun dokuları sıkıştırmayı düşünün. Küçük dokular gibi, sıkıştırılan dokular daha az bellek kaplar ve sistem belleğine sayfa ihtiyacını azaltır, ancak renk uygunluğuna düşürülür. Sıkıştırma, içeriğine bağlı olarak tüm dokuların (örneğin, küçük bir alanda önemli renk varyasyonlarına sahip olanlar) uygun değildir, ancak birçok dokuda sıkıştırma, boyutlarını azaltmadan daha iyi genel görüntü kalitesini koruyabilir.

## <a name="remarks"></a>Açıklamalar
 Doku boyutları, kaynak dokusu oluşturan `ID3D11Device::CreateTexture2D` her çağrıda azalır. Özellikle, `pDesc` geçirilen D3D11_TEXTURE2D_DESC nesnesi işlemede kullanılan bir dokuyu açıkladığı zaman doku boyutları azaltılır. Yani:

- BindFlags üyesinin yalnızca D3D11_BIND_SHADER_RESOURCE bayrağı kümesi vardır.

- MiscFlags üyesinde D3D11_RESOURCE_MISC_TILE_POOL bayrağı veya D3D11_RESOURCE_MISC_TILED bayrağı ayarlanmamış (döşeli kaynaklar yeniden boyutlandırılmaz).

- Doku biçimi, doku boyutunu azaltmak için gerekli olan bir işleme hedefi olarak desteklenir — D3D11_FORMAT_SUPPORT_RENDER_TARGET tarafından belirlendiği şekilde. BC1, BC2 ve BC3 biçimleri, işleme hedefleri olarak desteklenmese de desteklenir.

  İlk veriler uygulama tarafından sağlandıysa, bu değişken doku verilerini dokuyu oluşturmadan önce uygun boyuta ölçeklendirir. İlk veriler, BC1, BC2 veya BC3 gibi bir blok ile sıkıştırılmış biçimde sağlanırsa, daha küçük dokuyu oluşturmak için kullanılmadan önce kodu çözülür, ölçeklendirilir ve yeniden kodlanır. (Blok tabanlı sıkıştırma yapısı, ek kod çözme-kodlama işleminin neredeyse her zaman daha önce kodlanmayan bir dokusunun ölçeklendirilen sürümünden oluşturulduğu zaman daha düşük görüntü kalitesine neden olur.)

  Doku için MIP eşlemeleri etkinleştirilmişse, varyant, MIP düzeylerinin sayısını buna uygun şekilde azaltır; çeyrek boyutuna ölçeklendirirken yarı boyutlu veya iki daha az ölçeklendirirken bir daha az.

## <a name="example"></a>Örnek
 Bu varyant, `CreateTexture2D`çağrısından önce çalışma zamanında dokuları yeniden boyutlandırır. Tam boyutlu dokular daha fazla disk alanı kullandığından ve özellikle de önemli bir işlem gerektiren sıkıştırılmış dokular için, ek adım uygulamanızda yükleme sürelerini artırabildiğinden, üretim kodu için bu yaklaşıma önerilir Kodlanacak kaynaklar. Bunun yerine, yapı işlem hattınızın bir parçası olan bir görüntü Düzenleyicisi veya görüntü işlemcisi kullanarak dokularınızı çevrimdışı olarak yeniden boyutlandırmanızı öneririz. Bu yaklaşımlar, disk alanı gereksinimlerini azaltır ve uygulamanızda çalışma zamanı ek yükünü ortadan kaldırır ve dokularınızı küçülterek veya sıkıştırırken en iyi görüntü kalitesini sürdürebilmeniz için daha fazla işleme süresi elde edebilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Mip-map Oluşturma Çeşidi](mip-map-generation-variant.md)
- [BC Doku Sıkıştırma Çeşidi](bc-texture-compression-variant.md)