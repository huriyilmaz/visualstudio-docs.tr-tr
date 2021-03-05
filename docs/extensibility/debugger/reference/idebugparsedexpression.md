---
description: Bu arabirim, değerlendirilen bir ayrıştırılmış ifadeyi temsil eder.
title: IDebugParsedExpression | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugParsedExpression
helpviewer_keywords:
- IDebugParsedExpression interface
ms.assetid: be6486ed-b070-4898-95b1-58581bcb4447
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: bf978f6d2775c720cfff528ceb8a557fd96ae00a
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102169944"
---
# <a name="idebugparsedexpression"></a>IDebugParsedExpression
> [!IMPORTANT]
> Visual Studio 2015 ' de, değerlendiricileri ifadesi uygulama yöntemi kullanım dışıdır. CLR Expression değerlendiricileri 'ı uygulama hakkında daha fazla bilgi için lütfen bkz. [clr Expression değerlendiricileri](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [yönetilen ifade değerlendirici örneği](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Bu arabirim, değerlendirilen bir ayrıştırılmış ifadeyi temsil eder.

## <a name="syntax"></a>Syntax

```
IDebugParsedExpression : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Bir ifade değerlendirici, bu arabirimi değerlendirme için hazırlanma bir ayrıştırılmış ifadeyi temsil etmek için uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 [Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) çağrısı bu arabirimi döndürür.

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 Aşağıdaki tabloda, yöntemi gösterilmektedir `IDebugParsedExpression` .

|Yöntem|Açıklama|
|------------|-----------------|
|[EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)|Ayrıştırılmış ifadeyi değerlendirir.|

## <a name="remarks"></a>Açıklamalar
 Çağıran, ifadeyi değerlendirmeye hazırsa, değerlendirmenin sonucunu içeren bir [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) döndürmek için [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) çağırır. Değerlendirmek için bu iki bölümlü yaklaşım, ayrıştırma ve değerlendirme, ayrıştırılmış ifadenin birden çok kez değerlendirilmesini sağlar ve bu da ifadeyi ayrıştırmak için zaman alan işlem işlemini atlar.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: ee. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
