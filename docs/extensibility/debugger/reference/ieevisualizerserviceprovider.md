---
description: Bu arabirim, IDE için tür görselleştiricisi görevlerini işlemek üzere kullanılan bir Görselleştirici hizmeti oluşturabileceğiniz bir yönteme erişim sağlar.
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
ms.openlocfilehash: bbc67be1904c785f10ea1e3ee3144d2d40380730749247f58be639bbd0cbb8f4
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121389416"
---
# <a name="ieevisualizerserviceprovider"></a>IEEVisualizerServiceProvider
> [!IMPORTANT]
> Visual Studio 2015 ' de, değerlendiricileri ifadesi uygulama yöntemi kullanım dışıdır. CLR Expression değerlendiricileri 'ı uygulama hakkında daha fazla bilgi için lütfen bkz. [clr Expression değerlendiricileri](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [yönetilen ifade değerlendirici örneği](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Bu arabirim, IDE için tür görselleştiricisi görevlerini işlemek üzere kullanılan bir Görselleştirici hizmeti oluşturabileceğiniz bir yönteme erişim sağlar.

## <a name="syntax"></a>Syntax

```
IEEVisualizerServiceProvider : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Visual Studio, bu arabirimi bir görselleştirici hizmeti nesnesi oluşturmak için uygular, bu da `CLSID` Visual Studio ıde 'ye görselleştiriciler türündeki sınıf kimliklerini sağlamak için kullanılır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 ifade değerlendirici (EE), bu arabirimi edinmek için [geteeservice](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md) 'i çağırır.

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler

|Yöntem|Açıklama|
|------------|-----------------|
|[CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)|Görselleştiricisi hizmetini oluşturur|

## <a name="remarks"></a>Açıklamalar
 `IEEVisualizerServiceProvider`Arabirim, [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)uygulamasının uygulanması sırasında elde edilir. bu arabirimin oluşturduğu görselleştiricisi hizmeti, EE uygulamaktan sorumlu olan bir [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) arabirimine işlevsellik sağlamak için kullanılır. EE, tür görselleştiricilerin bir özelliğin değerini görüntülemesine ve değiştirmesine izin veren bir [ıeevisualizerdataprovider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md) arabirimi uygulamaktan de sorumludur.

 Bu arabirimlerin nasıl etkileşim kurabileceğine ilişkin ayrıntılar için bkz. [verileri görselleştirme ve görüntüleme](../../../extensibility/debugger/visualizing-and-viewing-data.md) .

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: ee. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
- [GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [Verileri Görselleştirme ve Görüntüleme](../../../extensibility/debugger/visualizing-and-viewing-data.md)
