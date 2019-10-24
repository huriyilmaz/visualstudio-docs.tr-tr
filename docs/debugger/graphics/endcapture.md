---
title: EndCapture | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 06084c3b-e065-49b6-968e-d578762fb871
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c54e8b12f4d3b924b363f42cb098a1d528a8108b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72735973"
---
# <a name="endcapture"></a>EndCapture
@No__t_0 ile başlatılan bir yakalama aralığını sonlandırır.

## <a name="syntax"></a>Sözdizimi

```C++
void EndCapture();
```

## <a name="remarks"></a>Açıklamalar
 Yakalama aralığı genellikle yalnızca belirli bir çizim çağrısı türü hakkında grafik bilgilerini yakalamak istediğinizde olduğu gibi, bir çerçevenin alt kümesini kapsar. Yakalama aralığı, var olan bir çağrıya yayılırsa, grafik bilgilerinin iki çerçevesi yakalanır. İlk kare `BeginCapture` çağrısı ve var olan çağrı arasındaki aralığı kapsar; ikinci çerçeve, var olan çağrının ve `EndCapture` çağrısının ardından ilk Direct3D olayı arasındaki aralığı kapsar.

 Bir aralığı yakalamak için, uygulamanızı grafik bilgilerini yakalamak ve kaydetmek üzere hazırlamanız gerekir — diğer bir deyişle, `BeginCapture` veya `EndCapture` çağırmadan önce `VsgDbg` sınıfının bir örneğinden [Init](init.md) olarak adlandırmanız gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [BeginCapture](begincapture.md)
- [CaptureCurrentFrame](capturecurrentframe.md)