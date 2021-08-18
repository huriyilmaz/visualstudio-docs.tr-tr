---
title: CaptureCurrentFrame | Microsoft Docs
description: Geçerli çerçevenin kalan kısmını grafik günlük dosyasına yakalamak için VsgDbg sınıfının CaptureCurrentFrame metodunu kullanın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 4509311d-6fe2-4b65-9b4a-ff0522585d6a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 0271ccd7b1a9a90ae683e86a141d41d269cac773
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122154271"
---
# <a name="capturecurrentframe"></a>CaptureCurrentFrame
Geçerli çerçevenin kalan kısmını grafik günlük dosyasına yakalar.

## <a name="syntax"></a>Syntax

```C++
void CaptureCurrentFrame();
```

## <a name="remarks"></a>Açıklamalar
 Başka bir yakalama devam ediyorsa (işlev tarafından başlatılan yakalama gibi `BeginCapture` ), yakalama tamamlanır ve grafik günlüğüne ayrı bir çerçeve olarak kaydedilir. Daha sonra, grafik tanılama, aynı zamanda farklı bir çerçeve olarak kaydedilen geçerli çerçevenin kalanını yakalamaya başlar. Geçerli çerçevenin bitişi, var olan bir çağrı tarafından işaretlenmiş.

 Bir çerçeveyi yakalamak için, uygulamanızı grafik bilgilerini yakalamak ve kaydetmek üzere hazırlamanız gerekir — diğer bir deyişle, çağrılmadan önce sınıfın bir örneğini [başlatma](init.md) olarak adlandırmanız gerekir `VsgDbg` `CaptureCurrentFrame` .

## <a name="see-also"></a>Ayrıca bkz.
- [Dengeleyici](init.md)
- [BeginCapture](begincapture.md)