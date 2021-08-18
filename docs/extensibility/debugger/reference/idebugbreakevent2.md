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
ms.openlocfilehash: 1816d2a6c53c4a1840f6511676dafff7a3710394
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122119769"
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
