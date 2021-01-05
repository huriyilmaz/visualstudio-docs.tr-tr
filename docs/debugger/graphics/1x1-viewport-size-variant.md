---
title: 1x1 Görünüm penceresi boyut varyantı | Microsoft Docs
description: Tüm işleme hedeflerindeki Görünüm penceresi boyutlarını 1x1 piksele düşürmek için 1x1 Görünüm penceresi boyut türevini uygulayın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 3dbc3247-00f5-4644-8ff9-72e9febcf09a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d1041f3a8016500a6e1f217849654d9710a508d8
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2020
ms.locfileid: "97726494"
---
# <a name="1x1-viewport-size-variant"></a>1x1 Görünüm Penceresi Boyut Çeşidi
Tüm işleme hedeflerindeki Görünüm penceresi boyutunu 1x1 piksele düşürür.

## <a name="interpretation"></a>Yorum
 Daha küçük bir görünüm penceresi, gölgelendirmek istediğiniz piksel sayısını azaltır. Ancak, daha küçük bir görünüm penceresi, işlemek istediğiniz köşe sayısını azaltmaz. Görünüm penceresi boyutlarını 1x1 piksel olarak ayarlamak, uygulamanızdan piksel gölgelendirmesini etkin bir şekilde ortadan kaldırır.

 Bu çeşit büyük bir performans kazancı gösteriyorsa, uygulamanızın çok fazla sayıda dolgusu kullandığını gösteriyor olabilir. Ayrıca, çözümlemenizin hedef platform için çok yüksek olması veya uygulamanız daha sonra üzerine yazılmış ve *fazla çizim* olarak da bilinen önemli zaman gölgeleme piksellerini harcayabilir. Daha küçük bir çerçeve arabelleği veya fazla çizim miktarını azaltmak, uygulamanızın performansını iyileştirir.

## <a name="remarks"></a>Açıklamalar
 Görünüm penceresi boyutları, veya için her çağrıdan sonra 1x1 piksel olarak `ID3D11DeviceContext::OMSetRenderTargets` sıfırlanır `ID3D11DeviceContext::RSSetViewports` .

## <a name="example"></a>Örnek
 Bu varyant aşağıdaki kodla yeniden oluşturulabilir:

```cpp
D3D11_VIEWPORT viewport;
viewport.TopLeftX = 0;
viewport.TopLeftY = 0;
viewport.Width = 1;
viewport.Height = 1;
d3d_context->RSSetViewports(1, &viewport);
```
