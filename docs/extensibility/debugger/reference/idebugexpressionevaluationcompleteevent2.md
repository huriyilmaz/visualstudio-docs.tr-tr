---
description: Bu arabirim, zaman uyumsuz ifade değerlendirmesi tamamlandığında hata ayıklama altyapısı (DE) tarafından oturum hata ayıklama yöneticisine (SDM) gönderilir.
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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: f6690c2bd598b0662cc5ef54170726ac8efe99e2
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725224"
---
# <a name="idebugexpressionevaluationcompleteevent2"></a>IDebugExpressionEvaluationCompleteEvent2
Bu arabirim, zaman uyumsuz ifade değerlendirmesi tamamlandığında hata ayıklama altyapısı (DE) tarafından oturum hata ayıklama yöneticisine (SDM) gönderilir.

## <a name="syntax"></a>Syntax

```
IDebugExpressionEvaluationCompleteEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 DE, EvaluateAsync çağrısıyla başlayan bir ifade değerlendirmesinin tamamlanmasını rapor etmek için [bu arabirimini uygulamaya almaktadır.](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) arabirimi, bu arabirimle aynı nesne üzerinde uygulanarak gerçekleştir gerekir. SDM, [arabirime erişmek için QueryInterface](/cpp/atl/queryinterface) `IDebugEvent2` kullanır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 DE, ifade değerlendirmesinin tamamlanmasını rapor etmek için bu olay nesnesini oluşturur ve gönderir. Olay, hata ayıklaması yapılan programa ekli olduğunda SDM tarafından sağlanan [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) geri çağırma işlevi kullanılarak gönderilir.

## <a name="methods-in-vtable-order"></a>VTable Sırasına Göre Yöntemler
 Aşağıdaki tabloda yöntemlerini `IDebugExpressionEvaluationCompleteEvent2` gösterir.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetExpression](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)|Özgün ifadeyi alır.|
|[GetResult](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md)|İfade değerlendirmesinin sonucu alır.|

## <a name="remarks"></a>Açıklamalar
 Değerlendirmenin başarılı olup olmadığı, DE'nin bu olayı göndermesi gerekir.

 Değerlendirme başarılı olmadı ise GetPropertyInfo tarafından döndürülen DEBUG_PROPERTY_INFO yapısında ve bayrakları ayarlanmaz `DEBUG_PROPINFO_VALUE` `DEBUG_PROPINFO_ATTRIB` [](../../../extensibility/debugger/reference/debug-property-info.md) [(IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) [](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) nesnesi DE tarafından oluşturulur ve değerlendirme başarısız olursa `IDebugExpressionEvaluationCompleteEvent2` olayda döndürülür).

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
