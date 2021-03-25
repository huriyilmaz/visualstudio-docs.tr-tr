---
description: Bu arabirim, IDebugProperty3 ve IPropertyProxyEESide arabirimlerine işlevsellik sağlayan temel yöntemleri uygular.
title: Ieevisualizerhizmeti | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerService
helpviewer_keywords:
- IEEVisualizerService interface
ms.assetid: 3bdb124b-c582-47ba-b465-13c6a1cdb702
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: cc712d0c86613d0ee6b30d754b759c17e3ab9bdc
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105086774"
---
# <a name="ieevisualizerservice"></a>IEEVisualizerService
> [!IMPORTANT]
> Visual Studio 2015 ' de, değerlendiricileri ifadesi uygulama yöntemi kullanım dışıdır. CLR Expression değerlendiricileri 'ı uygulama hakkında daha fazla bilgi için lütfen bkz. [clr Expression değerlendiricileri](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [yönetilen ifade değerlendirici örneği](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Bu arabirim, [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) ve [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) arabirimlerine işlevsellik sağlayan temel yöntemleri uygular.

## <a name="syntax"></a>Syntax

```
IEEVisualizerService : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Visual Studio, tür görselleştiricileri desteklemek için bir ifade değerlendiricisi (EE) sağlamak üzere bu arabirimi uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 EE, bu arabirimi tür Görselleştiriciler desteğinin bir parçası olarak almak için [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md) 'i çağırır.

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler

|Yöntem|Açıklama|
|------------|-----------------|
|[GetCustomViewerCount](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md)|Bu hizmetin bildiği özel görüntüleyicilerin sayısını alır.|
|[GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)|Özel görüntüleyicilerin listesini alır.|
|[GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)|Bir özellik için proxy nesnesi döndürür.|
|[GetValueDisplayStringCount](../../../extensibility/debugger/reference/ieevisualizerservice-getvaluedisplaystringcount.md)|Belirtilen özellik veya alan için görüntülenecek değer dizelerinin sayısını alır.|

## <a name="remarks"></a>Açıklamalar
 IDE, özellik için özel görüntüleyiciler veya tür Görselleştiriciler olup olmadığını öğrenmek için [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) arabirimini kullanır. Bir Görselleştirici hizmeti ( [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)ile) oluşturarak, ee, `IDebugProperty3` ve [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) işlevlerini sağlayabilir (bir özelliğin değerini görüntülemeyi ve değiştirmeyi destekler) ve bu sayede tür Görselleştiriciler desteklenir.

 Bir EE 'ın kendisi tarafından uygulanan özel görüntüleyenler varsa, EE `CLSID` Bu özel görüntüleyicilerin s 'Leri [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)tarafından döndürülen listenin sonuna ekleyebilir. Bu, bir EE 'ın hem tür Görselleştiriciler hem de kendi özel görüntüleyicilerini desteklemesini sağlar. [GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) 'un özel görüntüleyicilerin eklenmesini yansıttığından emin olun.

 Görselleştiriciler ve görüntüleyiciler arasındaki fark hakkında bir açıklama için bkz. [tür görselleştiricisi ve özel Görüntüleyici](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md) .

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: ee. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)
- [Tür Görselleştiricisi ve Özel Görüntüleyici](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
