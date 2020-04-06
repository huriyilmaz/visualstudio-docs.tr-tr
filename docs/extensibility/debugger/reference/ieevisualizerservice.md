---
title: IEEVisualizerService | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerService
helpviewer_keywords:
- IEEVisualizerService interface
ms.assetid: 3bdb124b-c582-47ba-b465-13c6a1cdb702
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 40d21dcc9b1da0e1e2250adcfad59b3ef46a2113
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717934"
---
# <a name="ieevisualizerservice"></a>IEEVisualizerService
> [!IMPORTANT]
> Visual Studio 2015'te ifade değerlendiricilerinin bu şekilde uygulanması amortismana uymaktadır. CLR ifade değerlendiricilerinin uygulanması hakkında bilgi için lütfen [CLR İfade Değerlendiriciler](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [Yönetilen İfade Değerlendirici Örneği'ne](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)bakın.

 Bu arabirim, [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) ve [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) arabirimlerine işlevsellik sağlayan önemli yöntemler uygular.

## <a name="syntax"></a>Sözdizimi

```
IEEVisualizerService : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Visual Studio, bir ifade değerlendiricinin (EE) tür görselleştiricilerini desteklemesine izin vermek için bu arabirimi uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 EE, type visualizers için verdiği desteğin bir parçası olarak bu arabirimi elde etmek için [CreateVisualizerService'i](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md) çağırır.

## <a name="methods-in-vtable-order"></a>Vtable sırasına göre yöntemler

|Yöntem|Açıklama|
|------------|-----------------|
|[GetCustomViewerCount](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md)|Bu hizmetin bildiği özel görüntüleyenlerin sayısını alır.|
|[GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)|Özel görüntüleyenlerin listesini alır.|
|[GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)|Bir özellik için proxy nesnesi döndürür.|
|[GetValueDisplayStringCount](../../../extensibility/debugger/reference/ieevisualizerservice-getvaluedisplaystringcount.md)|Belirtilen özellik veya alan için görüntülenecek değer dizelerinin sayısını alır.|

## <a name="remarks"></a>Açıklamalar
 IDE, özellik için özel görüntüleyenler veya yazı görüntüleyiciler olup olmadığını belirlemek için [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) arabirimini kullanır. Bir görselleştirici hizmeti oluşturarak [(CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)ile), EE işlevselliği `IDebugProperty3` [iPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) (bir özelliğin değerini görüntülemeyi ve değiştirmeyi destekler) sağlayabilir ve böylelikle tür görselleştiricilerini destekleyebilir.

 Bir EE'nin kendisi uyguladığı özel görüntüleyenler varsa, `CLSID`EE bu özel görüntüleyenlerin s'lerini [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)tarafından döndürülen listenin sonuna ekleyebilir. Bu, bir EE'nin hem tür görselleştiricilerini hem de kendi özel görüntüleyicileri desteklemesini sağlar. [Sadece GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) herhangi bir özel izleyicilerin ek yansıtır emin olun.

 Görselleştiriciler ve görüntüleyenler arasındaki farkı tartışmak için [Görselleştirici Yazın ve Özel Görüntüleyici'ye](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md) bakın.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: ee.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [İfade Değerlendirme Arabirimleri](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)
- [Tür Görselleştiricisi ve Özel Görüntüleyici](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
