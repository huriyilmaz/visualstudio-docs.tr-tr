---
description: Bu arabirim hata ayıklama altyapısı (DE) tarafından oturum hata ayıklama yöneticisini (SDM) göndermek için kullanılır.
title: IDebugEventCallback2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEventCallback2
helpviewer_keywords:
- IDebugEventCallback2
ms.assetid: 2c935ee0-2e22-4be0-a852-73736f33c8c9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: e769f4c960d49cb66f92a72f4a402c81c8f54b7f25f041251680138c84f4f07b
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121292643"
---
# <a name="idebugeventcallback2"></a>IDebugEventCallback2
Bu arabirim hata ayıklama altyapısı (DE) tarafından oturum hata ayıklama yöneticisini (SDM) göndermek için kullanılır.

## <a name="syntax"></a>Syntax

```
IDebugEventCallback2 : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] bir hata ayıklama altyapısından olay almak için bu arabirimi uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bir hata ayıklama altyapısı genellikle bu arabirimi, SDM [iliştirme](../../../extensibility/debugger/reference/idebugprogram2-attach.md), [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)veya [launchaskıya alındı](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)olarak çağırdığında alır. Hata ayıklama altyapısı, [olayı](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)çağırarak SDM 'ye olay gönderir.

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDebugEventCallback2` .

|Yöntem|Açıklama|
|------------|-----------------|
|[Olay](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)|Hata ayıklama olaylarının SDM 'ye bildirimini gönderir.|

## <a name="remarks"></a>Açıklamalar
 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) ve [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) bir arabirim alıp belirttikleri halde, `IDebugEventCallback2` Bu durum değildir ve arabirim işaretçisi her zaman bir null değer olacaktır. Bunun yerine, hata ayıklama altyapısının, `IDebugEventCallback2` [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md), [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)veya [launchaskıya alındı](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)çağrısında alınan arabirimini kullanması gerekir.

 Bir paket yönetilen kodda [ıınfo Geventcallback](../../../extensibility/debugger/reference/idebugeventcallback2.md) uygularsa, <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> [olaya](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)geçirilen çeşitli arabirimlerde çağrılması önemle tavsiye edilir.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [İliştir](../../../extensibility/debugger/reference/idebugprogram2-attach.md)
- [İliştir](../../../extensibility/debugger/reference/idebugengine2-attach.md)
