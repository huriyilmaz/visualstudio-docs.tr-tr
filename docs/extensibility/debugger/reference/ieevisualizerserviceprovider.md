---
description: Bu arabirim, IDE için tür görselleştirici görevlerini işlemek için kullanılan bir görselleştirici hizmeti oluştura bir yönteme erişim verir.
title: IEEVisualizerServiceProvider | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerServiceProvider
helpviewer_keywords:
- IEEVisualizerServiceProvider interface
ms.assetid: 859d1a51-1c65-4c8b-ae74-3b74b181ebcd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: acaa7071d2b204fead807f9fb2e36ec0d5abff2b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122125822"
---
# <a name="ieevisualizerserviceprovider"></a>IEEVisualizerServiceProvider
> [!IMPORTANT]
> 2015 Visual Studio de ifade değerlendiricilerini uygulamanın bu yolu kullanım dışıdır. CLR ifade değerlendiricilerini uygulama hakkında bilgi için bkz. [CLR İfade Değerlendiricileri](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [Yönetilen İfade Değerlendirici Örneği.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

 Bu arabirim, IDE için tür görselleştirici görevlerini işlemek için kullanılan bir görselleştirici hizmeti oluştura bir yönteme erişim verir.

## <a name="syntax"></a>Syntax

```
IEEVisualizerServiceProvider : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Visual Studio bir görselleştirici hizmeti nesnesi oluşturmak için bu arabirimi uygulayan ve bu nesne de Visual Studio IDE'ye tür görselleştiricilerin `CLSID` sınıf kimliklerini (s) sağlamak için kullanılır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 İfade değerlendiricisi (EE) bu arabirimi [almak için GetEEService'i](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md) arar.

## <a name="methods-in-vtable-order"></a>Vtable sırasına göre yöntemler

|Yöntem|Açıklama|
|------------|-----------------|
|[CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)|Görselleştirici hizmetini oluşturur|

## <a name="remarks"></a>Açıklamalar
 Arabirimi `IEEVisualizerServiceProvider` EvaluateSync uygulaması sırasında [elde edilir.](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) Bu arabirimin oluşturduğu görselleştirici hizmeti, uygulamanın sorumlu olduğu [bir IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) arabirimine EE sağlamak için kullanılır. Bu EE, tür görselleştiricilerinin bir özelliğin değerini görüntülemesine ve değiştirmesine olanak sağlayan [bir IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md) arabirimi uygulamakla da sorumludur.

 Bu [arabirimlerin nasıl etkileşim kurduğuna ilişkin](../../../extensibility/debugger/visualizing-and-viewing-data.md) ayrıntılar için bkz. Verileri Görselleştirme ve Görüntüleme.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: ee.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
- [GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [Verileri Görselleştirme ve Görüntüleme](../../../extensibility/debugger/visualizing-and-viewing-data.md)
