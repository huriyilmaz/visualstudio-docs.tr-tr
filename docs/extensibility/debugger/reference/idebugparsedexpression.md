---
title: IDebugParsedExpression | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugParsedExpression
helpviewer_keywords:
- IDebugParsedExpression interface
ms.assetid: be6486ed-b070-4898-95b1-58581bcb4447
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 22069b8eedb06d67eafaf7333f379a057c1b6f23
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725999"
---
# <a name="idebugparsedexpression"></a>IDebugParsedExpression
> [!IMPORTANT]
> Visual Studio 2015'te ifade değerlendiricilerinin bu şekilde uygulanması amortismana uymaktadır. CLR ifade değerlendiricilerinin uygulanması hakkında bilgi için lütfen [CLR İfade Değerlendiriciler](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [Yönetilen İfade Değerlendirici Örneği'ne](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)bakın.

 Bu arabirim, değerlendirilmeye hazır ayrışmış bir ifadeyi temsil eder.

## <a name="syntax"></a>Sözdizimi

```
IDebugParsedExpression : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Bir ifade değerlendiricisi, değerlendirmeye hazır ayrıştırılmış bir ifadeyi temsil etmek için bu arabirimi uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 [Parse'e](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) yapılan bir çağrı bu arabirimi döndürür.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 Aşağıdaki tabloda `IDebugParsedExpression`. yöntemini gösterir.

|Yöntem|Açıklama|
|------------|-----------------|
|[EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)|Ayrışdırılmış ifadeyi değerlendirir.|

## <a name="remarks"></a>Açıklamalar
 Arayan ifadeyi değerlendirmeye hazır olduğunda, değerlendirme sonucunu içeren bir [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) döndürmek için [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) çağırır. Değerlendirmeye bu iki bölümlü yaklaşım, ayrışma sonra değerlendirme, parsed ifade birden çok kez değerlendirilmesini sağlar, ifade ayrışma zaman alıcı süreci atlayarak.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: ee.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
