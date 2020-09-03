---
title: IDebugEntryPointEvent2 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80730323"
---
# <a name="idebugentrypointevent2"></a>IDebugEntryPointEvent2
Hata ayıklama altyapısı (DE), program kullanıcı kodunun ilk yönergesini yürütmek üzere olduğunda, bu arayüzü oturum hata ayıklama Yöneticisi 'ne (SDM) gönderir.

## <a name="syntax"></a>Syntax

```
IDebugEntryPointEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 DE bu arabirimi normal işlemlerinin bir parçası olarak uygular. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) arabiriminin bu arabirimle aynı nesne üzerinde uygulanması gerekir. SDM, arabirime erişmek için [QueryInterface](/cpp/atl/queryinterface) kullanır `IDebugEvent2` .

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 , Hata ayıklaması yapılan program yüklendiğinde ve kullanıcı kodunun ilk yönergesini yürütmeye hazırsa bu olay nesnesini oluşturur ve gönderir. Olay, hata ayıklamakta olan programa eklendiğinde SDM tarafından sağlanan [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) callback işlevi kullanılarak gönderilir.

## <a name="remarks"></a>Açıklamalar
- [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) , program ilk yönergeyi yürütmek üzere olduğunda gönderilir. Örneğin, `IDebugEntryPoint2` program kullanıcının işlevini yürütmek üzere olduğunda gönderilir `main` .

 Aynı olduğunda `IDebugEntryPointEvent2` , geçerli kod konumu kullanıcı kodunun ilk yönergesinde (gibi) olmalıdır `main` .

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)
