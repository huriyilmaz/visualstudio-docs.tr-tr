---
title: IPropertyProxyProvider | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80714790"
---
# <a name="ipropertyproxyprovider"></a>IPropertyProxyProvider
Bu arabirim, bir nesnenin verilerini görüntülemek ve değiştirmek için bir proxy arabirimi sağlar.

## <a name="syntax"></a>Syntax

```
IPropertyProxyProvider : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 İfade değerlendirici (EE), bu arabirimi, [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) arabirimini uygulayan aynı nesne üzerinde, görselin tür Görselleştiriciler desteğinin bir parçası olarak uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 [QueryInterface](/cpp/atl/queryinterface) `IDebugProperty3` Bu arabirimi edinmek Için arabirim üzerinde QueryInterface 'i çağırın.

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

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)
- [Tür Görselleştiricisi ve Özel Görüntüleyici](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
- [Verileri Görselleştirme ve Görüntüleme](../../../extensibility/debugger/visualizing-and-viewing-data.md)
