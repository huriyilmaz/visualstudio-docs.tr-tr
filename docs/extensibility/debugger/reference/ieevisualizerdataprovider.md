---
description: Bu arabirim, bir nesnenin değerini tür görselleştiricisi aracılığıyla değiştirme olanağı sağlar.
title: IEEVisualizerDataProvider | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerDataProvider
helpviewer_keywords:
- IEEVisualizerDataProvider interface
ms.assetid: 5fdfe6e3-b94e-4edb-acc5-41d8773d8ca5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d52f90e0fe2dc33fd8d790bfce5ef9304f6df745
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122103513"
---
# <a name="ieevisualizerdataprovider"></a>IEEVisualizerDataProvider
> [!IMPORTANT]
> Visual Studio 2015 ' de, değerlendiricileri ifadesi uygulama yöntemi kullanım dışıdır. CLR Expression değerlendiricileri 'ı uygulama hakkında daha fazla bilgi için lütfen bkz. [clr Expression değerlendiricileri](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [yönetilen ifade değerlendirici örneği](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Bu arabirim, bir nesnenin değerini tür görselleştiricisi aracılığıyla değiştirme olanağı sağlar.

## <a name="syntax"></a>Syntax

```
IEEVisualizerDataProvider : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 İfade değerlendirici, bir tür görselleştiricisi aracılığıyla bir özellik nesnesindeki verileri değiştirmeyi desteklemek için bu arabirimi uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu arabirim, [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)çağrısıyla [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) nesnesini oluşturmak için kullanılır. Daha fazla ayrıntı için bkz. [verileri görselleştirme ve görüntüleme](../../../extensibility/debugger/visualizing-and-viewing-data.md) .

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler

|Yöntem|Açıklama|
|------------|-----------------|
|[CanSetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-cansetobjectforvisualizer.md)|Bu Görselleştirici temsil ettiği nesnenin (ve daha sonra da bu değerin) güncelleştirilmesi mümkün olup olmadığını belirler.|
|[GetNewObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getnewobjectforvisualizer.md)|Bu Görselleştirici için nesnenin yeniden değerlendirilmesini zorlar.|
|[GetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getobjectforvisualizer.md)|Bu Görselleştirici için var olan bir nesneyi alır (değerlendirme yapılmaz).|
|[SetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-setobjectforvisualizer.md)|Bu Görselleştirici için nesneyi güncelleştirir, böylece Görselleştirici sunduğu değeri değiştirir.|

## <a name="remarks"></a>Açıklamalar
 Görselleştiricisi hizmeti ( [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) arabirimi tarafından temsil edilen ve [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)tarafından döndürülen), arabirimi uygulayan nesneye bir başvuru tutar `IEEVisualizerDataProvider` . Sonuç olarak, `IEEVisualizerDataProvider` Bu nesnenin nesneye bir başvuru elde etmesi durumunda arabirim, [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) uygulayan aynı nesneye uygulanmamalıdır `IEEVisualizerService` : döngüsel bir başvuru sonuçları ve nesneler yok edildiğinde kilitlenme oluşur. Önerilen yaklaşım, `IEEVisualizerDataProvider` `IDebugProperty2` nesnesine çağrı yapmadan nesnenin temsilci olarak ekleneceği ayrı bir nesneye uygulanır `IUnknown::AddRef` .

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: ee. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)
- [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)
- [Verileri Görselleştirme ve Görüntüleme](../../../extensibility/debugger/visualizing-and-viewing-data.md)
