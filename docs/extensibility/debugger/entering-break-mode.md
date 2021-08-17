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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 79e864849059e7d3e3543dbe2df6c2b79c720d7730e45431cfaa4ec8a4d26dca
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121342992"
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
