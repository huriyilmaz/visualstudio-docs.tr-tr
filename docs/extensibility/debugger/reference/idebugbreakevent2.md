---
title: IDebugBreakEvent2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakEvent2
helpviewer_keywords:
- IDebugBreakEvent2 interface
ms.assetid: 57dfdbc2-4e68-4dbf-9579-006cd6fb1c62
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1af6ce13de529fef5e16b3bc1be7053f0e1347b6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735396"
---
# <a name="idebugbreakevent2"></a>IDebugBreakEvent2
Bu arabirim, oturum hata ayıklama yöneticisine (SDM) bir eşzamanlı molanın başarıyla tamamlandığını bildirir.

## <a name="syntax"></a>Sözdizimi

```
IDebugBreakEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 DE, bir programdaki kullanıcı molalarını desteklemek için bu arabirimi uygular. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) arabirimi bu arabirimle aynı nesne üzerinde uygulanmalıdır (SDM `IDebugEvent2` [arabirime](/cpp/atl/queryinterface) erişmek için QueryInterface'i kullanır).

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 SDM, kullanıcı programın duraklatılmak üzere silinmesini istediğinde [CauseBreak'i](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) çağırır. Program başarıyla duraklatıldı, DE `IDebugBreakEvent2` olayı gönderir. Bu olay, sdm tarafından sağlanan [iDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) geri arama işlevi kullanılarak gönderilir.

## <a name="remarks"></a>Açıklamalar
 Örneğin, bir kullanıcı, sonsuz döngü çalıştıran bir programdan çıkmak için **Hata Ayıklama** menüsündeki **Tümünü Ara** komutunu seçebilir. SDM [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)arayarak durdurmak için program söyler. Program sonunda `IDebugBreakEvent2` durduğunda DE gönderir.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
