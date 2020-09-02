---
title: Point/Bilinear/trilinear/anısotropıc doku filtresi çeşitleri
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 57d14fc9-b5f7-45ee-9717-48086886742d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 314ec61da7ed61cc8bdd573e201d98a53862a32c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "66262927"
---
# <a name="point-bilinear-trilinear-and-anisotropic-texture-filtering-variants"></a>Nokta, Çift Doğrusal, Üçlü Doğrusal ve Yön Bağımlı Doku Filtreleme Çeşitleri
Uygun doku örnekleyicileri için filtreleme modunu geçersiz kılar.

## <a name="interpretation"></a>Yorumlama
 Farklı doku örnekleme yöntemleri farklı performans maliyetlerine ve görüntü kalitesine sahiptir. Maliyet artırma ve görsel kaliteyi artırma gibi — filtre modları şunlardır:

1. Nokta filtreleme (en az pahalı, en kötü görsel kalite)

2. Bilinear filtrelemesi

3. Trilinear filtrelemesi

4. Anısotropıc filtrelemesi (en pahalı, en iyi görsel kalite)

   Her bir varyantın performans maliyeti, daha yoğun filtreleme modlarıyla önemli veya artıyorsa maliyeti artan görüntü kalitesiyle karşılaştırın. Değerlendirmenize göre, görsel kaliteyi artırmak için ek performans maliyetlerini kabul edebilir veya daha yüksek bir kare hızına ulaşmak veya daha fazla şekilde kullanabileceğiniz performansı geri kazanmak için azalan görsel kaliteyi kabul edebilirsiniz.

   Filtreleme modundan bağımsız olarak performans maliyetinin göz ardı edilebilir veya kararlı olduğunu fark ederseniz — Örneğin, hedeflediğiniz GPU, gölgelendirici işleme ve bellek bant genişliğine sahip olduğunda, uygulamanızdaki en iyi görüntü kalitesini elde etmek için anısotropıc filtrelemeyi kullanmayı düşünün.

## <a name="remarks"></a>Açıklamalar
 Bu çeşitler, `ID3D11DeviceContext::PSSetSamplers` uygulama tarafından belirtilen örnekleyici filtre modunun bunlardan biri olduğu çağrılarında örnekleyici durumlarını geçersiz kılar:

- `D3D11_FILTER_MIN_MAG_MIP_POINT`

- `D3D11_FILTER_MIN_MAG_POINT_MIP_LINEAR`

- `D3D11_FILTER_MIN_POINT_MAG_LINEAR_MIP_POINT`

- `D3D11_FILTER_MIN_POINT_MAG_MIP_LINEAR`

- `D3D11_FILTER_MIN_LINEAR_MAG_MIP_POINT`

- `D3D11_FILTER_MIN_LINEAR_MAG_POINT_MIP_LINEAR`

- `D3D11_FILTER_MIN_MAG_LINEAR_MIP_POINT`

- `D3D11_FILTER_MIN_MAG_MIP_LINEAR`

- `D3D11_FILTER_ANISOTROPIC`

  **Nokta dokusu filtreleme** çeşidinde, uygulama tarafından sunulan filtre modu ile değiştirilmiştir `D3D11_FILTER_MIN_MAG_MIP_POINT` ; **Bilinear doku filtreleme** çeşidinde, Ile değiştirilmiştir `D3D11_FILTER_MIN_MAG_LINEAR_MIP_POINT` ve **trilinear doku filtreleme** çeşidinde ile değiştirilmiştir `D3D11_FILTER_MIN_MAG_MIP_LINEAR` .

  **Anısotropıc doku filtreleme** çeşidinde, uygulama tarafından sağlanmış filtre modu ile değiştirilmiştir `D3D11_FILTER_ANISOTROPIC` ve en yüksek Anısotrokopyala 16 olarak ayarlanır.

## <a name="restrictions-and-limitations"></a>Kısıtlamalar ve sınırlamalar
 Direct3D 'de, özellik düzeyi 9,1, 2x bir en yüksek anizedetrou belirtir. **Anısotropıc dokusu filtreleme** değişkeni, tek başına 16X aniztroa 'yı kullanmayı denetiğinden, bir özellik düzeyi 9,1 cihazında Çerçeve Analizi çalıştırıldığında kayıttan yürütme başarısız olur. Bu sınırlamanın etkilediği modern cihazlar ARM tabanlı Surface RT ve Surface 2 Windows tabletlerini içerir. Bazı bilgisayarlarda hala bulunan daha eski GPU 'Lar de etkilenebilir, ancak artık kullanılmıyor ve giderek daha sık görülen bir durumdur.

## <a name="example"></a>Örnek
 **Nokta dokusu filtreleme** değişkeni aşağıdaki gibi kod kullanılarak yeniden oluşturulabilir:

```cpp
D3D11_SAMPLER_DESC sampler_description;

// ... other sampler description setup ...

sampler_description.Filter = D3D11_FILTER_MIN_MAG_MIP_POINT;

d3d_device->CreateSamplerState(&sampler_desc, &sampler);
d3d_context->PSSetSamplers(0, 1, &sampler
```

## <a name="example"></a>Örnek
 **Bilinear doku filtreleme** değişkeni aşağıdaki gibi kod kullanılarak yeniden oluşturulabilir:

```cpp
D3D11_SAMPLER_DESC sampler_description;

// ... other sampler description setup ...

sampler_description.Filter = D3D11_FILTER_MIN_MAG_LINEAR_MIP_POINT;

d3d_device->CreateSamplerState(&sampler_desc, &sampler);
d3d_context->PSSetSamplers(0, 1, &sampler
```

## <a name="example"></a>Örnek
 **Trilinear doku filtreleme** değişkeni aşağıdaki gibi kod kullanılarak yeniden oluşturulabilir:

```cpp
D3D11_SAMPLER_DESC sampler_description;

// ... other sampler description setup ...

sampler_description.Filter = D3D11_FILTER_MIN_MAG_MIP_LINEAR;

d3d_device->CreateSamplerState(&sampler_desc, &sampler);
d3d_context->PSSetSamplers(0, 1, &sampler
```

## <a name="example"></a>Örnek
 **Anısotropıc doku filtreleme** değişkeni, şunun gibi kod kullanılarak yeniden oluşturulabilir:

```cpp
D3D11_SAMPLER_DESC sampler_description;

// ... other sampler description setup ...

sampler_description.Filter = D3D11_FILTER_ANISOTROPIC;
sampler_description.MaxAnisotropy = 16;

d3d_device->CreateSamplerState(&sampler_desc, &sampler);
d3d_context->PSSetSamplers(0, 1, &sampler
```
