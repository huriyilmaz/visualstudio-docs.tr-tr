---
title: IDebugLoadCompleteEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugLoadCompleteEvent2
helpviewer_keywords:
- IDebugLoadCompleteEvent2
ms.assetid: 37eb7360-28e9-4273-862a-4c17f22af690
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 37c6713dc0e34ae0823cfbfb5db5c539b5073e3b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99890259"
---
# <a name="idebugloadcompleteevent2"></a>IDebugLoadCompleteEvent2
Bu arabirim, bir program yüklendiğinde, ancak herhangi bir kod yürütülmeden önce, hata ayıklama altyapısı (DE) tarafından oturum hata ayıklama Yöneticisi 'ne (SDM) gönderilir.

## <a name="syntax"></a>Syntax

```
IDebugLoadCompleteEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Bu arabirimi, bir programın başarıyla yüklendiğini bildirmek için DE uygular. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) arabiriminin bu arabirimle aynı nesne üzerinde uygulanması gerekir. SDM, arabirime erişmek için [QueryInterface](/cpp/atl/queryinterface) kullanır `IDebugEvent2` .

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 DE, bir programın başarıyla yüklendiğini bildirmek için bu olay nesnesini oluşturur ve gönderir. Olay, hata ayıklamakta olan programa eklendiğinde SDM tarafından sağlanan [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) callback işlevi kullanılarak gönderilir.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
