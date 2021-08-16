---
description: Bu arabirim, ilişkili nesnede verileri görüntülemek için yöntemler sağlar.
title: IPropertyProxyEESide | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide
helpviewer_keywords:
- IPropertyProxyEESide interface
ms.assetid: cf227cf8-39d9-4758-8f7e-a697aebb1926
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 0ada25cdf053bdc7176491afab83b4226f4cf40f3eecbe614fa90d2478676286
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121377281"
---
# <a name="ipropertyproxyeeside"></a>IPropertyProxyEESide
Bu arabirim, ilişkili nesnede verileri görüntülemek için yöntemler sağlar. Bu arabirim, tür görselleştirici desteğinin bir parçası.

## <a name="syntax"></a>Syntax

```
IPropertyProxyEESide : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 İfade değerlendiricisi, tür görselleştiricileri desteklemek için bu arabirimi uygulamaya almaktadır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu [arabirimi almak için GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) çağrısı. [IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md) arabirimini almak için [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) arabiriminde [QueryInterface](/cpp/atl/queryinterface) çağrısı.

## <a name="methods-in-vtable-order"></a>Vtable sırasına göre yöntemler
 Aşağıdaki yöntemler bu arabirim tarafından uygulanır:

|Yöntem|Açıklama|
|------------|-----------------|
|[InitSourceDataProvider](../../../extensibility/debugger/reference/ipropertyproxyeeside-initsourcedataprovider.md)|Nesnenin verilerine erişilebilmek için bir veri kaynağı sağlayıcısını başlatılır.|
|[GetManagedViewerCreationData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getmanagedviewercreationdata.md)|Nesnenin derlemesi hakkında bilgi alınır.|
|[GetInitialData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getinitialdata.md)|Nesnesi için ilk verileri alır.|
|[CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)|Mevcut veri depolamanın bir kopyasını oluşturur.|
|[InPlaceUpdateObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject.md)|Mevcut bir veri depolama alanına başvuru oluşturur.|
|[ResolveAssemblyRef](../../../extensibility/debugger/reference/ipropertyproxyeeside-resolveassemblyref.md)|Bu nesneyi içeren derleme bağlamında belirli bir derleme hakkında bilgi alınır.|

## <a name="remarks"></a>Açıklamalar
 Tür görselleştiricisi, bu arabirimin parçası olduğu nesneyle ilişkili değerlere erişmek için bu arabirimi kullanır. Verilere, verilerin salt [okunur bir görünümünü sağlayan IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) arabirimi aracılığıyla erişilir.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [Tür Görselleştiricisi ve Özel Görüntüleyici](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
