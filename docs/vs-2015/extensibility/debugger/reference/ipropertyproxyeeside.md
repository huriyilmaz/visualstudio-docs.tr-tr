---
title: IPropertyProxyEESide | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide
helpviewer_keywords:
- IPropertyProxyEESide interface
ms.assetid: cf227cf8-39d9-4758-8f7e-a697aebb1926
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 660c792d9e13fabbd433aee46c57474fb824453f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65684665"
---
# <a name="ipropertyproxyeeside"></a>IPropertyProxyEESide
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu arabirim, ilişkili nesne üzerindeki verileri görüntülemek için yöntemler sağlar. Bu arabirim, tür Görselleştiriciler için desteğin bir parçasıdır.  
  
## <a name="syntax"></a>Syntax  
  
```  
IPropertyProxyEESide : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Implemenonun notları  
 Bir ifade değerlendirici bu arabirimi, tür görselleştiricileri desteklemek için uygular.  
  
## <a name="notes-for-callers"></a>Arayanlar İçin Notlar  
 Bu arabirimi almak için [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) çağrısı yapın. [IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md) arabirimini almak Için bir [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) arabiriminde [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) 'i çağırın.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler  
 Aşağıdaki yöntemler bu arabirim tarafından uygulanır:  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[InitSourceDataProvider](../../../extensibility/debugger/reference/ipropertyproxyeeside-initsourcedataprovider.md)|Bir veri kaynağı sağlayıcısını, nesnenin verilerine erişilebilmesi için başlatır.|  
|[GetManagedViewerCreationData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getmanagedviewercreationdata.md)|Nesnenin derlemesi hakkındaki bilgileri alır.|  
|[GetInitialData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getinitialdata.md)|Nesne için ilk verileri alır.|  
|[CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)|Var olan veri depolamanın bir kopyasını oluşturur.|  
|[InPlaceUpdateObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject.md)|Var olan veri depolamaya bir başvuru oluşturur.|  
|[ResolveAssemblyRef](../../../extensibility/debugger/reference/ipropertyproxyeeside-resolveassemblyref.md)|Bu nesneyi içeren derleme bağlamında belirli bir derleme hakkındaki bilgileri alır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir tür görselleştiricisi, bu arabirimin parçası olduğu nesneyle ilişkili değerlere erişmek için bu arabirimi kullanır. Verilere, verilerin salt okunurdur görünümü sağlayan [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) arabirimi üzerinden erişilir.  
  
## <a name="requirements"></a>Gereksinimler  
 Üst bilgi: msdbg. h  
  
 Ad alanı: Microsoft. VisualStudio. Debugger. Interop  
  
 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çekirdek arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)   
 [Tür görselleştiricisi ve özel Görüntüleyici](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
