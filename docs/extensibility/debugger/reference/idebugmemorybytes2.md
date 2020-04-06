---
title: IDebugMemoryBytes2 | Microsoft Dokümanlar
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727509"
---
# <a name="idebugmemorybytes2"></a>IDebugMemoryBytes2
Bu arabirim bellek baytlarını temsil eder.

## <a name="syntax"></a>Sözdizimi

```
IDebugMemoryBytes2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Hata ayıklama altyapısı (DE) bellekteki baytları temsil etmek için bu arabirimi uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
- [GetMemoryBytes,](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md) sistem belleği erişimi sağlamak için bu arabirimi döndürür. [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md) ve [GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md) bir nesnenin bayterişim sağlamak için bu arabirimi döndürün.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 Aşağıdaki tabloda `IDebugMemoryBytes2`.

|Yöntem|Açıklama|
|------------|-----------------|
|[ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)|Belirli bir konumdan başlayarak bir bayt dizisini okur.|
|[WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)|'den `dwCount` `pStartContext`başlayarak bayt yazar.|
|[GetSize](../../../extensibility/debugger/reference/idebugmemorybytes2-getsize.md)|Bu arabirim tarafından temsil edilen belleğin boyutunu baytolarak alır.|

## <a name="remarks"></a>Açıklamalar
 Özellikler için, bir diziyi temsil eden bir `IDebugMemoryBytes2` [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) arabirimi, bu dizideki değerlere erişmek için bir arabirim sağlar.

 Visual Studio'nun **Memory View'ı** [GetMemoryBytes'ı](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md) sistem belleğine erişmek için bir `IDebugMemoryBytes2` arayüz almak için çağırır. Erişilecek adres, bellek görünümüne adres olarak girilen ifadeyi ayrıştırarak ve `IDebugProperty2` arabirim almak için [EvaluateSync'i](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) kullanarak ayrıştırılmış ifadeyi değerlendirerek elde edilir. [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) için yapılan bir çağrı, bellek adresini açıklayan [IDebugMemoryContext2'yi](../../../extensibility/debugger/reference/idebugmemorycontext2.md) döndürür. Bu bellek bağlamı daha sonra [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md) ve [WriteAt'a](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)aktarılır.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)
- [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)
- [GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
