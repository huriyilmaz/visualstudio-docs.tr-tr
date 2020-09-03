---
title: Yarı çeyrek doku boyutları varyantı | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 282e9bbb-51aa-4cd0-8e5c-0901268c29e5
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 03485a3b9df9c06b1ef4755a5758cf2c8c997d1e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68161153"
---
# <a name="halfquarter-texture-dimensions-variant"></a>Yarı/Çeyrek Doku Boyutları Çeşidi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

İşleme hedefi olmayan dokuların doku boyutlarını azaltır.  
  
## <a name="interpretation"></a>Yorumlama  
 Küçük dokular daha az bellek kaplar ve bu nedenle daha az bellek bant genişliği tüketir ve GPU 'nun doku önbelleğinde basınç azalır. Ancak, özellikle de 3-b sahnede yakından görüntülendiklerinde veya büyütme bölümünde görüntülenirken, daha az ayrıntı, daha az görüntü kalitesine neden olabilir.  
  
 Bu çeşit büyük bir performans kazancı gösteriyorsa, uygulamanızın çok fazla bellek bant genişliği tükettiğini, doku önbelleğinin yeterince veya her ikisini de kullandığını gösterebilir. Ayrıca dokularınızın kullanılabilir olandan daha fazla GPU belleği kapladığını belirtebilir ve bu da dokuların sistem belleğine disk belleğine alınmasına neden olur.  
  
 Uygulamanız çok fazla bellek bant genişliği kullanıyorsa veya doku önbelleğini yeterince tercih edebiliyorsa, dokularınızın boyutunu azaltmayı göz önünde bulundurun, ancak yalnızca uygun dokular için MIP haritalarını etkinleştirmeyi düşünün. Daha küçük dokulara benzer şekilde, MIP eşlenmiş dokular, daha fazla GPU belleği kaplamakla birlikte daha az bellek bant genişliği tüketir ve önbellek kullanımını artırabilir, ancak doku ayrıntılarını azaltmazlar. Yüksek bellek kullanımı, dokuların sistem belleğine disk belleğine alınmasına neden olmadığı durumlarda MIP haritaları öneririz.  
  
 Dokularınız kullanılabilir olandan daha fazla GPU belleği kapladığında dokuların boyutunu azaltmayı göz önünde bulundurun, ancak yalnızca uygun dokuları sıkıştırmayı düşünün. Küçük dokular gibi, sıkıştırılan dokular daha az bellek kaplar ve sistem belleğine sayfa ihtiyacını azaltır, ancak renk uygunluğuna düşürülür. Sıkıştırma, içeriğine bağlı olarak tüm dokuların (örneğin, küçük bir alanda önemli renk varyasyonlarına sahip olanlar) uygun değildir, ancak birçok dokuda sıkıştırma, boyutlarını azaltmadan daha iyi genel görüntü kalitesini koruyabilir.  
  
## <a name="remarks"></a>Açıklamalar  
 Doku boyutları, `ID3D11Device::CreateTexture2D` kaynak dokusu oluşturan her çağrıda azaltılır. Özellikle, geçirilen D3D11_TEXTURE2D_DESC nesne, `pDesc` işlemede kullanılan bir dokuyu açıkladığı zaman doku boyutları azaltılır; bu:  
  
- BindFlags üyesi yalnızca D3D11_BIND_SHADER_RESOURCE bayrak kümesine sahiptir.  
  
- MiscFlags üyesinde D3D11_RESOURCE_MISC_TILE_POOL bayrağı yok veya D3D11_RESOURCE_MISC_TILED bayrağı ayarlı değil (döşeli kaynaklar yeniden boyutlandırılmaz).  
  
- Doku biçimi, doku boyutunu azaltmak için gereken D3D11_FORMAT_SUPPORT_RENDER_TARGET tarafından belirlendiği şekilde bir işleme hedefi olarak desteklenir. BC1, BC2 ve BC3 biçimleri, işleme hedefleri olarak desteklenmese de desteklenir.  
  
  İlk veriler uygulama tarafından sağlandıysa, bu değişken doku verilerini dokuyu oluşturmadan önce uygun boyuta ölçeklendirir. İlk veriler, BC1, BC2 veya BC3 gibi bir blok ile sıkıştırılmış biçimde sağlanırsa, daha küçük dokuyu oluşturmak için kullanılmadan önce kodu çözülür, ölçeklendirilir ve yeniden kodlanır. (Blok tabanlı sıkıştırma yapısı, ek kod çözme-kodlama işleminin neredeyse her zaman daha önce kodlanmayan bir dokusunun ölçeklendirilen sürümünden oluşturulduğu zaman daha düşük görüntü kalitesine neden olur.)  
  
  Doku için MIP eşlemeleri etkinleştirilmişse, varyant, MIP düzeylerinin sayısını buna uygun şekilde azaltır; çeyrek boyutuna ölçeklendirirken yarı boyutlu veya iki daha az ölçeklendirirken bir daha az.  
  
## <a name="example"></a>Örnek  
 Bu varyant, çağrısından önce çalışma zamanında dokuları yeniden boyutlandırır `CreateTexture2D` . Tam boyutlu dokular daha fazla disk alanı kullandığından ve ek adım uygulamanızdaki yükleme sürelerini arttıracağından ve özellikle de daha fazla bilgi işlem kaynakları kodlamak için önemli bir hesaplama kaynağı gerektiren, üretim kodu için bu yaklaşıma önerilir. Bunun yerine, yapı işlem hattınızın bir parçası olan bir görüntü Düzenleyicisi veya görüntü işlemcisi kullanarak dokularınızı çevrimdışı olarak yeniden boyutlandırmanızı öneririz. Bu yaklaşımlar, disk alanı gereksinimlerini azaltır ve uygulamanızda çalışma zamanı ek yükünü ortadan kaldırır ve dokularınızı küçülterek veya sıkıştırırken en iyi görüntü kalitesini sürdürebilmeniz için daha fazla işleme süresi elde edebilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [MİP eşleme oluşturma varyantı](../debugger/mip-map-generation-variant.md)   
 [BC Doku Sıkıştırma Çeşidi](../debugger/bc-texture-compression-variant.md)
