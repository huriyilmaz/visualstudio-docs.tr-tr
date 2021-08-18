---
description: Bu arabirim, genellikle sembol sağlayıcısı tarafından döndürülen bir sembol alanını, sembolün geçerli değerini içeren bir bellek bağlamına veya nesnesine bağlar.
title: IDebugBinder | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder
helpviewer_keywords:
- IDebugBinder interface
ms.assetid: d1f31e5b-c6e2-4e02-8959-b3e86041b29c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 16b18bb8a1208d6f6a9c4a0c87a73f35b66dec1d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122072843"
---
# <a name="idebugbinder"></a>IDebugBinder
> [!IMPORTANT]
> 2015 Visual Studio de ifade değerlendiricilerini uygulamanın bu yolu kullanım dışıdır. CLR ifade değerlendiricilerini uygulama hakkında bilgi için bkz. [CLR İfade Değerlendiricileri](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [Yönetilen İfade Değerlendirici Örneği.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

 Bu arabirim, genellikle sembol sağlayıcısı tarafından döndürülen bir sembol alanını, sembolün geçerli değerini içeren bir bellek bağlamına veya nesnesine bağlar.

## <a name="syntax"></a>Syntax

```
IDebugBinder : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Bu arabirim ifade değerlendirmesini destekler ve hata ayıklama altyapısı (DE) tarafından uygulanması gerekir.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu arabirim ifade değerlendirme sürecinde kullanılır ve genellikle [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) ve [EvaluateAsync uygulamasında kullanılır.](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)

## <a name="methods-in-vtable-order"></a>Vtable Sırasına Göre Yöntemler
 Aşağıdaki tabloda yöntemlerini `IDebugBinder` gösterir.

|Yöntem|Açıklama|
|------------|-----------------|
|[Bağlamak](../../../extensibility/debugger/reference/idebugbinder-bind.md)|Sembolün geçerli değerini içeren bellek bağlamını veya nesnesini alır.|
|[ResolveRuntimeType](../../../extensibility/debugger/reference/idebugbinder-resolveruntimetype.md)|Bir nesnenin çalışma zamanı türünü belirler.|
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugbinder-getmemorycontext.md)|Nesne konumunu veya bellek adresini bir bellek bağlamına dönüştürür.|
|[GetFunctionObject](../../../extensibility/debugger/reference/idebugbinder-getfunctionobject.md)|İşlev parametrelerini [oluşturmak için kullanılan IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) nesnesini alır.|
|[ResolveDynamicType](../../../extensibility/debugger/reference/idebugbinder-resolvedynamictype.md)|Bir değişkenin tam türünü alır.|

## <a name="remarks"></a>Açıklamalar
 Bu arabirim, ayrıştırma ağaçlarında ifade değerlendiricisi tarafından kullanılan nesneleri döndürür. İfade değerlendiricisi, ifadede yer alan sembolleri, kaynak kodda türü ve konumu açısından her simgeyi açıklayan [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)örneklerine dönüştürmek için sembol sağlayıcısını kullanarak bir ifadeyi ayrıştırıyor. [Bind yöntemi](../../../extensibility/debugger/reference/idebugbinder-bind.md) nesneleri, bir sembol türüne bağlanıp bellekte gerçek bir değere bağlayan `IDebugField` [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) nesnelerine dönüştürür. Bu `IDebugObject` nesneler daha sonra daha sonra değerlendirme için ayrıştırma ağacında depolanır.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: ee.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
