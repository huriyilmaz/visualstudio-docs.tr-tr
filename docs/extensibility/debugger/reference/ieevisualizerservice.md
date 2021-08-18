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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: dce24bb341c4b84fb91b6deedf83c96b67520831
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122125874"
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
 Visual Studio, bir ifade değerlendiricisi 'nin (EE) tür görselleştiricilerini desteklemesini sağlamak için bu arabirimi uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 EE, bu arabirimi tür görselleştiriciler için desteğinin bir parçası olarak almak üzere [createvisualizerservice](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md) ' i çağırır.

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler

|Yöntem|Açıklama|
|------------|-----------------|
|[GetCustomViewerCount](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md)|Bu hizmetin bildiği özel görüntüleyicilerin sayısını alır.|
|[GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)|Özel görüntüleyicilerin listesini alır.|
|[GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)|Bir özellik için proxy nesnesi döndürür.|
|[GetValueDisplayStringCount](../../../extensibility/debugger/reference/ieevisualizerservice-getvaluedisplaystringcount.md)|Belirtilen özellik veya alan için görüntülenecek değer dizelerinin sayısını alır.|

## <a name="remarks"></a>Açıklamalar
 IDE, özellik için özel görüntüleyiciler veya tür Görselleştiriciler olup olmadığını öğrenmek için [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) arabirimini kullanır. bir görselleştirici hizmeti ( [createvisualizerservice](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)ile) oluşturarak EE, `IDebugProperty3` ve [ıpropertyproxyeeside](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) işlevlerini sağlayabilir (bir özelliğin değerini görüntülemeyi ve değiştirmeyi destekler) ve bu sayede tür görselleştiriciler desteklenir.

 bir EE kendi kendine uyguladığı özel görüntüleyiciler varsa, EE `CLSID` bu özel görüntüleyicilerin s 'leri [getcustomviewerlist](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)tarafından döndürülen listenin sonuna ekleyebilir. bu, EE görselleştiriciler ve kendi özel görüntüleyicilerinin her ikisini de desteklemesini sağlar. [GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) 'un özel görüntüleyicilerin eklenmesini yansıttığından emin olun.

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
