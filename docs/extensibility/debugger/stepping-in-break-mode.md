---
title: Kesme modunda adımla | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80712852"
---
# <a name="stepping-in-break-mode"></a>Kesme modunda adımla
Aşağıdaki bölümde, hata ayıklayıcı kesme modundayken gerçekleşen işlem açıklanmakta ve kodun adım adım olması gerekir:

## <a name="stepping-process"></a>İşlem Adımlama

1. Bir adımı yürütmek için [Stepkind](../../extensibility/debugger/reference/stepkind.md) ve [stepunit](../../extensibility/debugger/reference/stepunit.md) bağımsız değişkenleriyle [IDebugProgram2:: Step](../../extensibility/debugger/reference/idebugprogram2-step.md) öğesini çağırın.

2. Adım tamamlandığında, durdurma olayı olarak bir [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) gönderin.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklayıcı olaylarını çağırma](../../extensibility/debugger/calling-debugger-events.md)
