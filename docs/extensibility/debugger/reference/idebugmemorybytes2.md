---
description: Bu arabirim, bellek baytlarını temsil eder.
title: IDebugMemoryBytes2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryBytes2
helpviewer_keywords:
- IDebugMemoryBytes2 interface
ms.assetid: d7647575-0e06-4190-88f5-ca40b82209a4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: add2f353b432d5a7a935a7206ece2113382182ca06aa0755c084fe8123fd7298
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121417099"
---
# <a name="idebugmemorybytes2"></a>IDebugMemoryBytes2
Bu arabirim, bellek baytlarını temsil eder.

## <a name="syntax"></a>Syntax

```
IDebugMemoryBytes2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Hata ayıklama altyapısı (DE), bellekte baytları temsil etmek için bu arabirimi kullanır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
- [GetMemoryBytes,](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md) sistem belleğine erişim sağlamak için bu arabirimi döndürür. [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md) ve [GetMemoryBytes,](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md) bir nesnenin baytlarına erişim sağlamak için bu arabirimi geri döner.

## <a name="methods-in-vtable-order"></a>Vtable Sırasına Göre Yöntemler
 Aşağıdaki tabloda yöntemlerini `IDebugMemoryBytes2` gösterir.

|Yöntem|Açıklama|
|------------|-----------------|
|[ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)|Verilen bir konumdan başlayarak bayt dizisini okur.|
|[WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)|ile `dwCount` başlayan baytları `pStartContext` yazar.|
|[GetSize](../../../extensibility/debugger/reference/idebugmemorybytes2-getsize.md)|Bu arabirim tarafından temsil edilen belleğin boyutunu bayt cinsinden alır.|

## <a name="remarks"></a>Açıklamalar
 Özellikler için, bir [diziyi temsil eden bir IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) arabirimi, bu dizide `IDebugMemoryBytes2` bulunan değerlere erişmek için bir arabirim sağlar.

 Visual Studio'nin **Bellek Görünümü,** sistem belleğine erişmek için bir arabirim almak için [GetMemoryBytes'i](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md) `IDebugMemoryBytes2` çağırıyor. Erişilen adres, bir adres olarak girilen ifade Bellek Görünümü'ne ayrıştırılır ve sonra bir arabirim almak için [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) kullanılarak `IDebugProperty2` ayrıştırılır. [GetMemoryContext çağrısı,](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) bellek adresini açıklayan [IDebugMemoryContext2'i](../../../extensibility/debugger/reference/idebugmemorycontext2.md) döndürür. Bu bellek bağlamı daha sonra ReadAt ve [WriteAt'a geçirildi.](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md) [](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)
- [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)
- [GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
