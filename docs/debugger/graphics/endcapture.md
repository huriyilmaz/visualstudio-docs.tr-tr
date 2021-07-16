---
title: EndCapture | Microsoft Docs
description: BeginCapture ile başlayan yakalama aralığını sona ertk için VsgDbg sınıfının EndCapture yöntemini kullanın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 06084c3b-e065-49b6-968e-d578762fb871
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8b0820950980860465e5129211c77e48ff641bdf
ms.sourcegitcommit: aeed3eb503d0b282537b073ebae8c028c4fef750
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/15/2021
ms.locfileid: "114232680"
---
# <a name="endcapture"></a>EndCapture
ile başlayan yakalama aralığını sona `BeginCapture` erer.

## <a name="syntax"></a>Syntax

```C++
void EndCapture();
```

## <a name="remarks"></a>Açıklamalar
 Yakalama aralığı genellikle bir çerçevenin alt kümesine yayma (örneğin, grafik bilgilerini yalnızca belirli bir çizim çağrısıyla ilgili olarak yakalamak istediğiniz durumlarda). Yakalama aralığı bir sunum çağrısına yayıyorsa, iki grafik bilgisi karesi yakalanır. İlk kare, çağrısı ile var olan çağrı arasındaki aralığı, ikinci kare ise çağrısının ardından ilk Direct3D olayı ile çağrısı arasındaki aralığı `BeginCapture` `EndCapture` gösterir.

 Bir aralığı yakalamak için, veya çağırmadan önce, uygulamanıza grafik bilgilerini yakalamaya ve kaydetmeye hazırlamanız gerekir. Başka bir ifadeyle [Init'i](init.md) sınıfın bir örneği `VsgDbg` aracılığıyla `BeginCapture` çağırmıştınız. `EndCapture`

## <a name="see-also"></a>Ayrıca bkz.
- [BeginCapture](begincapture.md)
- [CaptureCurrentFrame](capturecurrentframe.md)