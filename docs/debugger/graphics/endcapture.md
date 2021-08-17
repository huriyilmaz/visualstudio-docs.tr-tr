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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: bbcd047552671fa5b6767a78b82c08038968a18d038ab3d767e6a86f6bcf23f6
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121343670"
---
# <a name="endcapture"></a>EndCapture
ile başlayan yakalama aralığını sona `BeginCapture` erer.

## <a name="syntax"></a>Syntax

```C++
void EndCapture();
```

## <a name="remarks"></a>Açıklamalar
 Yakalama aralığı genellikle bir çerçevenin alt kümesini (örneğin, yalnızca belirli bir çizim çağrısıyla ilgili grafik bilgilerini yakalamak istediğiniz durumlarda) içerir. Yakalama aralığı bir sunum çağrısına yayıyorsa, iki grafik bilgisi karesi yakalanır. İlk kare, çağrısı ile var olan çağrı arasındaki aralığı, ikinci kare ise çağrısının ardından ilk Direct3D olayı ile çağrısı arasındaki aralığı `BeginCapture` `EndCapture` gösterir.

 Bir aralığı yakalamak için, veya çağırmadan önce, uygulamanıza grafik bilgilerini yakalamaya ve kaydetmeye hazırlamanız gerekir. Başka bir ifadeyle [Init'i](init.md) sınıfın bir örneği `VsgDbg` aracılığıyla `BeginCapture` çağırmıştınız. `EndCapture`

## <a name="see-also"></a>Ayrıca bkz.
- [BeginCapture](begincapture.md)
- [CaptureCurrentFrame](capturecurrentframe.md)