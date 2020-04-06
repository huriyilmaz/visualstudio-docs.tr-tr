---
title: IPropertyProxySağlayıcı | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyProvider
helpviewer_keywords:
- IPropertyProxyProvider interface
ms.assetid: 52e9f7fc-6fe0-4d23-890b-5673dca8c3cb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f71d993c7f99cade5b866e67298132a325986e3a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714790"
---
# <a name="ipropertyproxyprovider"></a>IPropertyProxyProvider
Bu arabirim, bir nesnenin verilerini görüntülemek ve değiştirmek için bir proxy arabirimi sağlar.

## <a name="syntax"></a>Sözdizimi

```
IPropertyProxyProvider : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 İfade değerlendiricisi (EE), bu arabirimi, EE'nin tür görselleştiricileri desteğinin bir parçası olarak [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) arabirimini uygulayan nesne üzerinde uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu arabirimi `IDebugProperty3` elde etmek için [queryinterface'i](/cpp/atl/queryinterface) bir arabirimden arayın.

## <a name="methods-in-vtable-order"></a>Vtable sırasına göre yöntemler
 Arabirim `IPropertyProxyProvider` aşağıdaki yöntemi uygular:

|Yöntem|Açıklama|
|------------|-----------------|
|[GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md)|Bir nesnedeki verileri görüntülemek için bir özellik proxy arabirimi alır.|

## <a name="remarks"></a>Açıklamalar
 EE bu arabirimi uygulasa da, [GetPropertyProxy'nin](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) uygulanması genellikle [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)tarafından işlenir. IEEVisualizerService arabirimini edinme yle ilgili ayrıntılar için [Görselleştirme ve Görüntüleme Verileri'ne](../../../extensibility/debugger/visualizing-and-viewing-data.md) bakın.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)
- [Tür Görselleştiricisi ve Özel Görüntüleyici](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
- [Verileri Görselleştirme ve Görüntüleme](../../../extensibility/debugger/visualizing-and-viewing-data.md)
