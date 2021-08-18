---
description: Bu arabirim, bir bağlantı noktası üzerinde çalışan bir işlemi temsil eder.
title: IDebugProcess2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2
helpviewer_keywords:
- IDebugProcess2 interface
ms.assetid: 99f6cd06-4076-45ee-b2ae-fa2ad627fd18
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: dede0cad4da45ccb5df4fe528214f4e0e22d2cdc9d5fe472a41be544e248c1cf
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121416254"
---
# <a name="idebugprocess2"></a>IDebugProcess2
Bu arabirim, bir bağlantı noktası üzerinde çalışan bir işlemi temsil eder. Bağlantı noktası yerel bağlantı noktası ise, genellikle `IDebugProcess2` yerel makinede fiziksel bir işlemi temsil eder.

## <a name="syntax"></a>Syntax

```
IDebugProcess2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Bu arabirim, programları grup olarak yönetmek için özel bir bağlantı noktası sağlayıcı tarafından uygulanır. Bu arabirimin bağlantı noktası sağlayıcı tarafından uygulanması gerekir.

 Bir hata ayıklama altyapısı, [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)aracılığıyla bir program başlatmayı destekliyorsa bu arabirimi de uygulamaya almaktadır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu arabirim, bu işlemde tanımlanan bir program grubuyla etkileşim kurmak için öncelikle oturum hata ayıklama yöneticisi (SDM) tarafından çağrılır.

 Bu [arabirimi almak için GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md) veya [GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md) çağrısı. Bu arabirim çağrılarak da `IDebugEngineLaunch2::LaunchSuspended` döndürülür.

## <a name="methods-in-vtable-order"></a>Vtable Sırasına Göre Yöntemler
 Aşağıdaki tabloda yöntemlerini `IDebugProcess2` gösterir.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)|Sürecin açıklamasını alır.|
|[EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)|Bu işlemde yer alan programları numaralar.|
|[GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)|Sürecin başlığını, kolay adını veya dosya adını alır.|
|[GetServer](../../../extensibility/debugger/reference/idebugprocess2-getserver.md)|Bu işlem üzerinde çalışan bir makine sunucusunun örneğini alır.|
|[Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)|işlemi sonlandırılır.|
|[İliştir](../../../extensibility/debugger/reference/idebugprocess2-attach.md)|İşleme iliştirer.|
|[CanDetach](../../../extensibility/debugger/reference/idebugprocess2-candetach.md)|SDM'nin işlemi ayırabilir olup olmadığını belirler.|
|[Ayır](../../../extensibility/debugger/reference/idebugprocess2-detach.md)|Hata ayıklayıcıyı işlemden ayırır.|
|[GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)|Sistem işlem tanımlayıcısını alır.|
|[GetProcessId](../../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)|Bu işlem için genel olarak benzersiz bir tanımlayıcı alır.|
|[GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)<br /><br /> [KULLANıM DıŞı]|İşlemde hata ayıklayıcı olan oturumun adını alır.<br /><br /> [KULLANıM DıŞı. HER ZAMAN `E_NOTIMPL` .]|
|[EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)|İşlemde çalışan iş parçacıklarını numaralar.|
|[CauseBreak](../../../extensibility/debugger/reference/idebugprocess2-causebreak.md)|Bu işlemde kod çalıştıran bir sonraki programın durdurması isteğinde bulundu.|
|[GetPort](../../../extensibility/debugger/reference/idebugprocess2-getport.md)|Bu işlem üzerinde çalışan bağlantı noktasını alır.|

## <a name="remarks"></a>Açıklamalar
 , `IDebugProcess2` bir veya daha fazla [IDebugProgram2 arabirimi](../../../extensibility/debugger/reference/idebugprogram2.md) içerir.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: Msdbg.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md)
- [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)
- [Sonraki](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md)
- [Olay](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
- [Olay](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
