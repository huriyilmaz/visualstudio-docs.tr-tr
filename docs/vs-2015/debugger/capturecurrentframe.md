---
title: CaptureCurrentFrame | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 4509311d-6fe2-4b65-9b4a-ff0522585d6a
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2718e800e2a31eb66319259ed1e43f2ab8b084c5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68161639"
---
# <a name="capturecurrentframe"></a>CaptureCurrentFrame
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Geçerli çerçevenin kalan kısmını grafik günlük dosyasına yakalar.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
void CaptureCurrentFrame();  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Başka bir yakalama devam ediyorsa (işlev tarafından başlatılan yakalama gibi `BeginCapture` ), yakalama tamamlanır ve grafik günlüğüne ayrı bir çerçeve olarak kaydedilir. Daha sonra, grafik tanılama, aynı zamanda farklı bir çerçeve olarak kaydedilen geçerli çerçevenin kalanını yakalamaya başlar. Geçerli çerçevenin bitişi, var olan bir çağrı tarafından işaretlenmiş.  
  
 Bir çerçeveyi yakalamak için, uygulamanızı grafik bilgilerini yakalamak ve kaydetmek üzere hazırlamanız gerekir — diğer bir deyişle, çağrılmadan önce sınıfın bir örneğini [başlatma](../debugger/init.md) olarak adlandırmanız gerekir `VsgDbg` `CaptureCurrentFrame` .  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Dengeleyici](../debugger/init.md)   
 [BeginCapture](../debugger/begincapture.md)
