---
title: Program sonlandırılıyor | Microsoft Docs
description: Bu makalede, IDE 'nin tek bir iş parçacığıyla tek bir programı sonlandırmak için hata ayıklama altyapısını nasıl kullandığı açıklanır.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 1b2b883611d5479f0febc169b32f7f378230be4c
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2020
ms.locfileid: "96995986"
---
# <a name="terminating-a-program"></a>Program sonlandırılıyor
Aşağıdaki bölümde, bir iş parçacığı ile tek bir programın sonlandırılması açıklanmaktadır.

## <a name="termination-process"></a>Sonlandırma işlemi

1. DE geçerli bir [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md)Ile bir [IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md) gönderir.

2. DE geçerli bir [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)Ile bir [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) gönderir.

   IDE tasarım moduna girer. Hata ayıklama altyapısı veya çalışma zamanı ortamı, programı bağlantı noktasından kaldırmak için [IDebugPortNotify2:: RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) yöntemini çağırır.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklayıcı olaylarını çağırma](../../extensibility/debugger/calling-debugger-events.md)
