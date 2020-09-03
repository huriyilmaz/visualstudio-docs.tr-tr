---
title: IEEDataStorage | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80718179"
---
# <a name="ieedatastorage"></a>IEEDataStorage
Bu arabirim bir bayt dizisini temsil eder.

## <a name="syntax"></a>Syntax

```
IEEDataStorage : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 İfade değerlendirici (EE), bu arabirimi bir bayt dizisini temsil etmek için uygular (verileri [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) arabirimi aracılığıyla almak ve değiştirmek için tür Görselleştiriciler tarafından kullanılır). EE genellikle bu arabirimi, dış tür görselleştiricilerini desteklemek için uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 `IPropertyProxyEESide`Arabirimindeki Yöntemler bu arabirimi döndürür. [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) arabirimini almak Için [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) çağrısı yapın. [IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md) arabirimini almak Için bir [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) arabiriminde [QueryInterface](/cpp/atl/queryinterface) 'i çağırın.

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 `IEEDataStorage`Arabirimi aşağıdaki yöntemleri uygular:

|Yöntem|Açıklama|
|------------|-----------------|
|[GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md)|Belirtilen arabellek için belirtilen sayıda veri baytı alır.|
|[GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)|Kullanılabilir veri baytlarının sayısını alır.|

## <a name="remarks"></a>Açıklamalar
 Bu arabirim, belirli bir nesne tarafından tutulan verilere erişmek için bir tür görselleştiricisi tarafından kullanılır. Veriler bir bayt dizisi olarak değerlendirilir ve bu, tür görselleştiricinin onu kullanıcıya sunmak için gereken herhangi bir şekilde işlemesini sağlar.

 Özel bir görüntüleyici, istenirse bu arabirimi de kullanabilir, ancak genellikle özel bir Görüntüleyici özel bir arabirim, [Getmemorybytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md) veya [GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md) (dize yönelimli veriler için) kullanır.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [Tür Görselleştiricisi ve Özel Görüntüleyici](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
