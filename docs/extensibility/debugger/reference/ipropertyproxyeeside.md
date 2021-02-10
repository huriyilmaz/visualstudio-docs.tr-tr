---
title: IPropertyProxyEESide | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide
helpviewer_keywords:
- IPropertyProxyEESide interface
ms.assetid: cf227cf8-39d9-4758-8f7e-a697aebb1926
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f0331365716c8399c1b2a565fc8046482df5d80f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99938908"
---
# <a name="ipropertyproxyeeside"></a>IPropertyProxyEESide
Bu arabirim, ilişkili nesne üzerindeki verileri görüntülemek için yöntemler sağlar. Bu arabirim, tür Görselleştiriciler için desteğin bir parçasıdır.

## <a name="syntax"></a>Syntax

```
IPropertyProxyEESide : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Bir ifade değerlendirici bu arabirimi, tür görselleştiricileri desteklemek için uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu arabirimi almak için [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) çağrısı yapın. [IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md) arabirimini almak Için bir [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) arabiriminde [QueryInterface](/cpp/atl/queryinterface) 'i çağırın.

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

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [Tür Görselleştiricisi ve Özel Görüntüleyici](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
