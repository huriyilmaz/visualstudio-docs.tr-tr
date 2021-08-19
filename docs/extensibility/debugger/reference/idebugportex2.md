---
description: Bu arabirim, oturum hata ayıklama yöneticisinin (SDM) bir bağlantı noktası üzerinde çalışan programları ve işlemleri denetlemesi sağlar.
title: IDebugPortEx2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEx2
helpviewer_keywords:
- IDebugPortEx2 interface
ms.assetid: 144724d0-38ee-4c9b-87ca-8a504371182b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 41c5eff48a164107c9c87582bc2de1d532f7236e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122057713"
---
# <a name="idebugportex2"></a>IDebugPortEx2
Bu arabirim, oturum hata ayıklama yöneticisinin (SDM) bir bağlantı noktası üzerinde çalışan programları ve işlemleri denetlemesi sağlar.

## <a name="syntax"></a>Syntax

```
IDebugPortEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Özel bir bağlantı noktası sağlayıcı, bu arabirimi [IDebugPort2 uygulayan nesnede de uygulamaya almaktadır.](../../../extensibility/debugger/reference/idebugport2.md)

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 SDM, bu arabirimi almak için arabiriminde [QueryInterface'i](/cpp/atl/queryinterface) `IDebugPort2` arar.

## <a name="methods-in-vtable-order"></a>Vtable Sırasına Göre Yöntemler
 Aşağıdaki tabloda yöntemlerini `IDebugPortEx2` gösterir.

|Yöntem|Açıklama|
|------------|-----------------|
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)|Yürütülebilir bir dosya başlatıyor.|
|[ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)|Bir işlemi yürütmeyi sürdürür.|
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugportex2-canterminateprocess.md)|Bir işlemi sonlandırıp sonlandırılamaylarını belirler.|
|[TerminateProcess](../../../extensibility/debugger/reference/idebugportex2-terminateprocess.md)|Bir işlemi sonlandırılır.|
|[GetPortProcessId](../../../extensibility/debugger/reference/idebugportex2-getportprocessid.md)|Bağlantı noktasının işlem kimliğini alır.|
|[GetProgram](../../../extensibility/debugger/reference/idebugportex2-getprogram.md)|Bir program düğümüyle ilişkili bir programı alır.|

## <a name="remarks"></a>Açıklamalar
 Bu arabirim normalde SDM ile özel bağlantı noktası sağlayıcı arasında özeldir.

 İsterseniz, bir hata ayıklama altyapısı (DE), [LaunchSuspended'e](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) geçirilen [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) arabiriminde bu arabirimi arayabiliyor ve programı başlatmak için [LaunchSuspended'i](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md) kullanabilir. Ancak bu bir gereksinim değildir ve DE, istek programını başlatmak için gereken her şeyi yapar.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: portpriv.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
