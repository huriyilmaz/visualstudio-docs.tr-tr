---
title: 1x1 Görünüm penceresi boyut varyantı | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 3dbc3247-00f5-4644-8ff9-72e9febcf09a
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 74e3bc706cb2df12aacddf9fbb77dec598bfc17a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157561"
---
# <a name="1x1-viewport-size-variant"></a>1x1 Görünüm Penceresi Boyut Çeşidi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tüm işleme hedeflerindeki Görünüm penceresi boyutunu 1x1 piksele düşürür.  
  
## <a name="interpretation"></a>Yorumlama  
 Daha küçük bir görünüm penceresi, gölgeli olması gereken piksel sayısını azaltır, ancak işlenmesi gereken köşe sayısını azaltmaz. Görünüm penceresi boyutlarını 1x1 piksel olarak ayarlamak, uygulamanızdan piksel gölgelendirmesini etkin bir şekilde ortadan kaldırır.  
  
 Bu çeşit büyük bir performans kazancı gösteriyorsa, uygulamanız çok fazla fillrate tükettiğini gösterebilir. Bu, seçtiğiniz çözümlemenin hedef platform için çok yüksek olduğunu veya uygulamanızın daha sonra üzerine yazılacak önemli bir zaman gölgeleme pikseli (fazla çizim) harcadığını gösterebilir. Bu sonuç, framebuffer boyutunu azaltmanızı veya fazla çizim miktarını azaltmanızı, uygulamanızın performansını iyileştirmesini önerir.  
  
## <a name="remarks"></a>Açıklamalar  
 Görünüm penceresi boyutları, veya için her çağrıdan sonra 1x1 piksel olarak `ID3D11DeviceContext::OMSetRenderTargets` sıfırlanır `ID3D11DeviceContext::RSSetViewports` .  
  
## <a name="example"></a>Örnek  
 Bu varyant, aşağıdaki gibi kod kullanılarak yeniden oluşturulabilir:  
  
```  
D3D11_VIEWPORT viewport;  
viewport.TopLeftX = 0;  
viewport.TopLeftY = 0;  
viewport.Width = 1;  
viewport.Height = 1;  
d3d_context->RSSetViewports(1, &viewport);  
```
