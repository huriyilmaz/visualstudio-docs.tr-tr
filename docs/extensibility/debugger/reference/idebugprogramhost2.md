---
title: IDebugProgramHost2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramHost2
helpviewer_keywords:
- IDebugProgramHost2 interface
ms.assetid: 2c37b3aa-97a9-4665-8709-edd917f18cb1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 64db456e0c438f8665f122c3cd1b079c2ad1cea1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80722215"
---
# <a name="idebugprogramhost2"></a>IDebugProgramHost2
Bu arabirim bir programla ilgili konak (işlem) bilgilerini sağlar.

## <a name="syntax"></a>Syntax

```
IDebugProgramHost2 : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Hata ayıklama altyapısı, barındırma işlemi hakkında bilgi sağlamak için bu arabirimi [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) arabirimiyle aynı nesne üzerinde uygular. Bu, isteğe bağlı bir arabirimdir.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 [QueryInterface](/cpp/atl/queryinterface) `IDebugProgram2` Bu arabirimi edinmek Için arabirim üzerinde QueryInterface 'i çağırın.

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDebugProgramHost2` .

|Yöntem|Açıklama|
|------------|-----------------|
|[GetHostName](../../../extensibility/debugger/reference/idebugprogramhost2-gethostname.md)|Bu programın barındırma sürecinin başlığını, kolay adını veya dosya adını alır.|
|[GetHostId](../../../extensibility/debugger/reference/idebugprogramhost2-gethostid.md)|Bu programın barındırma sürecinin işlem tanımlayıcısını alır.|
|[GetHostMachineName](../../../extensibility/debugger/reference/idebugprogramhost2-gethostmachinename.md)|Bu programın barındırma sürecinin üzerinde çalıştığı makinenin adını alır.|

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
