---
title: BeginCapture | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 9edbb52d-ee0b-4cc4-a382-972bcee067d3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9521288b27b1f9b11a2fdb8cbbd613f1a77f857d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72736150"
---
# <a name="begincapture"></a>BeginCapture
@No__t_0 ile biten bir yakalama aralığı başlatır.

## <a name="syntax"></a>Sözdizimi

```C++
void BeginCapture();
```

## <a name="remarks"></a>Açıklamalar
 Yakalama aralığı genellikle yalnızca belirli bir çizim çağrısı türü hakkında grafik bilgilerini yakalamak istediğinizde olduğu gibi, bir çerçevenin alt kümesini kapsar. Yakalama aralığı, var olan bir çağrıya yayılırsa, grafik bilgilerinin iki çerçevesi yakalanır. İlk kare `BeginCapture` çağrısı ve var olan çağrı arasındaki aralığı kapsar; ikinci çerçeve, var olan çağrının ve `EndCapture` çağrısının ardından ilk Direct3D olayı arasındaki aralığı kapsar.

 Bir aralığı yakalamak için, uygulamanızı grafik bilgilerini yakalamak ve kaydetmek üzere hazırlamanız gerekir — diğer bir deyişle, `BeginCapture` veya `EndCapture` çağırmadan önce `VsgDbg` sınıfının bir örneğinden [Init](init.md) olarak adlandırmanız gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [EndCapture](endcapture.md)
- [CaptureCurrentFrame](capturecurrentframe.md)