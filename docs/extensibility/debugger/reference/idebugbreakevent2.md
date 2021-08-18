---
description: Bu arabirim, oturum hata ayıklama Yöneticisi 'ne (SDM) zaman uyumsuz bir kesmenin başarıyla tamamlandığını söyler.
title: IDebugBreakEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakEvent2
helpviewer_keywords:
- IDebugBreakEvent2 interface
ms.assetid: 57dfdbc2-4e68-4dbf-9579-006cd6fb1c62
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: b07b7203f8ce3d557b0bbb2d4c1ca410e481aec67555da5f21f0563702e71656
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121293046"
---
# <a name="idebugbreakevent2"></a>IDebugBreakEvent2
Bu arabirim, oturum hata ayıklama Yöneticisi 'ne (SDM) zaman uyumsuz bir kesmenin başarıyla tamamlandığını söyler.

## <a name="syntax"></a>Syntax

```
IDebugBreakEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Bu arabirimi, bir programdaki Kullanıcı sonlarını desteklemek için DE uygular. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) arabirimi bu arabirimle aynı nesne üzerinde UYGULANMALıDıR (SDM, arabirime erişmek için [QueryInterface](/cpp/atl/queryinterface) kullanır `IDebugEvent2` ).

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Kullanıcı hata ayıklamakta olan programın duraklatılmasını istediği zaman SDM, [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) çağırır. Program başarıyla duraklatıldığında `IDebugBreakEvent2` olayı gönderir. Bu olay, hata ayıklamakta olan programa eklendiğinde SDM tarafından sağlanan [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) callback işlevi kullanılarak gönderilir.

## <a name="remarks"></a>Açıklamalar
 Örneğin, bir Kullanıcı, sonsuz bir döngü çalıştıran bir programdan ayırmak için **hata ayıklama** menüsündeki **Tümünü kes** komutunu seçebilir. SDM, programa [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)çağırarak durmasını söyler. , `IDebugBreakEvent2` Program finally DURDURULDUĞUNDA de gönderir.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
