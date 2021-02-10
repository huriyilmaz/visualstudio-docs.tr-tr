---
title: IDebugBreakEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakEvent2
helpviewer_keywords:
- IDebugBreakEvent2 interface
ms.assetid: 57dfdbc2-4e68-4dbf-9579-006cd6fb1c62
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 61fb53c1fc83f06c200b50b5fcf55f950a00ead6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99943440"
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
