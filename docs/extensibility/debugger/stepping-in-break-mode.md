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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0ed11d05e4351ac6ba76bc9aa10531a8a96ddf23
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105075412"
---
# <a name="stepping-in-break-mode"></a>Kesme modunda adımla
Aşağıdaki bölümde, hata ayıklayıcı kesme modundayken gerçekleşen işlem açıklanmakta ve kodun adım adım olması gerekir:

## <a name="stepping-process"></a>İşlem Adımlama

1. Bir adımı yürütmek için [Stepkind](../../extensibility/debugger/reference/stepkind.md) ve [stepunit](../../extensibility/debugger/reference/stepunit.md) bağımsız değişkenleriyle [IDebugProgram2:: Step](../../extensibility/debugger/reference/idebugprogram2-step.md) öğesini çağırın.

2. Adım tamamlandığında, durdurma olayı olarak bir [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) gönderin.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklayıcı olaylarını çağırma](../../extensibility/debugger/calling-debugger-events.md)
