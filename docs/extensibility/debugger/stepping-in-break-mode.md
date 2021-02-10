---
title: Kesme modunda adımla | Microsoft Docs
description: Hata ayıklayıcı kesme modundayken gerçekleşen işlem hakkında bilgi edinin. Hata ayıklayıcı daha sonra kod içinde ilermelidir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- break mode, stepping
- stepping, in break mode
- debugging [Debugging SDK], stepping in break mode
ms.assetid: b08dc8ee-6c63-4462-a097-6f525cfbb35a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4f284fecf32a94f7187ecd34798f9ac21f476804
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99960682"
---
# <a name="stepping-in-break-mode"></a>Kesme modunda adımla
Aşağıdaki bölümde, hata ayıklayıcı kesme modundayken gerçekleşen işlem açıklanmakta ve kodun adım adım olması gerekir:

## <a name="stepping-process"></a>İşlem Adımlama

1. Bir adımı yürütmek için [Stepkind](../../extensibility/debugger/reference/stepkind.md) ve [stepunit](../../extensibility/debugger/reference/stepunit.md) bağımsız değişkenleriyle [IDebugProgram2:: Step](../../extensibility/debugger/reference/idebugprogram2-step.md) öğesini çağırın.

2. Adım tamamlandığında, durdurma olayı olarak bir [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) gönderin.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklayıcı olaylarını çağırma](../../extensibility/debugger/calling-debugger-events.md)
