---
title: Programı Sonlandırma | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- programs, termination events
- debugging [Debugging SDK], terminating a program
ms.assetid: eedda0a3-5e05-44fe-841d-a2f4866ac72d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 985b20fe75f8ceee3d434ac681b437c51baf85e8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712515"
---
# <a name="terminating-a-program"></a>Programı sonlandırma
Aşağıdaki bölümde tek bir iş parçacığı ile tek bir programın sonlandırılması açıklanır.

## <a name="termination-process"></a>Sonlandırma işlemi

1. DE geçerli bir [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md)ile bir [IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md) gönderir.

2. DE geçerli bir [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)ile bir [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) gönderir.

   IDE tasarım moduna geçer. Hata ayıklama motoru veya çalışma zamanı ortamı, programı bağlantı noktasından kaldırmak için [IDebugPortNotify2::RemoveProgramNode'u](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) çağırır.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklama olaylarını çağırma](../../extensibility/debugger/calling-debugger-events.md)
