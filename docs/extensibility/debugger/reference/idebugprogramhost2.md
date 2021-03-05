---
description: Bu arabirim bir programla ilgili konak (işlem) bilgilerini sağlar.
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
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 109cca0cc3d12d8bf14da848774042fe346f0f1e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102168120"
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
 [](/cpp/atl/queryinterface) `IDebugProgram2` Bu arabirimi edinmek Için arabirim üzerinde QueryInterface 'i çağırın.

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
