---
title: IDebugThreadDestroyEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThreadDestroyEvent2
helpviewer_keywords:
- IDebugThreadDestroyEvent2
ms.assetid: fca3f603-9432-457b-9ddd-8b0ec17da046
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ebc250f485e5507a9b50bc5a8e1c5b4c3bea37ef
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80718473"
---
# <a name="idebugthreaddestroyevent2"></a>IDebugThreadDestroyEvent2
Bu arabirim, bir iş parçacığının tamamlanması çalıştırıldığında hata ayıklama altyapısı (DE) tarafından oturum hata ayıklama Yöneticisi 'ne (SDM) gönderilir.

## <a name="syntax"></a>Syntax

```
IDebugThreadDestroyEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Bu, bir iş parçacığının sona erini raporlamak için DE bu arabirimi uygular. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) arabiriminin bu arabirimle aynı nesne üzerinde uygulanması gerekir. SDM, arabirime erişmek için [QueryInterface](/cpp/atl/queryinterface) kullanır `IDebugEvent2` .

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 DE, bir iş parçacığının sonlandırıldığından emin olmak için bu olay nesnesini oluşturur ve gönderir. Olay, ayıklanmakta olan programa eklendiği zaman SDM tarafından sağlanan [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) callback işlevi kullanılarak gönderilir.

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDebugThreadDestroyEvent2` .

|Yöntem|Açıklama|
|------------|-----------------|
|[GetExitCode](../../../extensibility/debugger/reference/idebugthreaddestroyevent2-getexitcode.md)|İş parçacığının çıkış kodunu alır.|

## <a name="remarks"></a>Açıklamalar
 Visual Studio, **Iş parçacıkları** penceresini güncelleştirmek için bu olayı kullanır.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
