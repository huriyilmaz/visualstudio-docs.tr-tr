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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72736150"
---
# <a name="begincapture"></a>BeginCapture
İle biten bir yakalama aralığı başlatır `EndCapture` .

## <a name="syntax"></a>Syntax

```C++
void BeginCapture();
```

## <a name="remarks"></a>Açıklamalar
 Yakalama aralığı genellikle yalnızca belirli bir çizim çağrısı türü hakkında grafik bilgilerini yakalamak istediğinizde olduğu gibi, bir çerçevenin alt kümesini kapsar. Yakalama aralığı, var olan bir çağrıya yayılırsa, grafik bilgilerinin iki çerçevesi yakalanır. İlk çerçeve, çağrısı ve var olan çağrı arasındaki aralığı kapsar `BeginCapture` ; ikinci kare, çağrısı ve çağrısı sonrasında Ilk Direct3D olayı arasındaki aralığı kapsar `EndCapture` .

 Bir aralığı yakalamak için, uygulamanızı grafik bilgilerini yakalamak ve kaydetmek üzere hazırlamanız gerekir — diğer bir deyişle, [Init](init.md) `VsgDbg` veya çağrısından önce sınıfının bir örneğini kullanarak Init olarak adlandırmanız gerekir `BeginCapture` `EndCapture` .

## <a name="see-also"></a>Ayrıca bkz.
- [EndCapture](endcapture.md)
- [CaptureCurrentFrame](capturecurrentframe.md)