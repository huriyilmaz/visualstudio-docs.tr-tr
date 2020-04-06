---
title: IDebugEntryPointEvent2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEntryPointEvent2
helpviewer_keywords:
- IDebugEntryPointEvent2 interface
ms.assetid: a15d1cc3-97b7-438c-8d24-c23149708f42
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 531ff846f2488193ed7f3d9f200a1a4ea04df6f9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730323"
---
# <a name="idebugentrypointevent2"></a>IDebugEntryPointEvent2
Hata ayıklama altyapısı (DE), program ilk kullanıcı kodu talimatını yürütmek üzereyken bu arabirimi oturum hata ayıklama yöneticisine (SDM) gönderir.

## <a name="syntax"></a>Sözdizimi

```
IDebugEntryPointEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 DE, bu arabirimi normal işlemlerinin bir parçası olarak uygular. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) arabirimi bu arabirimle aynı nesne üzerinde uygulanmalıdır. SDM `IDebugEvent2` [arabirime](/cpp/atl/queryinterface) erişmek için QueryInterface kullanır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 De, debugged olan program yüklendiğinde ve kullanıcı kodunun ilk yönergesini yürütmeye hazır olduğunda DE bu olay nesnesini oluşturur ve gönderir. Olay, sdm tarafından verilen [iDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) geri arama işlevi kullanılarak gönderilir.

## <a name="remarks"></a>Açıklamalar
- [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) program ilk talimatı yürütmek üzereyken gönderilir. Örneğin, `IDebugEntryPoint2` program kullanıcının `main` işlevini yürütmek üzereyken gönderilir.

 DE gönderdiğinde, `IDebugEntryPointEvent2`geçerli kod konumu kullanıcı kodunun ilk yönergesi olmalıdır, gibi `main`.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)
