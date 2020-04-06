---
title: IEEVisualizerDataProvider | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerDataProvider
helpviewer_keywords:
- IEEVisualizerDataProvider interface
ms.assetid: 5fdfe6e3-b94e-4edb-acc5-41d8773d8ca5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a10f306b6c507f6db7add17931b8a38d926a37d9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718057"
---
# <a name="ieevisualizerdataprovider"></a>IEEVisualizerDataProvider
> [!IMPORTANT]
> Visual Studio 2015'te ifade değerlendiricilerinin bu şekilde uygulanması amortismana uymaktadır. CLR ifade değerlendiricilerinin uygulanması hakkında bilgi için lütfen [CLR İfade Değerlendiriciler](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [Yönetilen İfade Değerlendirici Örneği'ne](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)bakın.

 Bu arabirim, bir tür görselleştiricisi aracılığıyla nesnenin değerini değiştirme olanağı sağlar.

## <a name="syntax"></a>Sözdizimi

```
IEEVisualizerDataProvider : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 İfade değerlendiricisi, bir tür görselleştiricisi aracılığıyla özellik nesnesi üzerindeki verileri değiştirmeyi desteklemek için bu arabirimi uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu arabirim [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)için bir çağrı yoluyla [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) nesne oluştururken kullanılır. Daha fazla ayrıntı için [Verileri Görselleştirme ve Görüntüleme'ye](../../../extensibility/debugger/visualizing-and-viewing-data.md) bakın.

## <a name="methods-in-vtable-order"></a>Vtable sırasına göre yöntemler

|Yöntem|Açıklama|
|------------|-----------------|
|[CanSetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-cansetobjectforvisualizer.md)|Bu görselleştiricinin temsil ettiği nesneyi (ve daha sonra değerini) güncelleştirmenin mümkün olup olmadığını belirler.|
|[GetNewObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getnewobjectforvisualizer.md)|Bu görselleştirici için nesnenin yeniden değerlendirilmesini zorlar.|
|[GetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getobjectforvisualizer.md)|Bu görselleştirici için varolan bir nesne alır (değerlendirme yapılmaz).|
|[SetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-setobjectforvisualizer.md)|Bu görselleştiriciiçin nesneyi güncelleştirir ve böylece görselleştiricinin sunduğu değeri değiştirir.|

## <a name="remarks"></a>Açıklamalar
 Visualizer hizmeti [(IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) arabirimi tarafından temsil edildiği ve [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)tarafından döndürülen) `IEEVisualizerDataProvider` arabirimi uygulayan nesneye bir referans tutar. Sonuç olarak, `IEEVisualizerDataProvider` bu nesne `IEEVisualizerService` nesneye bir başvuru tutarsa, arabirim [IDebugProperty2'yi](../../../extensibility/debugger/reference/idebugproperty2.md) uygulayan nesne üzerinde uygulanmamalıdır: nesneler yok edildiğinde dairesel bir başvuru sonuçları ve bir kilitlenme oluşur. Önerilen yaklaşım, nesnenin `IEEVisualizerDataProvider` `IDebugProperty2` onu çağırmadan `IUnknown::AddRef` devraldığı ayrı bir nesne üzerinde uygulamaktır.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: ee.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [İfade Değerlendirme Arabirimleri](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)
- [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)
- [Verileri Görselleştirme ve Görüntüleme](../../../extensibility/debugger/visualizing-and-viewing-data.md)
