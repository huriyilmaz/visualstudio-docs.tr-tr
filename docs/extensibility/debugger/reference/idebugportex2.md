---
title: IDebugPortEx2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEx2
helpviewer_keywords:
- IDebugPortEx2 interface
ms.assetid: 144724d0-38ee-4c9b-87ca-8a504371182b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5789681b0da70f46dadac1e29d0d6bb9dc905d1a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724991"
---
# <a name="idebugportex2"></a>IDebugPortEx2
Bu arabirim, oturum hata ayıklama yöneticisinin (SDM) bir bağlantı noktasında çalışan programları ve işlemleri denetlemesini sağlar.

## <a name="syntax"></a>Sözdizimi

```
IDebugPortEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Özel bir bağlantı noktası tedarikçisi bu arabirimi [IDebugPort2'yi](../../../extensibility/debugger/reference/idebugport2.md)uygulayan nesne üzerinde uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 SDM bu arabirimi `IDebugPort2` elde etmek için arabirimde [QueryInterface](/cpp/atl/queryinterface) çağırır.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 Aşağıdaki tabloda `IDebugPortEx2`.

|Yöntem|Açıklama|
|------------|-----------------|
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)|Çalıştırılabilir bir dosya başlatıyor.|
|[ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)|Bir işlemin yürütülmesini devam ettirer.|
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugportex2-canterminateprocess.md)|Bir işlemin sonlandırılıp sonlandırılamayacağını belirler.|
|[TerminateProcess](../../../extensibility/debugger/reference/idebugportex2-terminateprocess.md)|Bir işlemi sonlandırır.|
|[GetPortProcessId](../../../extensibility/debugger/reference/idebugportex2-getportprocessid.md)|Bağlantı noktasının işlem kimliğini alır.|
|[GetProgram](../../../extensibility/debugger/reference/idebugportex2-getprogram.md)|Program düğümüyle ilişkili bir program alır.|

## <a name="remarks"></a>Açıklamalar
 Bu arabirim normalde SDM ve özel bağlantı noktası tedarikçisi arasında özeldir.

 İstenirse, hata ayıklama motoru (DE) LaunchSuspended'e geçen [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) arabiriminde bu arabirimi bulabilir ve programı başlatmak için [LaunchSuspended'ı](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) kullanabilir. [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md) Bu bir gereklilik değildir, ancak, ve bir DE istek programı başlatmak için ne gerekiyorsa yapabilirsiniz.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: portpriv.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
