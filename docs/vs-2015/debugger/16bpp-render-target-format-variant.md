---
title: 16bpp Işleme hedefi biçim değişkeni | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 24b22ad9-5ad0-4161-809a-9b518eb924bf
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7b315c7ab9bb10d039e81ba26b1beb9c4447a205
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157566"
---
# <a name="16bpp-render-target-format-variant"></a>16bpp İşleme Hedef Biçim Çeşidi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tüm işleme hedefleri ve geri arabellekler için piksel biçimini DXGI_FORMAT_B5G6R5_UNORM olarak ayarlar.  
  
## <a name="interpretation"></a>Yorumlama  
 Bir işleme hedefi veya arka arabellek genellikle B8G8R8A8_UNORM gibi bir 32bpp (piksel başına 32 bit) biçimi kullanır. 32bpp biçimleri çok fazla bellek bant genişliği kullanabilir. B5G6R5_UNORM biçimi, 32bpp biçimlerinin yarısı olan bir 16bpp biçim olduğundan, bunu kullanmak bellek bant genişliğine göre azalmayı, ancak azaltılmış renk uygunluğuna karşı düşürebilir.  
  
 Bu çeşit büyük bir performans kazancı gösteriyorsa, büyük olasılıkla uygulamanızın çok fazla bellek bant genişliği tükettiğini gösterir. Profil oluşturma çerçevesi, çok fazla sayıda fazla çizmeden veya çok sayıda Alfa karışımı içerdiğinde, özellikle de kullanılabilir.  
  
 Uygulamanız tarafından işlenen sahne türleri için yüksek uygunlukta renk üretilmesi gerekmiyorsa, işleme hedefinin bir alfa kanalına sahip olmasını gerektirmez ve genellikle düşük renk uygunluğu altında bant yapıtlarına açıktır olan kesintisiz degradeler kullanmayın; bellek bant genişliği kullanımını azaltmak için bir 16bpp işleme hedefi biçimi kullanmayı düşünün.  
  
 Uygulamanızda işlenen sahneler, Yüksek uygunluğa sahip bir renk üretilmesi veya bir alfa kanalı gerektiriyorsa ya da düzgün degradeler ortak ise, bellek bant genişliği kullanımını azaltmaya yönelik diğer stratejileri göz önünde bulundurun — Örneğin, fazla çizim veya alfa karıştırma miktarını azaltma, framebuffer boyutlarını azaltma veya doku kaynaklarını daha az bellek bant genişliği tüketerek boyutları azaltma veya boyutlarını azaltma. Her zamanki gibi, bu iyileştirmelerin herhangi biriyle birlikte gelen görüntü kalitesi dengelerini göz önünde bulundurmanız gerekir.  
  
 Uygulamanızın bir 16bpp geri arabelleğine geçiş yapma avantajı olsa da, takas zincirinizin bir parçası olduğu için DXGI_FORMAT_B5G6R5_UNORM, veya kullanılarak oluşturulan takas zincirlerinin desteklenen bir geri arabellek biçimi olmadığından ek adımlar gerçekleştirmeniz gerekir `D3D11CreateDeviceAndSwapChain` `IDXGIFactory::CreateSwapChain` . Bunun yerine, kullanarak B5G6R5_UNORM bir biçim oluşturma hedefi oluşturmanız `CreateTexture2D` ve bunu bunun yerine işlemek zorunda olmanız gerekir. Daha sonra, takas zincirinizde çağırmadan önce, kaynak dokunuz olarak işleme hedefi ile bir tam ekran dörtlü çizerek işleme hedefini takas zinciri biriktirme arabelleği üzerine kopyalayın. Bu, bazı bellek bant genişliğine sahip olacak ek bir adım olmakla birlikte, en fazla işleme işlemi 16bpp işleme hedefini etkilediği için daha az bant genişliği tüketir; Bu işlem, işleme hedefini takas zinciri biriktirme arabelleğine kopyalayarak tüketildiğinden daha fazla bant genişliği kaydederse, işleme performansı geliştirildi.  
  
 Çerçeve arabelleğinin daha büyük bir bölümü her bir kutucuğun yerel framebuffer önbelleğine sığabileceğinden, döşenmiş işleme tekniklerini kullanan GPU mimarileri, bir 16bpp framebuffer biçimi kullanarak önemli performans avantajlarını görebilirler. Döşenmiş işleme mimarileri, bazen mobil eller ve tablet bilgisayarlardaki GPU 'Larda bulunur; Bu Niche dışında nadiren görünürler.  
  
## <a name="remarks"></a>Açıklamalar  
 İşleme hedefi biçimi, işleme hedefi oluşturan her çağrıda DXGI_FORMAT_B5G6R5_UNORM sıfırlanır `ID3D11Device::CreateTexture2D` . Özellikle, pDesc içinde geçirilen D3D11_TEXTURE2D_DESC nesne bir işleme hedefini açıkladığı zaman biçim geçersiz kılınır; Yani:  
  
- BindFlags üyesinin D3D11_BIND_REDNER_TARGET bayrak kümesi vardır.  
  
- BindFlags üyesi D3D11_BIND_DEPTH_STENCIL bayrağını temizledi.  
  
- Kullanım üyesi D3D11_USAGE_DEFAULT olarak ayarlanır.  
  
## <a name="restrictions-and-limitations"></a>Kısıtlamalar ve sınırlamalar  
 B5G6R5 biçiminde bir alfa kanalı olmadığından, Alfa içeriği bu değişken tarafından korunmaz. Uygulamanızın işleme, oluşturma hedefinde bir alfa kanalı gerektiriyorsa, yalnızca B5G6R5 biçimine geçiş yapamazsınız.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki gibi kodla kullanılarak oluşturulan işleme hedefleri için **16bpp Işleme hedefi biçim** değişkeni yeniden oluşturulabilir `CreateTexture2D` :  
  
```  
D3D11_TEXTURE2D_DESC target_description;  
  
target_description.BindFlags = D3D11_BIND_RENDER_TARGET;  
target_description.Format = DXGI_FORMAT_B5G6R5_UNORM;  
d3d_device->CreateTexture2D(&target_description, nullptr, &render_target);  
```
