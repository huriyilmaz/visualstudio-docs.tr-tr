---
title: IDebugProcess2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2
helpviewer_keywords:
- IDebugProcess2 interface
ms.assetid: 99f6cd06-4076-45ee-b2ae-fa2ad627fd18
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c72659491ec6718397a4fbb494175eea0896c7f7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723805"
---
# <a name="idebugprocess2"></a>IDebugProcess2
Bu arabirim, bağlantı noktasında çalışan bir işlemi temsil eder. Bağlantı noktası yerel bağlantı noktasıysa, `IDebugProcess2` genellikle yerel makinedeki fiziksel bir işlemi temsil eder.

## <a name="syntax"></a>Sözdizimi

```
IDebugProcess2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Bu arabirim, programları grup olarak yönetmek için özel bir bağlantı noktası tedarikçisi tarafından uygulanır. Bu arabirim bağlantı noktası tedarikçisi tarafından uygulanmalıdır.

 Bir hata ayıklama motoru da [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)üzerinden bir program başlatılmasını desteklereğer bu arayüzü uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu arabirim, bu işlemde tanımlanan bir program grubuyla etkileşim kurmak için öncelikle oturum hata ayıklama yöneticisi (SDM) tarafından çağrılır.

 Bu arabirimi almak için [GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md) veya [GetProcess'i](../../../extensibility/debugger/reference/idebugport2-getprocess.md) arayın. Bu arabirim de `IDebugEngineLaunch2::LaunchSuspended`arayarak döndürülür.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 Aşağıdaki tabloda `IDebugProcess2`.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)|Sürecin bir açıklamasını alır.|
|[EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)|Bu işlemde yer alan programları doğrular.|
|[GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)|İşlemin başlığını, dostu adını veya dosya adını alır.|
|[GetServer](../../../extensibility/debugger/reference/idebugprocess2-getserver.md)|Bu işlemin üzerinde çalışan bir makine sunucusu örneğini alır.|
|[Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)|İşlemi sonlandırır.|
|[İliştir](../../../extensibility/debugger/reference/idebugprocess2-attach.md)|İşleme bağlanır.|
|[CanDetach](../../../extensibility/debugger/reference/idebugprocess2-candetach.md)|SDM'nin işlemi ayırıp ayıramayacağına karar verebiliyor.|
|[Ayır](../../../extensibility/debugger/reference/idebugprocess2-detach.md)|Hata ayıklama işleminden ayrılır.|
|[GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)|Sistem işlem tanımlayıcısını alır.|
|[GetProcessid](../../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)|Bu işlem için benzersiz bir tanımlayıcı alır.|
|[GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)<br /><br /> [DEPRECATED]|İşlemhatasını yapan oturumun adını alır.<br /><br /> [AMORTISMANA UĞRADı. HER ZAMAN `E_NOTIMPL`DÖNMELIDIR .]|
|[EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)|İşlemde çalışan iş parçacıklarını oyalar.|
|[CauseBreak](../../../extensibility/debugger/reference/idebugprocess2-causebreak.md)|Bu işlemde kod çalıştıran sonraki programın durmasını ister.|
|[GetPort](../../../extensibility/debugger/reference/idebugprocess2-getport.md)|Bu işlemin devam ettiği bağlantı noktasını alır.|

## <a name="remarks"></a>Açıklamalar
 Bir `IDebugProcess2` veya daha fazla [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) arabirimi içerir.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: Msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

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
