---
title: IDebugProgramCreateEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramCreateEvent2
helpviewer_keywords:
- IDebugProgramCreateEvent2 interface
ms.assetid: b19a7934-6179-4a68-9075-bd7dcd640b05
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5b73deab28f08ed9268033e941b64b753f64adf5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99891026"
---
# <a name="idebugprogramcreateevent2"></a>IDebugProgramCreateEvent2
Bu arabirim, bir program öğesine eklendiğinde hata ayıklama altyapısı (DE) tarafından oturum hata ayıklama Yöneticisi (SDM) tarafından gönderilir.

## <a name="syntax"></a>Syntax

```
IDebugProgramCreateEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 DE veya özel bağlantı noktası sağlayıcısı bu arabirimi, genellikle programın eklendiği zaman bir programın oluşturulduğunu raporlamak için uygular. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) arabiriminin bu arabirimle aynı nesne üzerinde uygulanması gerekir. SDM, `QueryInterface` arabirime erişmek için yöntemini kullanır `IDebugEvent2` .

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 DE veya özel bağlantı noktası sağlayıcısı, bir programın oluşturulmasını raporlamak için bu olay nesnesini oluşturur ve gönderir. Bu olayı, hata ayıklamakta olan programa eklendiğinde SDM tarafından sağlanan [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) callback işlevini kullanarak gönderir. Özel bağlantı noktası sağlayıcısı bu olayı [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) arabirimini kullanarak gönderir.

## <a name="remarks"></a>Açıklamalar
 DE veya özel bağlantı noktası sağlayıcısı, [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)çağırarak yeni bir [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) arabirimi yayımlar.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
