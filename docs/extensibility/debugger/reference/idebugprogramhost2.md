---
title: IDebugProgramHost2 | Microsoft Dokümanlar
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722215"
---
# <a name="idebugprogramhost2"></a>IDebugProgramHost2
Bu arabirim, bir program hakkında ana bilgisayar (işlem) bilgileri sağlar.

## <a name="syntax"></a>Sözdizimi

```
IDebugProgramHost2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Hata ayıklama altyapısı, barındırma işlemi hakkında bilgi sağlamak için bu arabirimi [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) arabirimiyle aynı nesne üzerinde uygular. Bu isteğe bağlı bir arayüzdür.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu arabirimi `IDebugProgram2` elde etmek için [queryinterface'i](/cpp/atl/queryinterface) bir arabirimden arayın.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 Aşağıdaki tabloda `IDebugProgramHost2`.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetHostName](../../../extensibility/debugger/reference/idebugprogramhost2-gethostname.md)|Bu programın barındırma işleminin başlığını, dostu adını veya dosya adını alır.|
|[GetHostId](../../../extensibility/debugger/reference/idebugprogramhost2-gethostid.md)|Bu programın barındırma işleminin işlem tanımlayıcısını alır.|
|[GetHostMachineName](../../../extensibility/debugger/reference/idebugprogramhost2-gethostmachinename.md)|Bu programın barındırma işlemi üzerinde çalışıyor makinenin adını alır.|

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
