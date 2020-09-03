---
title: IDebugMemoryBytes2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryBytes2
helpviewer_keywords:
- IDebugMemoryBytes2 interface
ms.assetid: d7647575-0e06-4190-88f5-ca40b82209a4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 56cb234e2295c5c9c08c2a2e9271e1c173524875
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80727509"
---
# <a name="idebugmemorybytes2"></a>IDebugMemoryBytes2
Bu arabirim, bellek baytlarını temsil eder.

## <a name="syntax"></a>Syntax

```
IDebugMemoryBytes2 : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Hata ayıklama altyapısı (DE), bellekteki baytları temsil etmek için bu arabirimi uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
- [Getmemorybytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md) , sistem belleğine erişim sağlamak için bu arabirimi döndürür. [Getmemorybytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md) ve [getmemorybytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md) , bir nesnenin baytlarına erişim sağlamak için bu arabirimi döndürür.

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDebugMemoryBytes2` .

|Yöntem|Açıklama|
|------------|-----------------|
|[ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)|Belirli bir konumdan başlayarak bir bayt dizisini okur.|
|[WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)|`dwCount`Bayttan itibaren bayt Yazar `pStartContext` .|
|[GetSize](../../../extensibility/debugger/reference/idebugmemorybytes2-getsize.md)|Bu arabirim tarafından temsil edilen belleğin bayt cinsinden boyutunu alır.|

## <a name="remarks"></a>Açıklamalar
 Özellikler için bir diziyi temsil eden bir [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) arabirimi, `IDebugMemoryBytes2` Bu dizideki değerlere erişmek için bir arabirim sağlar.

 Visual Studio 'nun **bellek görünümü** , sistem belleğine erişim için bir arabirim almak üzere [getmemorybytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md) çağırır `IDebugMemoryBytes2` . Erişilecek adres, bellek görünümüne adres olarak girilen ifadeyi ayrıştırarak ve ardından bir arabirim almak için [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) kullanılarak ayrıştırılmış ifade değerlendirilirken elde edilir `IDebugProperty2` . [Getmemorycontext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) çağrısı, bellek adresini açıklayan [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) döndürür. Bu bellek bağlamı daha sonra [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md) ve [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)'a geçirilir.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)
- [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)
- [GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
