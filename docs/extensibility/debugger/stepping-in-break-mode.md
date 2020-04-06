---
title: Kesme Moduna Girme | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- break mode, stepping
- stepping, in break mode
- debugging [Debugging SDK], stepping in break mode
ms.assetid: b08dc8ee-6c63-4462-a097-6f525cfbb35a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3161fc1c1ec8b44d96b3793198ac630ba2e32d67
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712852"
---
# <a name="stepping-in-break-mode"></a>Kesme moduna girme
Aşağıdaki bölümde hata ayıklayıcı kesme modundayken oluşan ve kod üzerinden adım atması gereken işlem açıklanır:

## <a name="stepping-process"></a>Atlama işlemi

1. Çağrı [IDebugProgram2::StepKIND](../../extensibility/debugger/reference/idebugprogram2-step.md) ve [STEPUNIT](../../extensibility/debugger/reference/stepkind.md) bağımsız değişkenleri ile adım bir adım yürütmek için. [STEPUNIT](../../extensibility/debugger/reference/stepunit.md)

2. Adım tamamlandığında, durdurma olayı olarak bir [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) gönderin.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklama olaylarını çağırma](../../extensibility/debugger/calling-debugger-events.md)
