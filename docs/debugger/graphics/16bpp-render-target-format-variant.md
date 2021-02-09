---
title: 16bpp Işleme hedefi biçim değişkeni | Microsoft Docs
description: Piksel biçimini tüm işleme hedefleri ve geri arabellekler için DXGI_FORMAT_B5G6R5_UNORM olarak ayarlayarak 16 bit/piksel (BPP) işleme hedefi biçim türevini uygulayın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 24b22ad9-5ad0-4161-809a-9b518eb924bf
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6d0f43e2b004272b6882ff4a19e62fa99c998e53
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874632"
---
# <a name="16-bpp-render-target-format-variant"></a>16 BPP Işleme hedefi biçim değişkeni
Tüm işleme hedefleri ve geri arabellekler için piksel biçimini DXGI_FORMAT_B5G6R5_UNORM olarak ayarlar.

## <a name="interpretation"></a>Yorum
 Bir işleme hedefi veya arka arabellek, genellikle B8G8R8A8_UNORM gibi bir 32 BPP (piksel başına 32 bit) biçimi kullanır. 32-BPP biçimleri büyük miktarda bellek bant genişliği kullanabilir. B5G6R5_UNORM biçimi 32-BPP biçimlerin yarısı olan 16-BPP bir biçim olduğundan, bu, kullanılması bellek bant genişliğine göre azalmayı, ancak azaltılmış renk uygunluğuna karşı düşürebilir.

 Bu çeşit büyük bir performans kazancı gösteriyorsa, büyük olasılıkla uygulamanızın çok fazla bellek bant genişliği tükettiğini gösterir. Özellikle, profili oluşturulan çerçevede önemli miktarda fazla çizim veya Alfa karışımı olduğunda önemli performans artışı elde edebilirsiniz.

Bir 16 bit işleme hedefi biçimi, uygulamanız aşağıdaki koşullara sahip olduğunda kullanım ile bellek bantlarını azaltabilir:
- Yüksek uygunluğa sahip bir renk üretilmesi gerektirmez.
- Bir alfa kanalı gerektirmez.
- Genellikle düzgün gradyanlar yoktur (Bu, azaltılmış renk uygunlukta bant yapılarına açıktır).

Bellek bant genişliğini azaltmaya yönelik diğer stratejiler şunlardır:
- Fazla çizim veya alfa karıştırma miktarını azaltın.
- Çerçeve arabelleğinin boyutlarını küçültün.
- Doku kaynaklarının boyutlarını küçültün.
- Doku kaynaklarının sıkıştırmaları azalır.

Her zamanki gibi, bu iyileştirmelerin herhangi biriyle birlikte gelen görüntü kalitesi dengelerini göz önünde bulundurmanız gerekir.

Takas zincirinin bir parçası olan uygulamaların, 16 BPP desteklemeyen bir arka arabellek biçimi (DXGI_FORMAT_B5G6R5_UNORM) vardır. Bu değiştirme zincirleri veya kullanılarak oluşturulur `D3D11CreateDeviceAndSwapChain` `IDXGIFactory::CreateSwapChain` . Bu kısıtlamayı geçici olarak çözmek için aşağıdaki adımları uygulayın:
1. Kullanarak bir B5G6R5_UNORM biçim oluşturma hedefi oluşturun `CreateTexture2D` ve bu hedefe işlenir.
2. Kaynak dokunuz olarak işleme hedefini bir tam ekran dörtlü çizerek, işleme hedefini takas zinciri biriktirme arabelleği üzerine kopyalayın.
3. Takas zincirinizdeki çağrı var.

   Bu strateji, işleme hedefini takas zinciri biriktirme arabelleğine kopyalayarak tüketildiğinden daha fazla bant genişliği kaydederse, işleme performansı geliştirildi.

   Döşenmiş işleme tekniklerini kullanan GPU mimarileri, 16 BPP çerçeve arabelleği biçimi kullanarak önemli performans avantajlarını görebilirler. Bu geliştirme, çerçeve arabelleğinin daha büyük bir kısmının her bir kutucuğun yerel çerçeve arabelleği önbelleğine sığabileceğinden oluşur. Döşenmiş işleme mimarileri, bazen mobil eller ve tablet bilgisayarlardaki GPU 'Larda bulunur; Bu Niche dışında nadiren görünürler.

## <a name="remarks"></a>Açıklamalar
 İşleme hedefi biçimi, işleme hedefi oluşturan her çağrıda DXGI_FORMAT_B5G6R5_UNORM sıfırlanır `ID3D11Device::CreateTexture2D` . Özellikle, pDesc içinde geçirilen D3D11_TEXTURE2D_DESC nesne bir işleme hedefini açıkladığı zaman biçim geçersiz kılınır; Yani:

- BindFlags üyesinin D3D11_BIND_REDNER_TARGET bayrak kümesi vardır.

- BindFlags üyesi D3D11_BIND_DEPTH_STENCIL bayrağını temizledi.

- Kullanım üyesi D3D11_USAGE_DEFAULT olarak ayarlanır.

## <a name="restrictions-and-limitations"></a>Kısıtlamalar ve sınırlamalar
 B5G6R5 biçiminde bir alfa kanalı olmadığından, Alfa içeriği bu değişken tarafından korunmaz. Uygulamanızın işleme, oluşturma hedefinde bir alfa kanalı gerektiriyorsa, yalnızca B5G6R5 biçimine geçiş yapamazsınız.

## <a name="example"></a>Örnek
 Aşağıdaki gibi kodla kullanılarak oluşturulan işleme hedefleri için **16 BPP Işleme hedefi biçim** değişkeni yeniden oluşturulabilir `CreateTexture2D` :

```cpp
D3D11_TEXTURE2D_DESC target_description;

target_description.BindFlags = D3D11_BIND_RENDER_TARGET;
target_description.Format = DXGI_FORMAT_B5G6R5_UNORM;
d3d_device->CreateTexture2D(&target_description, nullptr, &render_target);
```
