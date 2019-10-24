---
title: CaptureCurrentFrame | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4509311d-6fe2-4b65-9b4a-ff0522585d6a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b9967d776845088e707035c7b1c56855ac80af82
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72736130"
---
# <a name="capturecurrentframe"></a>CaptureCurrentFrame
Geçerli çerçevenin kalan kısmını grafik günlük dosyasına yakalar.

## <a name="syntax"></a>Sözdizimi

```C++
void CaptureCurrentFrame();
```

## <a name="remarks"></a>Açıklamalar
 Şu anda başka bir yakalama devam ediyorsa — `BeginCapture` işlevi tarafından başlatılan yakalama gibi), yakalama tamamlanır ve grafik günlüğüne ayrı bir çerçeve olarak kaydedilir. Daha sonra, grafik tanılama, aynı zamanda farklı bir çerçeve olarak kaydedilen geçerli çerçevenin kalanını yakalamaya başlar. Geçerli çerçevenin bitişi, var olan bir çağrı tarafından işaretlenmiş.

 Bir çerçeveyi yakalamak için, uygulamanızı grafik bilgilerini yakalamak ve kaydetmek üzere hazırlamanız gerekir — Yani, `CaptureCurrentFrame` çağırmadan önce `VsgDbg` sınıfının bir örneğinden [Init](init.md) olarak adlandırmanız gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [Init](init.md)
- [BeginCapture](begincapture.md)