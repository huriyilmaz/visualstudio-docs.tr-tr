---
title: Kesme Modu'| Microsoft Docs
description: Hata ayıklayıcı kesme modundayken oluşan işlem hakkında bilgi edinebilirsiniz. Hata ayıklayıcısı daha sonra kodda adım adım ilerler.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- break mode, stepping
- stepping, in break mode
- debugging [Debugging SDK], stepping in break mode
ms.assetid: b08dc8ee-6c63-4462-a097-6f525cfbb35a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 928340634c7b34e5f731704961803b4cab85db21
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626427"
---
# <a name="stepping-in-break-mode"></a>Kesme modunda adımlama
Aşağıdaki bölümde, hata ayıklayıcı kesme modunda olduğunda oluşan ve kodda adım adım ilerleyen işlem açıkmektedir:

## <a name="stepping-process"></a>Adımlama işlemi

1. Bir [adımı yürütmek için IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md) with [STEPKIND](../../extensibility/debugger/reference/stepkind.md) ve [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) bağımsız değişkenlerini çağırma.

2. Adım tamamlandığında, durdurma olayı olarak [bir IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) gönderin.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklayıcı olaylarını çağırma](../../extensibility/debugger/calling-debugger-events.md)
