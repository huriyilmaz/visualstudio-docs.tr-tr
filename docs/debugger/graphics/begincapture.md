---
title: BeginCapture | Microsoft Docs
description: EndCapture ile sona erecek yakalama aralığına başlamak için VsgDbg sınıfının BeginCapture yöntemini kullanın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 9edbb52d-ee0b-4cc4-a382-972bcee067d3
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c9fc81bdd058d3a8c1dbe26bbe944bcb0e354ac7
ms.sourcegitcommit: aeed3eb503d0b282537b073ebae8c028c4fef750
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/15/2021
ms.locfileid: "114232745"
---
# <a name="begincapture"></a>BeginCapture
ile sona erecek bir yakalama aralığı `EndCapture` başlar.

## <a name="syntax"></a>Syntax

```C++
void BeginCapture();
```

## <a name="remarks"></a>Açıklamalar
 Yakalama aralığı genellikle bir çerçevenin alt kümesine yayma (örneğin, grafik bilgilerini yalnızca belirli bir çizim çağrısıyla ilgili olarak yakalamak istediğiniz durumlarda). Yakalama aralığı bir sunum çağrısına yayıyorsa, iki grafik bilgisi karesi yakalanır. İlk kare, çağrısı ile var olan çağrı arasındaki aralığı, ikinci kare ise çağrısının ardından ilk Direct3D olayı ile çağrısı arasındaki aralığı `BeginCapture` `EndCapture` gösterir.

 Bir aralığı yakalamak için, veya çağırmadan önce, uygulamanıza grafik bilgilerini yakalamaya ve kaydetmeye hazırlamanız gerekir. Başka bir ifadeyle [Init'i](init.md) sınıfın bir örneği `VsgDbg` aracılığıyla `BeginCapture` çağırmıştınız. `EndCapture`

## <a name="see-also"></a>Ayrıca bkz.
- [EndCapture](endcapture.md)
- [CaptureCurrentFrame](capturecurrentframe.md)