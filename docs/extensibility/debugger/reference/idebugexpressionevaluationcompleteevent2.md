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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b30b61c0b7a9a9f3e06465a6b194c882213afb34
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105092208"
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
