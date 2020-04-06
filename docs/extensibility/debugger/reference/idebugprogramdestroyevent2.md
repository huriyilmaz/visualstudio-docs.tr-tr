---
title: IDebugProgramDestroyEvent2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramDestroyEvent2
helpviewer_keywords:
- IDebugProgramDestroyEvent2
ms.assetid: ddf127ca-c4a5-4071-90ca-68faf2f57dbd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dc83e15372a15cefccc47ea60db5ba451546ecba
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722597"
---
# <a name="idebugprogramdestroyevent2"></a>IDebugProgramDestroyEvent2
Bu arabirim, hata ayıklama altyapısı (DE) tarafından, bir program tamamlandığında oturum hata ayıklama yöneticisine (SDM) gönderilir.

## <a name="syntax"></a>Sözdizimi

```
IDebugProgramDestroyEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 DE veya özel bağlantı noktası tedarikçisi, bir programın sonlandırıldığını ve artık hata ayıklama için kullanılamayacağını bildirmek için bu arabirimi uygular. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) arabirimi bu arabirimle aynı nesne üzerinde uygulanmalıdır. SDM `IDebugEvent2` [arabirime](/cpp/atl/queryinterface) erişmek için QueryInterface kullanır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 DE veya özel bağlantı noktası tedarikçisi, bir programın sonlandırılmasını bildirmek için bu olay nesnesini oluşturur ve gönderir. DE bu olayı, sdm tarafından verilen [iDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) geri arama işlevini kullanarak gönderir. Özel bağlantı noktası tedarikçisi bu olayı [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) arabirimini kullanarak gönderir.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 Aşağıdaki tabloda `IDebugProgramDestroyEvent2`. yöntemini gösterir.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetExitCode](../../../extensibility/debugger/reference/idebugprogramdestroyevent2-getexitcode.md)|Programın çıkış kodunu alır.|

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
