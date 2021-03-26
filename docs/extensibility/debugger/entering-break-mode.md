---
title: Kesme moduna giriliyor | Microsoft Docs
description: Bir işlevde karşılaşılan, imleçteki kaynak kodu satırına çalışan veya bir kesme noktasına çalışan bir kesme noktası için oluşan işlem hakkında bilgi edinin.
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
ms.workload:
- vssdk
ms.openlocfilehash: 6e8af8aa2765e199e8e278982669f68b3019b6c2
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105097220"
---
# <a name="enter-break-mode"></a>Kesme moduna gir
Aşağıdaki bilgiler bir işleve adımladıktan sonra, üzerinde imleç bulunan kaynak kodu satırına çalışan veya bir kesme noktasına çalışan bir kesme noktasına gelindiğinde oluşan süreci açıklar.

## <a name="break-mode-process"></a>Kesme modu işlemi

1. Hata ayıklama altyapısı (DE), IDE 'nin kesme moduna girmesine neden olmak için [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md), [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)veya başka bir durdurma olayı gönderir.

2. SDM, iş parçacığından gelen çağrı yığını bilgilerini aşağıdaki gibi alır:

    - [IDebugThread2::EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)

    - [IEnumDebugFrameInfo2::GetCount](../../extensibility/debugger/reference/ienumdebugframeinfo2-getcount.md)

    - [IEnumDebugFrameInfo2::Next](../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md)

    - [IDebugStackFrame2:: GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) kaynak kodu bilgilerini almak için

    - [IDebugDocumentContext2:: GetName](../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md) dosya adını almak için

    - [IDebugDocumentContext2:: GetStatementRange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md) ifade aralığını almak için

    - [IDebugStackFrame2:: GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md) bellek bilgilerini almak için

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklayıcı olaylarını çağırma](../../extensibility/debugger/calling-debugger-events.md)
