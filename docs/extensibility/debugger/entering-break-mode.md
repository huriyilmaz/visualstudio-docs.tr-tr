---
title: Kesme Modu'| Microsoft Docs
description: İşlevde karşılaşılan bir kesme noktası için oluşan işlemi, imlecin kaynak kodu satırına kadar çalıştırmayı veya bir kesme noktası çalıştırmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- break mode
- debugging [Debugging SDK], entering break mode
ms.assetid: e9a8a241-cd21-4d4e-999a-283554c288b1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 01d52a2596dfc0d5b67cdcf5208c0819aaa099c2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122153569"
---
# <a name="enter-break-mode"></a>Kesme moduna girme
Aşağıdaki bilgiler, bir işleve adımlama sonrasında bir kesme noktasıyla karşılaşıldıktan, imlecin içinde yer alan kaynak kod satırına çalıştırıldıktan veya bir kesme noktası çalıştırıldıktan sonra oluşan işlemi açıklar.

## <a name="break-mode-process"></a>Kesme modu işlemi

1. Hata ayıklama altyapısı (DE) [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md), [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)veya IDE'nin kesme moduna girmesinde neden olacak başka bir durdurma olayı gönderir.

2. SDM, çağrı yığını bilgilerini iş parçacığından aşağıdaki gibi alır:

    - [IDebugThread2::EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)

    - [IEnumDebugFrameInfo2::GetCount](../../extensibility/debugger/reference/ienumdebugframeinfo2-getcount.md)

    - [IEnumDebugFrameInfo2::Next](../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md)

    - [Kaynak kod bilgilerini almak için IDebugStackFrame2::GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)

    - [Dosya adını almak için IDebugDocumentContext2::GetName](../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)

    - [Deyim aralığını almak için IDebugDocumentContext2::GetStatementRange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)

    - [Bellek bilgilerini almak için IDebugStackFrame2::GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklayıcı olaylarını çağırma](../../extensibility/debugger/calling-debugger-events.md)
