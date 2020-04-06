---
title: IDebugStepCompleteEvent2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStepCompleteEvent2
helpviewer_keywords:
- IDebugStepCompleteEvent2 interface
ms.assetid: eba2b76e-f90d-486b-ae5c-c47f1b8ba2e5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 289609c93cf0e58eb44500bff135282d01212bbc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719453"
---
# <a name="idebugstepcompleteevent2"></a>IDebugStepCompleteEvent2
Bu arabirim, hata ayıklama altyapısı (DE) tarafından, hata ayıklama yöneticisine (SDM) program bir adım, bir adım üzerinde veya kaynak kodu veya deyimi veya yönerge satırından bir adım atıldığında tamamlandığında gönderilir.

## <a name="syntax"></a>Sözdizimi

```
IDebugStepCompleteEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 DE, bir adım işleminin tamamını bildirmek için bu arabirimi uygular. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) arabirimi bu arabirimle aynı nesne üzerinde uygulanmalıdır. SDM `IDebugEvent2` [arabirime](/cpp/atl/queryinterface) erişmek için QueryInterface kullanır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 DE oluşturur ve bir adım işleminin tamamlanmasını bildirmek için bu olay nesnesi gönderir. Olay, debugged olan programa iliştirildiğinde SDM tarafından sağlanan [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) geri arama işlevi kullanılarak gönderilir.

## <a name="remarks"></a>Açıklamalar
 Adım tamamlandıktan sonra, debugged olan program bir kez daha duraklatıldı ve IDE tüm pencerelerini güncelleştirir.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
