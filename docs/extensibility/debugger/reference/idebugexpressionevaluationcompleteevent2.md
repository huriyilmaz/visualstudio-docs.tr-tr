---
description: Bu arabirim, zaman uyumsuz ifade değerlendirmesi tamamlandığında, hata ayıklama altyapısı (DE) tarafından oturum hata ayıklama Yöneticisi (SDM) tarafından gönderilir.
title: IDebugExpressionEvaluationCompleteEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluationCompleteEvent2
helpviewer_keywords:
- IDebugExpressionEvaluationCompleteEvent2
ms.assetid: d538fc19-55bf-4231-9595-eb01e84fd1d8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8a56cb564470263c9ae98fb0adda84881f25209c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102152604"
---
# <a name="idebugexpressionevaluationcompleteevent2"></a>IDebugExpressionEvaluationCompleteEvent2
Bu arabirim, zaman uyumsuz ifade değerlendirmesi tamamlandığında, hata ayıklama altyapısı (DE) tarafından oturum hata ayıklama Yöneticisi (SDM) tarafından gönderilir.

## <a name="syntax"></a>Syntax

```
IDebugExpressionEvaluationCompleteEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Bu arabirimi, [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)çağrısıyla başlatılan bir ifade değerlendirmesinin tamamlanmasını RAPORLAMAK için de uygular. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) arabiriminin bu arabirimle aynı nesne üzerinde uygulanması gerekir. SDM, arabirime erişmek için [QueryInterface](/cpp/atl/queryinterface) kullanır `IDebugEvent2` .

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 DE, bir ifade değerlendirmesinin tamamlanmasını raporlamak için bu olay nesnesini oluşturur ve gönderir. Olay, hata ayıklamakta olan programa eklendiğinde SDM tarafından sağlanan [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) callback işlevi kullanılarak gönderilir.

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDebugExpressionEvaluationCompleteEvent2` .

|Yöntem|Açıklama|
|------------|-----------------|
|[GetExpression](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)|Özgün ifadeyi alır.|
|[GetResult](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md)|İfade değerlendirmesinin sonucunu alır.|

## <a name="remarks"></a>Açıklamalar
 Aynı değerlendirme başarılı olup olmadığı için DE bu olayı göndermelidir.

 Değerlendirme başarılı olmazsa, `DEBUG_PROPINFO_VALUE` ve `DEBUG_PROPINFO_ATTRIB` bayrakları [getpropertyınfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) tarafından döndürülen [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) yapısında ayarlanmayacak ( [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) nesnesi, tarafından oluşturulur ve `IDebugExpressionEvaluationCompleteEvent2` değerlendirme başarısız olursa olayda döndürülür).

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
