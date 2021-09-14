---
description: Bu arabirim, hata ayıklama olaylarını oturum hata ayıklama yöneticisine (SDM) göndermek için hata ayıklama altyapısı (DE) tarafından kullanılır.
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
ms.openlocfilehash: a4d75583b2c936b82e167618356a9ae0547f337e
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725227"
---
# <a name="idebugeventcallback2"></a>IDebugEventCallback2
Bu arabirim, hata ayıklama olaylarını oturum hata ayıklama yöneticisine (SDM) göndermek için hata ayıklama altyapısı (DE) tarafından kullanılır.

## <a name="syntax"></a>Syntax

```
IDebugEventCallback2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] , bir hata ayıklama altyapısından olayları almak için bu arabirimini uygulamaya alır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Hata ayıklama altyapısı genellikle SDM [Attach,](../../../extensibility/debugger/reference/idebugprogram2-attach.md) [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)veya [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)çağrısında olduğunda bu arabirimi alır. Bir hata ayıklama altyapısı, Olay çağırarak olayları SDM'ye [gönderir.](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)

## <a name="methods-in-vtable-order"></a>VTable Sırasına Göre Yöntemler
 Aşağıdaki tabloda yöntemlerini `IDebugEventCallback2` gösterir.

|Yöntem|Açıklama|
|------------|-----------------|
|[Olay](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)|SDM'ye hata ayıklama olayları bildirimi gönderir.|

## <a name="remarks"></a>Açıklamalar
 [EvaluateSync ve](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) bir arabirim alacaklarını belirtse de, bu durum geçerli değildir ve arabirim işaretçisi `IDebugEventCallback2` her zaman null değer olur. Bunun yerine, hata ayıklama altyapısı Attach , Attach , veya `IDebugEventCallback2` [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) [](../../../extensibility/debugger/reference/idebugprogram2-attach.md)çağrısında alınan arabirimi kullan gerekir. [](../../../extensibility/debugger/reference/idebugengine2-attach.md)

 Bir paket yönetilen kodda [IDebugEventCallback](../../../extensibility/debugger/reference/idebugeventcallback2.md) uygulayıyorsa, Event'e geçirilen çeşitli arabirimlerde <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> çağrılmasına önemle tavsiye [edilir.](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [İliştir](../../../extensibility/debugger/reference/idebugprogram2-attach.md)
- [İliştir](../../../extensibility/debugger/reference/idebugengine2-attach.md)
