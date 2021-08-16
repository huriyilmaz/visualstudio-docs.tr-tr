---
title: 1x1 GörünümPort Boyutu Varyantı | Microsoft Docs
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
ms.openlocfilehash: c9cda1347a0f1293165b5cbb553f1102eac615c67d3659a000c263bd762d17fe
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121263666"
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
