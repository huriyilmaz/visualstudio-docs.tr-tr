---
title: IDebugProgramCreateEvent2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramCreateEvent2
helpviewer_keywords:
- IDebugProgramCreateEvent2 interface
ms.assetid: b19a7934-6179-4a68-9075-bd7dcd640b05
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 78088d6e5da61c32302c13b08143c9ed902452e2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722635"
---
# <a name="idebugprogramcreateevent2"></a>IDebugProgramCreateEvent2
Bu arabirim, hata ayıklama altyapısı (DE) tarafından bir program eklendiğinde oturum hata ayıklama yöneticisine (SDM) gönderilir.

## <a name="syntax"></a>Sözdizimi

```
IDebugProgramCreateEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 DE veya özel bağlantı noktası tedarikçisi, genellikle programın bağlı olduğu anda bir programın oluşturulduğunu bildirmek için bu arabirimi uygular. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) arabirimi bu arabirimle aynı nesne üzerinde uygulanmalıdır. SDM `QueryInterface` `IDebugEvent2` arabirime erişmek için yöntemi kullanır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 DE veya özel bağlantı noktası tedarikçisi oluşturur ve bir program oluşturulmasını bildirmek için bu olay nesnesi gönderir. DE bu olayı, sdm tarafından verilen [iDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) geri arama işlevini kullanarak gönderir. Özel bağlantı noktası tedarikçisi bu olayı [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) arabirimini kullanarak gönderir.

## <a name="remarks"></a>Açıklamalar
 DE veya özel bağlantı noktası tedarikçisi [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)çağırarak yeni bir [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) arabirimi yayımlar.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
