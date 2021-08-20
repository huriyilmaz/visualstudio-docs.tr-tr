---
title: 1x1 Görünüm Açısı Boyutu Çeşitleme | Microsoft Docs
description: Tüm işleme hedeflerine yönelik görünüm açısı boyutlarını 1x1 piksele düşürmek için 1x1 görünüm açısı boyut çeşidini uygulama.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 3dbc3247-00f5-4644-8ff9-72e9febcf09a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: bf619c6f9499916971620e3d428cf3545fd4cea1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122121106"
---
# <a name="1x1-viewport-size-variant"></a>1x1 Görünüm Penceresi Boyut Çeşidi
Tüm işleme hedeflerine yönelik görünüm açısı boyutlarını 1x1 piksele azaltır.

## <a name="interpretation"></a>Yorum
 Daha küçük bir görünüm açısı, gölgelendirmek zorunda olduğunuz piksel sayısını azaltır. Ancak daha küçük bir görünüm noktası, işlemesi gereken köşe sayısını azaltmaz. Görünüm açısı boyutlarını 1x1 piksel olarak ayarlama, uygulamanıza piksel gölgelendirmeyi etkili bir şekilde ortadan kaldırıyor.

 Bu değişken büyük bir performans kazancı gösteriyorsa, bu durum, uygulamanın çok fazla dolgu oranı tükettiğine işaret ediyor olabilir. Buna ek olarak, çözünürlüğünü hedef platform için fazla yüksek olabilir veya uygulamanız daha sonra üzerine yazılan pikselleri gölgelendirmek için önemli ölçüde zaman harcayabilir ve üzerine *çizi olarak da anılabilir.* Daha küçük bir çerçeve arabelleği veya fazla çizim miktarını azaltmak, uygulamanın performansını artırır.

## <a name="remarks"></a>Açıklamalar
 veya için yapılan her çağrıdan sonra görünüm açısı boyutları 1x1 piksele `ID3D11DeviceContext::OMSetRenderTargets` `ID3D11DeviceContext::RSSetViewports` sıfırlanır.

## <a name="example"></a>Örnek
 Bu değişken aşağıdaki kodla yeniden üretılabilir:

```cpp
D3D11_VIEWPORT viewport;
viewport.TopLeftX = 0;
viewport.TopLeftY = 0;
viewport.Width = 1;
viewport.Height = 1;
d3d_context->RSSetViewports(1, &viewport);
```
