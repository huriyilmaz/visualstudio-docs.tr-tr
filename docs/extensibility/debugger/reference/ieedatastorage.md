---
title: IEEDataStorage | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEDataStorage
helpviewer_keywords:
- IEEDataStorage interface
ms.assetid: 704e932d-2325-410e-89c4-ce88c6ec19da
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ad7da71d31e1093d87d68bb39958a71a117f5d5f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718179"
---
# <a name="ieedatastorage"></a>IEEDataStorage
Bu arabirim bir bayt dizisini temsil eder.

## <a name="syntax"></a>Sözdizimi

```
IEEDataStorage : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 İfade değerlendiricisi (EE), bu arabirimi bir dizi baytı [(IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) arabirimi üzerinden veri almak ve değiştirmek için tür görüntüleyiciler tarafından kullanılır) temsil etmek için uygular. EE genellikle dış tür görüntüleyiciler desteklemek için bu arabirimi uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Arabirimdeki `IPropertyProxyEESide` yöntemlerin tümü bu arabirimi döndürer. [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) arabirimini almak için [GetPropertyProxy'yi](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) arayın. [IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md) arabirimini elde etmek için [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) arabiriminde [QueryInterface'i](/cpp/atl/queryinterface) arayın.

## <a name="methods-in-vtable-order"></a>Vtable sırasına göre yöntemler
 Arabirim `IEEDataStorage` aşağıdaki yöntemleri uygular:

|Yöntem|Açıklama|
|------------|-----------------|
|[GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md)|Verilen arabelleğe belirtilen veri bayt sayısını alır.|
|[GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)|Kullanılabilir veri baytlarının sayısını alır.|

## <a name="remarks"></a>Açıklamalar
 Bu arabirim, belirli bir nesne tarafından tutulan verilere erişmek için bir tür görselleştiricisi tarafından kullanılır. Veriler, tür görselleştiricisinin kullanıcıya sunmak için gereken her şekilde işlemesine olanak tanıyan bir bayt dizisi olarak kabul edilir.

 Özel bir görüntüleyici, istenirse bu arabirimi de kullanabilir, ancak daha tipik olarak, özel bir görüntüleyici özel bir arabirim, [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md) veya [GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md) (dize yönelimli veriler için) kullanır.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [Tür Görselleştiricisi ve Özel Görüntüleyici](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
