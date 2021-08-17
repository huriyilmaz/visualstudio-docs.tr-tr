---
title: 0x-2x-4x MSAA Varyantları | Microsoft Docs
description: 0x, 2x veya 4x MSAA çeşitlemelerini kullanarak tüm işleme hedeflerinde ve takas zincirlerinde çok örnekli diğer ad koruma (MSAA) ayarlarını geçersiz kılmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 668a6603-5082-4c78-98e6-f3dc871aa55b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 60133b32d65adc3f58dc430b1fe2d4ae9e5f91e4
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122074370"
---
# <a name="0x2x4x-msaa-variants"></a>0x/2x/4x MSAA Çeşitleri
Tüm işleme hedeflerinde ve değiştirme zincirlerinde çok örnekli diğer ad koruma (MSAA) ayarlarını geçersiz kılar.

## <a name="interpretation"></a>Yorum
 Çok örnekli diğer addan koruma, örnekleri her pikselde birden çok konumda alarak görsel kalitesini artırır; daha yüksek MSAA düzeyleri daha fazla örnek alır ve MSAA olmadan pikselin merkezinden yalnızca bir örnek alınır. Uygulamanıza MSAA'nın etkinleştirilmesi genellikle performansın düşük ancak fark edilebilir bir maliyeti olur, ancak belirli iş yüklerinde veya belirli GPU'larda neredeyse hiç etkisi olmaz.

 Uygulamanıza MSAA zaten etkinleştirilmişse, daha az MSAA varyantları, mevcut, daha üst düzey MSAA'nın sahip olduğu göreli performans maliyetini gösterir. Özellikle 0x MSAA varyantı, MSAA olmadan uygulamanın göreli performansını gösterir.

 Uygulamanız MSAA'yı henüz etkinleştirmediyse, 2x MSAA ve 4x MSAA çeşitlemeleri, uygulamanıza bunları etkinleştirmenin göreli performans maliyetini gösterir. Maliyet kabul edilebilir ölçüde düşük olduğunda, MSAA'yı etkinleştirerek uygulamanın görüntü kalitesini geliştirmeyi göz önünde bulundurabilirsiniz.

> [!NOTE]
> Donanımınız tüm biçimler için MSAA'yı tam olarak desteklemeyebilirsiniz. Bu varyantlardan herhangi biri üzerinde çalışılamaz bir donanım sınırlaması ile karşılaşırsa, performans özeti tablosunda sütunu boştur ve bir hata iletisi üretir.

## <a name="remarks"></a>Açıklamalar
 Bu çeşitlemeler, işleme hedefleri oluşturmak için yapılan çağrılarda örnek sayısını ve `ID3DDevice::CreateTexture2D` örnek kalitesi bağımsız değişkenlerini geçersiz kılar. Özellikle, bu parametreler şu olduğunda geçersiz kılınır:

- geçirilen `D3D11_TEXTURE2D_DESC` nesne `pDesc` bir işleme hedefini açıklar; yani:

  - BindFlags üyesi, D3D11_BIND_TARGET bayrağına veya D3D11_BIND_DEPTH_STENCIL bayrağına sahip.

  - Kullanım üyesi, D3D11_USAGE_DEFAULT.

  - CPUAccessFlags üyesi 0 olarak ayarlanır.

  - MipLevels üyesi 1 olarak ayarlanır.

- Cihaz, tarafından belirlenen istenen işleme hedefi biçimi (D3D11_TEXTURE2D_DESC::Format üyesi) için istenen örnek sayısını (0, 2 veya 4) ve örnek kalitesini (0) `ID3D11Device::CheckMultisampleQualityLevels` destekler.

  D3D11_TEXTURE2D_DESC::BindFlags üyesinin D3D_BIND_SHADER_RESOURCE veya D3D11_BIND_UNORDERED_ACCESS bayrakları ayarlanmışsa doku iki sürümü oluşturulur; birincisi bu bayrakları işleme hedefi olarak kullanmak üzere temizledi, diğeri ise bu bayrakların ilk sürüm için çözüm arabelleği olarak hareket etmek üzere bozulmadan bırakıldığı MSAA olmayan bir doku. Gölgelendirici kaynağı olarak veya sırasız erişim için MSAA dokusu kullanmanın geçerli olması pek olası değildir; örneğin, üzerinde eylemde geçen gölgelendirici MSAA olmayan bir doku bekleyecek yanlış sonuçlar üretir. Değişken MSAA olmayan ikincil doku oluşturdu ise, MSAA işleme hedefi cihaz bağlamından ne zaman kümelenmişse, içeriği MSAA olmayan dokuya çözümlenir. Benzer şekilde, MSAA işleme hedefinin gölgelendirici kaynağı olarak bağlı olması veya sırasız bir erişim görünümünde kullanımı her olduğunda, çözümlenen MSAA olmayan doku bunun yerine bağlı olur.

  Bu çeşitler ayrıca , , , ve kullanılarak oluşturulan tüm takas zincirlerinde MSAA `IDXGIFactory::CreateSwapChain` `IDXGIFactory2::CreateSwapChainForHwnd` ayarlarını geçersiz `IDXGIFactory2::CreateSwapChainForCoreWindow` `IDXGIFactory2::CreateSwapChainForComposition` `ID3D11CreateDeviceAndSwapChain` kılar.

  Bu değişikliklerin net etkisi tüm işlemenin bir MSAA işleme hedefine yapılmasıdır, ancak uygulamanız bu işleme hedeflerinden birini veya takas zinciri arabelleklerini gölgelendirici kaynak görünümü veya sırasız erişim görünümü olarak kullanıyorsa, işleme hedefinin çözümlenen, MSAA olmayan kopyasından veriler örneklenir.

## <a name="restrictions-and-limitations"></a>Kısıtlamalar ve sınırlamalar
 Direct3D11'de MSAA dokuları MSAA olmayan dokulara göre daha kısıtlıdır. Örneğin, bir MSAA dokusunda çağıramazsınız ve kaynak ve hedef kaynağın örnek sayısı ve örnek kalitesi eşleşmezse çağrı başarısız olur. Bu durum, bu değişken bir kaynağın MSAA ayarlarını geçersiz kıldı ancak diğer kaynakla `ID3D11DeviceContext::UpdateSubresource` `ID3D11DeviceContext::CopySubresourceRegion` eşleşmez.

 Kayıttan yürütme bu tür çakışmaları algılasa, amaçlanan davranışı çoğaltmak için en iyi çabayı gösterir, ancak sonuçlarıyla tam olarak eşleşmesi mümkün olmayabilir. Bu varyantların performansını etkilerini yanlış tanıtacak şekilde etkilemesi yaygın bir durum olsa da, çoğaltılan doku aynı içeriğe sahip olabileceği için piksel gölgelendiricideki akış denetimi bir piksel gölgelendiricisinde kesin içerik tarafından belirlenebilir.

## <a name="example-1"></a>Örnek 1
 Bu çeşitlemeler, şu şekilde kod kullanılarak oluşturulan işleme `ID3D11Device::CreateTexture2D` hedefleri için yeniden oluşturulabilir:

```cpp
D3D11_TEXTURE2D_DESC target_description;
target_description.BindFlags = D3D11_BIND_RENDER_TARGET;
target_description.SampleDesc.Count = 4; // 4x MSAA, can be 2 or 0 instead
target_description.SampleDesc.Quality = 0;
d3d_device->CreateTexture2D(&target_description, nullptr, &render_target);
```

## <a name="example-2"></a>Örnek 2
 Veya IDXGISwapChain kullanılarak oluşturulan değiştirme zincirleri için::CreateSwapChain veya D3D11CreateDeviceAndSwapChain aşağıdaki gibi bir kod kullanarak:

```cpp
DXGI_SWAP_CHAIN_DESC chain_description;
chain_description.SampleDesc.Count = 4; // 4x MSAA, can be 2 or 0 instead
chain_description.SampleDesc.Quality = 0;

// Call IDXGISwapChain::CreateSwapChain or D3D11CreateDeviceAndSwapChain, etc.
```
