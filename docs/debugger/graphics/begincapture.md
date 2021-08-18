---
title: BeginCapture | Microsoft Docs
description: EndCapture ile sona erecek bir yakalama aralığına başlamak için VsgDbg sınıfının BeginCapture yöntemini kullanın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 9edbb52d-ee0b-4cc4-a382-972bcee067d3
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: c9c461bdae97e1fd26491e72bad1791ce529e2ed
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122052076"
---
# <a name="begincapture"></a>BeginCapture
ile sona erecek bir yakalama aralığı `EndCapture` başlar.

## <a name="syntax"></a>Syntax

```C++
void BeginCapture();
```

## <a name="remarks"></a>Açıklamalar
 Yakalama aralığı genellikle bir çerçevenin alt kümesini (örneğin, yalnızca belirli bir çizim çağrısıyla ilgili grafik bilgilerini yakalamak istediğiniz durumlarda) içerir. Yakalama aralığı bir sunum çağrısına yayıyorsa, iki grafik bilgisi karesi yakalanır. İlk kare, çağrısı ile var olan çağrı arasındaki aralığı, ikinci kare ise çağrısının ardından ilk Direct3D olayı ile çağrısı arasındaki aralığı `BeginCapture` `EndCapture` gösterir.

 Bir aralığı yakalamak için, veya çağırmadan önce, uygulamanıza grafik bilgilerini yakalamaya ve kaydetmeye hazırlamanız gerekir. Başka bir ifadeyle [Init'i](init.md) sınıfın bir örneği `VsgDbg` aracılığıyla `BeginCapture` çağırmıştınız. `EndCapture`

## <a name="see-also"></a>Ayrıca bkz.
- [EndCapture](endcapture.md)
- [CaptureCurrentFrame](capturecurrentframe.md)