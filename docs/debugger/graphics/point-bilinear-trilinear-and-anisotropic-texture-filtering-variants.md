---
title: Point/Bilinear/trilinear/anısotropıc doku filtresi çeşitleri
description: Bir noktanın performans maliyeti, Bilinear, trilinear veya anısotropıc doku filtreleme varyantı önemli ise, kullanım süresinin maliyete değer olup olmadığını göz önünde bulundurun.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 57d14fc9-b5f7-45ee-9717-48086886742d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: bdec03536054c5f4380fc1412ff192e34b343bdd
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122154089"
---
# <a name="point-bilinear-trilinear-and-anisotropic-texture-filtering-variants"></a>Nokta, Çift Doğrusal, Üçlü Doğrusal ve Yön Bağımlı Doku Filtreleme Çeşitleri
Uygun doku örnekleyicileri için filtreleme modunu geçersiz kılar.

## <a name="interpretation"></a>Yorum
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
 Direct3D 'de, özellik düzeyi 9,1, 2x bir en yüksek anizedetrou belirtir. **Anısotropıc dokusu filtreleme** değişkeni, tek başına 16X aniztroa 'yı kullanmayı denetiğinden, bir özellik düzeyi 9,1 cihazında Çerçeve Analizi çalıştırıldığında kayıttan yürütme başarısız olur. bu sınırlamanın etkilediği modern cihazlar ARM tabanlı yüzey RT ve surface 2 Windows tabletlerini içerir. Bazı bilgisayarlarda hala bulunan daha eski GPU 'Lar de etkilenebilir, ancak artık kullanılmıyor ve giderek daha sık görülen bir durumdur.

## <a name="example-1"></a>Örnek 1
 **Nokta dokusu filtreleme** değişkeni aşağıdaki gibi kod kullanılarak yeniden oluşturulabilir:

```cpp
D3D11_SAMPLER_DESC sampler_description;

// ... other sampler description setup ...

sampler_description.Filter = D3D11_FILTER_MIN_MAG_MIP_POINT;

d3d_device->CreateSamplerState(&sampler_desc, &sampler);
d3d_context->PSSetSamplers(0, 1, &sampler
```

## <a name="example-2"></a>Örnek 2
 **Bilinear doku filtreleme** değişkeni aşağıdaki gibi kod kullanılarak yeniden oluşturulabilir:

```cpp
D3D11_SAMPLER_DESC sampler_description;

// ... other sampler description setup ...

sampler_description.Filter = D3D11_FILTER_MIN_MAG_LINEAR_MIP_POINT;

d3d_device->CreateSamplerState(&sampler_desc, &sampler);
d3d_context->PSSetSamplers(0, 1, &sampler
```

## <a name="example-3"></a>Örnek 3
 **Trilinear doku filtreleme** değişkeni aşağıdaki gibi kod kullanılarak yeniden oluşturulabilir:

```cpp
D3D11_SAMPLER_DESC sampler_description;

// ... other sampler description setup ...

sampler_description.Filter = D3D11_FILTER_MIN_MAG_MIP_LINEAR;

d3d_device->CreateSamplerState(&sampler_desc, &sampler);
d3d_context->PSSetSamplers(0, 1, &sampler
```

## <a name="example-4"></a>Örnek 4
 **Anısotropıc doku filtreleme** değişkeni, şunun gibi kod kullanılarak yeniden oluşturulabilir:

```cpp
D3D11_SAMPLER_DESC sampler_description;

// ... other sampler description setup ...

sampler_description.Filter = D3D11_FILTER_ANISOTROPIC;
sampler_description.MaxAnisotropy = 16;

d3d_device->CreateSamplerState(&sampler_desc, &sampler);
d3d_context->PSSetSamplers(0, 1, &sampler
```
