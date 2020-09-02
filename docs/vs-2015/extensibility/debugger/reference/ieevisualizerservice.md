---
title: Ieevisualizerhizmeti | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEEVisualizerService
helpviewer_keywords:
- IEEVisualizerService interface
ms.assetid: 3bdb124b-c582-47ba-b465-13c6a1cdb702
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b3bb741aa25cf6695f1dd1d8d66fc0c1846413b8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64798514"
---
# <a name="ieevisualizerservice"></a>IEEVisualizerService
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İfade değerlendirme arabirimleri](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)   
 [Tür Görselleştiricisi ve Özel Görüntüleyici](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
