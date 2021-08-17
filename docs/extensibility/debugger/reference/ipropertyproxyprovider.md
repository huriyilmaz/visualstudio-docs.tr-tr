---
description: Bu arabirim, bir nesnenin verilerini görüntülemek ve değiştirmek için bir ara sunucu arabirimi sağlar.
title: IPropertyProxyProvider | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyProvider
helpviewer_keywords:
- IPropertyProxyProvider interface
ms.assetid: 52e9f7fc-6fe0-4d23-890b-5673dca8c3cb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 838bffb792d709dc237aae279f3af754d4e7873d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122029222"
---
# <a name="ipropertyproxyprovider"></a>IPropertyProxyProvider
Bu arabirim, bir nesnenin verilerini görüntülemek ve değiştirmek için bir ara sunucu arabirimi sağlar.

## <a name="syntax"></a>Syntax

```
IPropertyProxyProvider : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 İfade değerlendiricisi (EE), bu arabirimi, EE'nin tür görselleştiricileri desteğinin bir parçası olarak [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) arabirimini uygulayan aynı nesne üzerinde uygulamaya almaktadır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu arabirimi almak için bir arabirimde [QueryInterface](/cpp/atl/queryinterface) `IDebugProperty3` çağrısı yapmak.

## <a name="methods-in-vtable-order"></a>Vtable sırasına göre yöntemler
 Arabirimi `IPropertyProxyProvider` aşağıdaki yöntemi kullanır:

|Yöntem|Açıklama|
|------------|-----------------|
|[GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md)|Bir nesnede verileri görüntülemek için bir özellik ara sunucusu arabirimini alın.|

## <a name="remarks"></a>Açıklamalar
 Uygulama EE arabirimini uygulaysa [da, GetPropertyProxy'nin](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) uygulaması genellikle [GetPropertyProxy tarafından işleniyor.](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md) IEEVisualizerService arabirimini alma hakkında ayrıntılı bilgi için bkz. Verileri Görselleştirme ve Görüntüleme. [](../../../extensibility/debugger/visualizing-and-viewing-data.md)

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)
- [Tür Görselleştiricisi ve Özel Görüntüleyici](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
- [Verileri Görselleştirme ve Görüntüleme](../../../extensibility/debugger/visualizing-and-viewing-data.md)
