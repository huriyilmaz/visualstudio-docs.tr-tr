---
title: Nokta/bilinear/trilinear/anisotropik doku filtresi varyantları
description: Bir noktanın, bilinear, trilinear veya anisotropik doku filtreleme varyantının performans maliyeti önemli ise, kullanımının maliyete değer olup oalcağını göz önünde bulundurabilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 57d14fc9-b5f7-45ee-9717-48086886742d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0d89db195b94bcf31d2ce2c7482c5b7315a979e9
ms.sourcegitcommit: aeed3eb503d0b282537b073ebae8c028c4fef750
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/15/2021
ms.locfileid: "114232654"
---
# <a name="point-bilinear-trilinear-and-anisotropic-texture-filtering-variants"></a>Nokta, Çift Doğrusal, Üçlü Doğrusal ve Yön Bağımlı Doku Filtreleme Çeşitleri
Uygun doku örnekleyicilerde filtreleme modunu geçersiz kılar.

## <a name="interpretation"></a>Yorum
 Farklı doku örnekleme yöntemleri farklı performans maliyetlerine ve görüntü kalitesine sahiptir. Maliyeti ve görsel kalitesini artırmak için filtre modları şu şekildedir:

1. Nokta filtreleme (en düşük maliyetli, en kötü görsel kalitesi)

2. Bilinear filtreleme

3. Trilinear filtreleme

4. Anisotropik filtreleme (en pahalı, en iyi görsel kalitesi)

   Her varyantın performans maliyeti önemli olursa veya daha yoğun filtreleme modlarıyla artarsa, bunun maliyetini artan görüntü kalitesine göre ölçebilirsiniz. Değerlendirmenize bağlı olarak, görsel kalitesini artırmak için ek performans maliyetleri kabul edilebilir veya daha yüksek bir kare hızı elde etmek veya başka yollarla kullanabileceğiniz performansı geri elde etmek için görsel kalitesinin azalmalarını kabul etmiş oluruz.

   Filtreleme modundan bağımsız olarak performans maliyetinin göz ardı edilebilir veya sabit olduğunu bulursanız (örneğin, hedeflemekte olduğu GPU'da gölgelendirici aktarım hızı ve bellek bant genişliği bolluğu olduğunda) uygulamanıza en iyi görüntü kalitesini elde etmek için anisotropik filtrelemeyi kullanmayı göz önünde bulundurabilirsiniz.

## <a name="remarks"></a>Açıklamalar
 Bu çeşitler, uygulama tarafından sağlanan örnekleyicinin filtre modunun bunlardan biri olduğu çağrılarda örnekleyici `ID3D11DeviceContext::PSSetSamplers` durumları geçersiz kılar:

- `D3D11_FILTER_MIN_MAG_MIP_POINT`

- `D3D11_FILTER_MIN_MAG_POINT_MIP_LINEAR`

- `D3D11_FILTER_MIN_POINT_MAG_LINEAR_MIP_POINT`

- `D3D11_FILTER_MIN_POINT_MAG_MIP_LINEAR`

- `D3D11_FILTER_MIN_LINEAR_MAG_MIP_POINT`

- `D3D11_FILTER_MIN_LINEAR_MAG_POINT_MIP_LINEAR`

- `D3D11_FILTER_MIN_MAG_LINEAR_MIP_POINT`

- `D3D11_FILTER_MIN_MAG_MIP_LINEAR`

- `D3D11_FILTER_ANISOTROPIC`

  Nokta **Doku** Filtreleme çeşidinde, uygulama tarafından sağlanan filtre modu ile `D3D11_FILTER_MIN_MAG_MIP_POINT` değiştirilir; **Bilinear Doku** Filtreleme çeşidinde ile değiştirilir `D3D11_FILTER_MIN_MAG_LINEAR_MIP_POINT` ve **Trilinear Doku** Filtreleme varyantı'nın yerine ile `D3D11_FILTER_MIN_MAG_MIP_LINEAR` değiştirilir.

  **Anisotropik Doku** Filtreleme çeşidinde, uygulama tarafından sağlanan filtre modu ile değiştirilir ve `D3D11_FILTER_ANISOTROPIC` Maksimum Anisotropi 16 olarak ayarlanır.

## <a name="restrictions-and-limitations"></a>Kısıtlamalar ve sınırlamalar
 Direct3D'de özellik düzeyi 9.1, maksimum anisotropiyi 2x olarak belirtir. **Anisotropik Doku** Filtreleme varyantı özel olarak 16x anisotropi kullanmayı denemesi nedeniyle, özellik düzeyi 9.1 cihazında kare analizi çalıştır çalıştırılana kayıttan yürütme başarısız olur. Bu sınırlamadan etkilenen cihazlar ARM tabanlı Surface RT ve Surface 2 ve tabletler arasında Windows içerir. Bazı bilgisayarlarda hala buluna eski GPU'lar da etkilenebilir, ancak yaygın olarak eski olduğu kabul edilir ve giderek daha yaygındır.

## <a name="example-1"></a>Örnek 1
 Nokta **Doku Filtreleme varyantı** aşağıdaki gibi bir kod kullanılarak yeniden üretebilirsiniz:

```cpp
D3D11_SAMPLER_DESC sampler_description;

// ... other sampler description setup ...

sampler_description.Filter = D3D11_FILTER_MIN_MAG_MIP_POINT;

d3d_device->CreateSamplerState(&sampler_desc, &sampler);
d3d_context->PSSetSamplers(0, 1, &sampler
```

## <a name="example-2"></a>Örnek 2
 **Bilinear Doku Filtreleme** varyantı aşağıdaki gibi kod kullanılarak yeniden üretebilirsiniz:

```cpp
D3D11_SAMPLER_DESC sampler_description;

// ... other sampler description setup ...

sampler_description.Filter = D3D11_FILTER_MIN_MAG_LINEAR_MIP_POINT;

d3d_device->CreateSamplerState(&sampler_desc, &sampler);
d3d_context->PSSetSamplers(0, 1, &sampler
```

## <a name="example-3"></a>Örnek 3
 **Trilinear Doku Filtreleme varyantı** aşağıdaki gibi kod kullanılarak yeniden üretebilirsiniz:

```cpp
D3D11_SAMPLER_DESC sampler_description;

// ... other sampler description setup ...

sampler_description.Filter = D3D11_FILTER_MIN_MAG_MIP_LINEAR;

d3d_device->CreateSamplerState(&sampler_desc, &sampler);
d3d_context->PSSetSamplers(0, 1, &sampler
```

## <a name="example-4"></a>Örnek 4
 **Anisotropik Doku Filtreleme** varyantı aşağıdaki gibi kod kullanılarak yeniden üretılabilir:

```cpp
D3D11_SAMPLER_DESC sampler_description;

// ... other sampler description setup ...

sampler_description.Filter = D3D11_FILTER_ANISOTROPIC;
sampler_description.MaxAnisotropy = 16;

d3d_device->CreateSamplerState(&sampler_desc, &sampler);
d3d_context->PSSetSamplers(0, 1, &sampler
```
