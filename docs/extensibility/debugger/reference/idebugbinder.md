---
description: Bu arabirim, genellikle sembol sağlayıcısı tarafından döndürülen bir sembol alanını, simgenin geçerli değerini içeren bir bellek bağlamına veya nesnesine bağlar.
title: Idebugciltçi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder
helpviewer_keywords:
- IDebugBinder interface
ms.assetid: d1f31e5b-c6e2-4e02-8959-b3e86041b29c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: febe22338ddeaf275b37ae09c76921c91ec509da
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102143629"
---
# <a name="idebugbinder"></a>IDebugBinder
> [!IMPORTANT]
> Visual Studio 2015 ' de, değerlendiricileri ifadesi uygulama yöntemi kullanım dışıdır. CLR Expression değerlendiricileri 'ı uygulama hakkında daha fazla bilgi için lütfen bkz. [clr Expression değerlendiricileri](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [yönetilen ifade değerlendirici örneği](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Bu arabirim, genellikle sembol sağlayıcısı tarafından döndürülen bir sembol alanını, simgenin geçerli değerini içeren bir bellek bağlamına veya nesnesine bağlar.

## <a name="syntax"></a>Syntax

```
IDebugBinder : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Bu arabirim, ifade değerlendirmesini destekler ve hata ayıklama altyapısı (DE) tarafından uygulanmalıdır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu arabirim, ifade değerlendirmesi sürecinde kullanılır ve genellikle [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) ve [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)uygulamalarında kullanılır.

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDebugBinder` .

|Yöntem|Açıklama|
|------------|-----------------|
|[Bağladığınızda](../../../extensibility/debugger/reference/idebugbinder-bind.md)|Simgenin geçerli değerini içeren bellek bağlamını veya nesnesini alır.|
|[ResolveRuntimeType](../../../extensibility/debugger/reference/idebugbinder-resolveruntimetype.md)|Bir nesnenin çalışma zamanı türünü belirler.|
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugbinder-getmemorycontext.md)|Bir nesne konumunu veya bellek adresini bir bellek bağlamına dönüştürür.|
|[GetFunctionObject](../../../extensibility/debugger/reference/idebugbinder-getfunctionobject.md)|İşlev parametreleri oluşturmak için kullanılan bir [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) nesnesi alır.|
|[ResolveDynamicType](../../../extensibility/debugger/reference/idebugbinder-resolvedynamictype.md)|Bir değişkenin tam türünü alır.|

## <a name="remarks"></a>Açıklamalar
 Bu arabirim, ayrıştırma ağaçlarında ifade değerlendiricisi tarafından kullanılan nesneleri döndürür. İfade değerlendirici, ifadedeki sembolleri, her bir sembolü kaynak koddaki türü ve konumu bakımından açıklayan [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)örneklerine dönüştürmek için sembol sağlayıcısını kullanarak bir ifadeyi ayrıştırır. [Bind](../../../extensibility/debugger/reference/idebugbinder-bind.md) yöntemi nesneleri, `IDebugField` bir sembol türünü, bellekteki gerçek bir değere bağlayan veya bağlayan [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) nesnelerine dönüştürür. `IDebugObject`Daha sonra bu nesneler daha sonra değerlendirme için bir ayrıştırma ağacında depolanır.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: ee. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
