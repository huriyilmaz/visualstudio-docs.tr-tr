---
title: BeginCapture | Microsoft Docs
description: EndCapture ile biten bir yakalama aralığı başlatmak için VsgDbg sınıfının BeginCapture yöntemini kullanın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 9edbb52d-ee0b-4cc4-a382-972bcee067d3
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a9e002a66ec3ec121a4cdc20ffb9ce59c1ed9dc0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874580"
---
# <a name="begincapture"></a>BeginCapture
İle biten bir yakalama aralığı başlatır `EndCapture` .

## <a name="syntax"></a>Syntax

```C++
void BeginCapture();
```

## <a name="remarks"></a>Açıklamalar
 Yakalama aralığı genellikle yalnızca belirli bir çizim çağrısı türü hakkında grafik bilgilerini yakalamak istediğinizde olduğu gibi, bir çerçevenin alt kümesini kapsar. Yakalama aralığı, var olan bir çağrıya yayılırsa, grafik bilgilerinin iki çerçevesi yakalanır. İlk çerçeve, çağrısı ve var olan çağrı arasındaki aralığı kapsar `BeginCapture` ; ikinci kare, çağrısı ve çağrısı sonrasında Ilk Direct3D olayı arasındaki aralığı kapsar `EndCapture` .

 Bir aralığı yakalamak için, uygulamanızı grafik bilgilerini yakalamak ve kaydetmek üzere hazırlamanız gerekir — diğer bir deyişle, [](init.md) `VsgDbg` veya çağrısından önce sınıfının bir örneğini kullanarak Init olarak adlandırmanız gerekir `BeginCapture` `EndCapture` .

## <a name="see-also"></a>Ayrıca bkz.
- [EndCapture](endcapture.md)
- [CaptureCurrentFrame](capturecurrentframe.md)