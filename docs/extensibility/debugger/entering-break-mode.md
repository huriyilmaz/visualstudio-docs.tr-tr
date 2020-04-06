---
title: Kesme Moduna Girme | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- break mode
- debugging [Debugging SDK], entering break mode
ms.assetid: e9a8a241-cd21-4d4e-999a-283554c288b1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4bbcec8adf6468f70d95df5f291ce1e5540406cf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738881"
---
# <a name="enter-break-mode"></a>Kesme modunu girin
Aşağıdaki bilgiler, bir işleve adım attıktan sonra bir kesme noktasıyla karşılaşıldığında, imleci içinde bulunan kaynak kodu satırına doğru çalışan veya kesme noktasına çalışan işlemi açıklar.

## <a name="break-mode-process"></a>Kesme modu işlemi

1. Hata ayıklama motoru (DE), [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md), [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)veya ide'nin kesme moduna girmesine neden olan başka bir durdurma olayı gönderir.

2. SDM, çağrı yığını bilgilerini iş parçacığından aşağıdaki gibi alır:

    - [IDebugThread2::EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)

    - [IEnumDebugFrameInfo2::GetCount](../../extensibility/debugger/reference/ienumdebugframeinfo2-getcount.md)

    - [IEnumDebugFrameInfo2::Next](../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md)

    - [IDebugStackFrame2::GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) kaynak kodu bilgilerini almak için

    - [IDebugDocumentContext2::Dosya](../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md) adını almak için Name getname

    - [IDebugDocumentContext2::GetStatementRange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md) ifade aralığı almak için

    - [IDebugStackFrame2::GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md) bellek bilgileri almak için

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklama olaylarını çağırma](../../extensibility/debugger/calling-debugger-events.md)
