---
title: IDebugProperty3 | Microsoft Docs
description: Bu arabirim, özelliği ile ilişkili rastgele bir uzun dizenin alınması için destek sağlar, özellik için özel görüntüleyicilerin bir listesini alarak, özelliğin değerini ortaya çıkan hataları raporlayabilir şekilde ayarlayarak, özelliği ile ilişkili, benzersiz bir KIMLIĞI özelliği ile ilişkilendirirken
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3
helpviewer_keywords:
- IDebugProperty3 interface
ms.assetid: 8f9be68d-4490-4eca-8f6b-8a10ed77e226
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: a5659e96896687f39a77c67e15e14b3bba8cc607737bba42013ac1be034aa486
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121292253"
---
# <a name="idebugproperty3"></a>IDebugProperty3
Bu arabirim için destek sağlar:

- Özelliği ile ilişkili rastgele bir uzun dize alma.

- Benzersiz bir KIMLIĞI özelliği ile ilişkilendirme.

- Özelliği için özel görüntüleyicilerin bir listesi alınıyor.

- Bir özelliğin değerini, ortaya çıkan hataları bildirme özelliğiyle ayarlama

## <a name="syntax"></a>Syntax

```
IDebugProperty3 : IDebugProperty2
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Hata ayıklama altyapısı (DE), uzun dizeler, özellik kimlikleri ve özel görüntüleyiciler için destek sağlamak üzere [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) uygulayan aynı nesne üzerinde bu arabirimi uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 [](/cpp/atl/queryinterface) `IDebugProperty2` Bu arabirimi edinmek Için arabirim üzerinde QueryInterface 'i çağırın.

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 Kaynağından devralınan yöntemlere ek olarak `IDebugProperty2` , `IDebugProperty3` arabirimi aşağıdaki yöntemleri sunar.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetStringCharLength](../../../extensibility/debugger/reference/idebugproperty3-getstringcharlength.md)|Özelliği ile ilişkili dizenin uzunluğunu döndürür.|
|[GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md)|Kullanıcı tarafından sağlanan arabellekteki dizeyi döndürür.|
|[CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)|Bu özellik için benzersiz bir KIMLIK oluşturur.|
|[DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)|Bu özellik için benzersiz KIMLIĞI yok eder.|
|[GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)|Bu özelliğin görüntülenebilmesini sağlayan özel görüntüleyicilerin sayısını döndürür.|
|[GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)|Bu özelliğin görüntülenebilmesini sağlayan özel görüntüleyicilerin listesini döndürür.|
|[SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)|Bu özelliğin değerini ayarlar, bir sorun varsa hata iletisi döndürür.|

## <a name="remarks"></a>Açıklamalar
- [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md) , oturum hata ayıklama Yöneticisi 'nın (SDM) bir özelliğin değerini ayarlaması için tercih edilen yoldur.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)
