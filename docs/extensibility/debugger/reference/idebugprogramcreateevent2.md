---
description: Bu arabirim, bir program ekli olduğunda hata ayıklama altyapısı (DE) tarafından oturum hata ayıklama yöneticisine (SDM) gönderilir.
title: IDebugProgramCreateEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramCreateEvent2
helpviewer_keywords:
- IDebugProgramCreateEvent2 interface
ms.assetid: b19a7934-6179-4a68-9075-bd7dcd640b05
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 9f6d4db4ed0b2a732fc216938c616cd64963d94cb2d4878e731fae1e89c8bb84
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121338819"
---
# <a name="idebugprogramcreateevent2"></a>IDebugProgramCreateEvent2
Bu arabirim, bir program ekli olduğunda hata ayıklama altyapısı (DE) tarafından oturum hata ayıklama yöneticisine (SDM) gönderilir.

## <a name="syntax"></a>Syntax

```
IDebugProgramCreateEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 DE veya özel bağlantı noktası sağlayıcı, genellikle programın ekli olduğu sırada bir programın oluşturuldığını rapor etmek için bu arabirimi uygulamaya almaktadır. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) arabirimi, bu arabirimle aynı nesne üzerinde uygulanarak uygulanarak. SDM, `QueryInterface` arabirimine erişmek için yöntemini `IDebugEvent2` kullanır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 DE veya özel bağlantı noktası sağlayıcı bu olay nesnesini oluşturur ve bir programın oluşturulmasını rapor etmek üzere gönderir. DE, hata ayıklaması yapılan programa ekli olduğunda SDM tarafından sağlanan [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) geri çağırma işlevini kullanarak bu olayı gönderir. Özel bağlantı noktası sağlayıcı bu olayı [IDebugPortEvents2 arabirimini kullanarak](../../../extensibility/debugger/reference/idebugportevents2.md) gönderir.

## <a name="remarks"></a>Açıklamalar
 DE veya özel bağlantı noktası sağlayıcı [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)çağırarak yeni [bir IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) arabirimi yayımlar.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
