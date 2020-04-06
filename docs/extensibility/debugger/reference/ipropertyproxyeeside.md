---
title: IPropertyProxyEESide | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide
helpviewer_keywords:
- IPropertyProxyEESide interface
ms.assetid: cf227cf8-39d9-4758-8f7e-a697aebb1926
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c89cecbf22091a45e31c307c5b523ac8aa4c924e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714852"
---
# <a name="ipropertyproxyeeside"></a>IPropertyProxyEESide
Bu arabirim, ilişkili nesnedeki verileri görüntülemek için yöntemler sağlar. Bu arabirim, tür görüntüleyiciler için desteğin bir parçasıdır.

## <a name="syntax"></a>Sözdizimi

```
IPropertyProxyEESide : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Bir ifade değerlendiricisi, tür görselleştiricilerini desteklemek için bu arabirimi uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu arabirimi elde etmek için [GetPropertyProxy'yi](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) arayın. [IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md) arabirimini elde etmek için [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) arabiriminde [QueryInterface'i](/cpp/atl/queryinterface) arayın.

## <a name="methods-in-vtable-order"></a>Vtable sırasına göre yöntemler
 Aşağıdaki yöntemler bu arabirim tarafından uygulanır:

|Yöntem|Açıklama|
|------------|-----------------|
|[InitSourceDataProvider](../../../extensibility/debugger/reference/ipropertyproxyeeside-initsourcedataprovider.md)|Nesnenin verilerine erişilebilmek için bir veri kaynağı sağlayıcısını başolarak ele alar.|
|[GetManagedViewerCreationData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getmanagedviewercreationdata.md)|Nesnenin derlemesi hakkındaki bilgileri alır.|
|[GetInitialData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getinitialdata.md)|Nesnenin ilk verilerini alır.|
|[CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)|Varolan bir veri depolamasının kopyasını oluşturur.|
|[InPlaceUpdateObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject.md)|Varolan bir veri depolamasına başvuru oluşturur.|
|[ResolveAssemblyRef](../../../extensibility/debugger/reference/ipropertyproxyeeside-resolveassemblyref.md)|Bu nesneyi içeren derleme bağlamında belirli bir derleme hakkındaki bilgileri alır.|

## <a name="remarks"></a>Açıklamalar
 Bir tür görselleştiricisi, bu arabirimin parçası olduğu nesneyle ilişkili değerlere erişmek için bu arabirimi kullanır. Verilere, verilerin salt okunur görünümünü sağlayan [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) arabirimi üzerinden erişilir.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [Tür Görselleştiricisi ve Özel Görüntüleyici](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
