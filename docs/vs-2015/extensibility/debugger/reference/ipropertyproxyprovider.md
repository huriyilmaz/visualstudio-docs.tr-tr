---
title: IPropertyProxyProvider | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IPropertyProxyProvider
helpviewer_keywords:
- IPropertyProxyProvider interface
ms.assetid: 52e9f7fc-6fe0-4d23-890b-5673dca8c3cb
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 39cdc7769765a7680905fca5faa49222bf0a3b6d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65700039"
---
# <a name="ipropertyproxyprovider"></a>IPropertyProxyProvider
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu arabirim, bir nesnenin verilerini görüntülemek ve değiştirmek için bir proxy arabirimi sağlar.  
  
## <a name="syntax"></a>Syntax  
  
```  
IPropertyProxyProvider : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Implemenonun notları  
 İfade değerlendirici (EE), bu arabirimi, [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) arabirimini uygulayan aynı nesne üzerinde, görselin tür Görselleştiriciler desteğinin bir parçası olarak uygular.  
  
## <a name="notes-for-callers"></a>Arayanlar İçin Notlar  
 [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) `IDebugProperty3` Bu arabirimi edinmek Için arabirim üzerinde QueryInterface 'i çağırın.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler  
 `IPropertyProxyProvider`Arabirimi aşağıdaki yöntemi uygular:  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md)|Bir nesne üzerindeki verileri görüntülemek için bir özellik proxy arabirimini alır.|  
  
## <a name="remarks"></a>Açıklamalar  
 EE bu arabirimi uygusa da [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) 'nin uygulanması genellikle [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)tarafından işlenir. IEEVisualizerService arabirimini edinme hakkında ayrıntılar için bkz. [verileri görselleştirme ve görüntüleme](../../../extensibility/debugger/visualizing-and-viewing-data.md) .  
  
## <a name="requirements"></a>Gereksinimler  
 Üst bilgi: msdbg. h  
  
 Ad alanı: Microsoft. VisualStudio. Debugger. Interop  
  
 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çekirdek arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)   
 [Tür görselleştiricisi ve özel Görüntüleyici](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)   
 [Verileri Görselleştirme ve Görüntüleme](../../../extensibility/debugger/visualizing-and-viewing-data.md)
