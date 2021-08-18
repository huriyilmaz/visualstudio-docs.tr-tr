---
description: Bu arabirim bir bayt dizisini temsil eder.
title: IEEDataStorage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEDataStorage
helpviewer_keywords:
- IEEDataStorage interface
ms.assetid: 704e932d-2325-410e-89c4-ce88c6ec19da
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 1f8597a62f319247ca607d4b1f5221665f3de186
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122152997"
---
# <a name="ieedatastorage"></a>IEEDataStorage
Bu arabirim bir bayt dizisini temsil eder.

## <a name="syntax"></a>Syntax

```
IEEDataStorage : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 İfade değerlendirici (EE), bir bayt dizisini temsil etmek için bu arabirimi (tür görselleştiriciler tarafından [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) arabirimi aracılığıyla verileri almak ve değiştirmek için kullanılır) uygulamaya alır. Bu EE genellikle dış tür görselleştiricileri desteklemek için bu arabirimi uygulamaz.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Arabirimde yöntemlerin `IPropertyProxyEESide` hepsi bu arabirimi geri döner. [IPropertyProxyESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) arabirimini almak için [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) çağrısı. [IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md) arabirimini almak için [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) arabiriminde [QueryInterface](/cpp/atl/queryinterface) çağrısı.

## <a name="methods-in-vtable-order"></a>Vtable sırasına göre yöntemler
 Arabirimi `IEEDataStorage` aşağıdaki yöntemleri kullanır:

|Yöntem|Açıklama|
|------------|-----------------|
|[Veri Al](../../../extensibility/debugger/reference/ieedatastorage-getdata.md)|Sağlanan bir arabelleğe belirtilen sayıda veri baytı kaldırır.|
|[GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)|Kullanılabilir veri bayt sayısını alan.|

## <a name="remarks"></a>Açıklamalar
 Bu arabirim, belirli bir nesne tarafından düzenlenen verilere erişmek için tür görselleştiricisi tarafından kullanılır. Veriler bir bayt dizisi olarak kabul edilir ve tür görselleştiricinin bunu kullanıcıya sunmak için gereken her şekilde işlemesini sağlar.

 Özel görüntüleyici, istenirse bu arabirimi de kullanabilir, ancak genellikle özel görüntüleyici [getMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md) veya [GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md) (dize odaklı veriler için) özel bir arabirim kullanır.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [Tür Görselleştiricisi ve Özel Görüntüleyici](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
