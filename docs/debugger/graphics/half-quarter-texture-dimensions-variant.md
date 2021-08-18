---
title: Half-Quarter Doku Boyutları Varyantı | Microsoft Docs
description: Daha küçük dokular büyük performans kazancı gösteriyorsa, bellek bant genişliği baskısı veya GPU doku önbelleğinin verimsiz kullanımı önerebilir. Doku boyutlarını küçültmeyi göz önünde bulundurabilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 282e9bbb-51aa-4cd0-8e5c-0901268c29e5
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 815623537a8ac9f038f5405f7c8d11c1d55de8ab
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122121017"
---
# <a name="halfquarter-texture-dimensions-variant"></a>Yarı/Çeyrek Doku Boyutları Çeşidi
Hedef işlemeden doku boyutlarını azaltır.

## <a name="interpretation"></a>Yorum
 Daha küçük dokular daha az bellek kaplar ve bu nedenle daha az bellek bant genişliği tüketir ve GPU'nun doku önbelleği üzerindeki baskıyı azaltır. Ancak, daha az ayrıntısı, özellikle de 3-D sahnesinde yakından görüntülendiklerinde veya büyüteç altında görüntülendiklerinde görüntü kalitesinin azalmasına neden olabilir.

 Bu değişken büyük bir performans kazancı gösteriyorsa, bu durum, uygulamanın çok fazla bellek bant genişliği kullandığını, doku önbelleğini verimsiz kullandığını veya her ikisini birden kullandığını gösteriyor olabilir. Ayrıca dokuların kullanılabilir olandan daha fazla GPU belleği kaplasa da dokuların sistem belleğine sayfalandırılana neden olduğunu gösterir.

 Uygulamanız çok fazla bellek bant genişliği kullanıyorsa veya doku önbelleğini verimsiz kullanıyorsa dokularının boyutunu azaltmayı göz önünde bulundurabilirsiniz ancak uygun dokular için mip eşlemelerini etkinleştirmeyi göz önünde bulundurduktan sonra. Daha küçük dokular gibi, mip ile eşlenen dokular da daha fazla GPU belleği kapsasa da daha az bellek bant genişliği tüketir ve önbellek kullanımını artırır ancak doku ayrıntısını azaltmaz. Artan bellek kullanımı dokuların sistem belleğine çağrıl kullanılmasına neden oluşturmazsa mip eşlemelerini öneririz.

 Dokular kullanılabilir olandan daha fazla GPU belleği kaplarsa dokuların boyutunu azaltmayı ancak uygun dokuları sıkıştırmayı göz önünde bulundurarak azaltmayı göz önünde bulundurabilirsiniz. Daha küçük dokular gibi sıkıştırılmış dokular da daha az bellek kaplar ve sistem belleğine sayfa ekleme ihtiyacı azalır, ancak renk uygunlukları azalır. Sıkıştırma, içeriğine bağlı olarak (örneğin, küçük bir alanda önemli renk varyasyonu olan dokular) tüm dokular için uygun değildir, ancak birçok doku için sıkıştırma, boyutlarını azaltmaktan daha iyi genel görüntü kalitesini koruyabilirsiniz.

## <a name="remarks"></a>Açıklamalar
 Doku boyutları, kaynak doku oluşturan her `ID3D11Device::CreateTexture2D` çağrısında azaltıldı. Özellikle, içinde geçirilen D3D11_TEXTURE2D_DESC işlemede kullanılan dokuyu açıksa doku boyutları `pDesc` azalır; yani:

- BindFlags üyesinin yalnızca D3D11_BIND_SHADER_RESOURCE ayarlanmıştır.

- MiscFlags üyesi, D3D11_RESOURCE_MISC_TILE_POOL bayrağına veya D3D11_RESOURCE_MISC_TILED bayrağı kümesine sahip değildir (kutucuklı kaynaklar yeniden boyutlandırılmaz).

- Doku biçimi, doku boyutunu azaltmak için gerekli olan D3D11_FORMAT_SUPPORT_RENDER_TARGET tarafından belirlenen işleme hedefi olarak de desteklemektedir. BC1, BC2 ve BC3 biçimleri, işleme hedefleri olarak desteklense de de de desteklenir.

  İlk veriler uygulama tarafından sağlanırsa, bu değişken dokuyu oluşturana kadar doku verilerini uygun boyuta ölçeklendirer. İlk veriler BC1, BC2 veya BC3 gibi blok sıkıştırılmış biçimde sağlanırsa, daha küçük dokuyu oluşturmak için kullanılmadan önce kodu çözülür, ölçeklendirılır ve yeniden kodlanmış olur. (Blok tabanlı sıkıştırmanın doğası, fazladan kod çözme-ölçek kodlama işleminin neredeyse her zaman daha önce kodlanmamış dokunun ölçeklendirılmış bir sürümünden blok sıkıştırılmış doku oluşturmadan daha düşük görüntü kalitesine neden olduğu anlamına gelir.)

  Doku için mip eşlemeleri etkinleştirildiyse değişken, çeyrek boyutuna ölçeklendirildiğinde mip düzeylerinin sayısını buna göre azaltır; yarı boyuta ölçeklendirildiğinde bir veya iki kat daha az olur.

## <a name="example"></a>Örnek
 Bu değişken, çalışma zamanında dokuları çağrısının öncesinde yeniden `CreateTexture2D` boyutlandırıyor. Tam boyutlu dokular daha fazla disk alanı tükettiği ve ek adımın uygulamanıza yükleme sürelerini artıra bilhassa sıkıştırılmış dokular için kodlanması gereken sıkıştırılmış dokular için bu yaklaşıma karşı önerilir. Bunun yerine, derleme işlem hattınıza bir parçası olan görüntü düzenleyicisi veya görüntü işlemcisi kullanarak dokularınızı çevrimdışı olarak yeniden boyutlandırmanızı öneririz. Bu yaklaşımlar disk alanı gereksinimlerini azaltır, uygulamanıza çalışma zamanı yükünü ortadan kaldırmak ve dokularınızı küçültürken veya sıkıştırırken en iyi görüntü kalitesini koruyabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [Mip-map Oluşturma Çeşidi](mip-map-generation-variant.md)
- [BC Doku Sıkıştırma Çeşidi](bc-texture-compression-variant.md)