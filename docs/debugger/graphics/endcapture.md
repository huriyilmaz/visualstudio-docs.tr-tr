---
title: EndCapture | Microsoft Docs
description: BeginCapture ile başlatılan bir yakalama aralığını sonlandırmak için VsgDbg sınıfının EndCapture yöntemini kullanın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 06084c3b-e065-49b6-968e-d578762fb871
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3f7733eb9bed86bc450e4438ce34054312b13db5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99880287"
---
# <a name="endcapture"></a>EndCapture
İle başlatılan bir yakalama aralığını sonlandırır `BeginCapture` .

## <a name="syntax"></a>Syntax

```C++
void EndCapture();
```

## <a name="remarks"></a>Açıklamalar
 Yakalama aralığı genellikle yalnızca belirli bir çizim çağrısı türü hakkında grafik bilgilerini yakalamak istediğinizde olduğu gibi, bir çerçevenin alt kümesini kapsar. Yakalama aralığı, var olan bir çağrıya yayılırsa, grafik bilgilerinin iki çerçevesi yakalanır. İlk çerçeve, çağrısı ve var olan çağrı arasındaki aralığı kapsar `BeginCapture` ; ikinci kare, çağrısı ve çağrısı sonrasında Ilk Direct3D olayı arasındaki aralığı kapsar `EndCapture` .

 Bir aralığı yakalamak için, uygulamanızı grafik bilgilerini yakalamak ve kaydetmek üzere hazırlamanız gerekir — diğer bir deyişle, [](init.md) `VsgDbg` veya çağrısından önce sınıfının bir örneğini kullanarak Init olarak adlandırmanız gerekir `BeginCapture` `EndCapture` .

## <a name="see-also"></a>Ayrıca bkz.
- [BeginCapture](begincapture.md)
- [CaptureCurrentFrame](capturecurrentframe.md)