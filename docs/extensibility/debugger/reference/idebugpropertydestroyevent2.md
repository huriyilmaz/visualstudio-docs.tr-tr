---
description: Bu arabirim, belirli bir belgeyle ilişkili bir özelliğin yok edileceği bir özellik olduğunda, hata ayıklama altyapısı (DE) tarafından oturum hata ayıklama Yöneticisi (SDM) tarafından gönderilir.
title: IDebugPropertyDestroyEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPropertyDestroyEvent2
helpviewer_keywords:
- IDebugPropertyDestroyEvent2 interface
ms.assetid: 301b7a75-ecfa-46f1-9131-66cf3e4be147
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d9d0e0751b184ddbf6ebc62e12ed1d3a9bca853c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105083810"
---
# <a name="idebugpropertydestroyevent2"></a>IDebugPropertyDestroyEvent2
Bu arabirim, belirli bir belgeyle ilişkili bir özelliğin yok edileceği bir özellik olduğunda, hata ayıklama altyapısı (DE) tarafından oturum hata ayıklama Yöneticisi (SDM) tarafından gönderilir.

## <a name="syntax"></a>Syntax

```
IDebugPropertyDestroyEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 DE bu arabirimi bir özelliğin yok edildiğini bildirmek için uygular. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) arabiriminin bu arabirimle aynı nesne üzerinde uygulanması gerekir. SDM, arabirime erişmek için [QueryInterface](/cpp/atl/queryinterface) kullanır `IDebugEvent2` . Bu arabirim daha önce bir komut dosyasıyla ilişkili bir özellik oluşturulduysa uygulanır; özelliğin yok edilmesi, ilişkili betiği IDE 'den kaldırır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 DE, bu olay nesnesini oluşturur ve bir özelliğin yok edildiğini bildirmek üzere gönderir. Olay, ayıklanmakta olan programa eklendiği zaman SDM tarafından sağlanan [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) callback işlevi kullanılarak gönderilir.

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 Aşağıdaki tabloda, yöntemi gösterilmektedir `IDebugPropertyDestroyEvent2` .

|Yöntem|Açıklama|
|------------|-----------------|
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertydestroyevent2-getdebugproperty.md)|Yok edilecek özelliği alır.|

## <a name="remarks"></a>Açıklamalar
 Bu olayların neden kullanıldığına ilişkin ayrıntılar için [IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md) açıklamalarını inceleyin.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)
