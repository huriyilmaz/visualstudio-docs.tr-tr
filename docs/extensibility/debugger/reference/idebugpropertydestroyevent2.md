---
description: Bu arabirim, belirli bir belgeyle ilişkili bir özellik yok etmek üzereyken hata ayıklama altyapısı (DE) tarafından oturum hata ayıklama yöneticisine (SDM) gönderilir.
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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 8326ba7248e5c1e351cae0e625794cf3af7ab08e
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725171"
---
# <a name="idebugpropertydestroyevent2"></a>IDebugPropertyDestroyEvent2
Bu arabirim, belirli bir belgeyle ilişkili bir özellik yok etmek üzereyken hata ayıklama altyapısı (DE) tarafından oturum hata ayıklama yöneticisine (SDM) gönderilir.

## <a name="syntax"></a>Syntax

```
IDebugPropertyDestroyEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 DE, bir özelliğin yok edilmiş olduğunu rapor etmek için bu arabirimini uygulamaya almaktadır. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) arabirimi, bu arabirimle aynı nesne üzerinde uygulanarak gerçekleştir gerekir. SDM, [arabirime erişmek için QueryInterface](/cpp/atl/queryinterface) `IDebugEvent2` kullanır. DE daha önce bir betikle ilişkili bir özellik oluşturdu ise bu arabirim uygulanır; özelliğini yok etmek ilişkili betiği IDE'den kaldırır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 DE bu olay nesnesini oluşturur ve bir özelliğin yok edilmiş olduğunu rapor etmek için gönderir. Olay, hata ayıklama yapılan programa ekli olduğunda SDM tarafından sağlanan [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) geri çağırma işlevi kullanılarak gönderilir.

## <a name="methods-in-vtable-order"></a>VTable Sırasına Göre Yöntemler
 Aşağıdaki tabloda yöntemini `IDebugPropertyDestroyEvent2` gösterir.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertydestroyevent2-getdebugproperty.md)|Yok edilecek özelliği alır.|

## <a name="remarks"></a>Açıklamalar
 Bu olayların neden kullanıldıklarına ilişkin ayrıntılar için [bkz. IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md) açıklamaları.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)
