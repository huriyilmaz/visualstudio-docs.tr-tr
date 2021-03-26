---
description: Bu arabirim, oturum hata ayıklama Yöneticisi 'nin (SDM) bir bağlantı noktasında çalışan programları ve süreçlerini denetlemesine olanak tanır.
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
ms.workload:
- vssdk
ms.openlocfilehash: e26fec4b47a301bfb266f40b41fd88216ccf671f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105072435"
---
# <a name="idebugportex2"></a>IDebugPortEx2
Bu arabirim, oturum hata ayıklama Yöneticisi 'nin (SDM) bir bağlantı noktasında çalışan programları ve süreçlerini denetlemesine olanak tanır.

## <a name="syntax"></a>Syntax

```
IDebugPortEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Özel bir bağlantı noktası sağlayıcısı, bu arabirimi [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)uygulayan aynı nesne üzerinde uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 SDM, [](/cpp/atl/queryinterface) `IDebugPort2` Bu arabirimi edinmek için arabirimdeki QueryInterface 'i çağırır.

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDebugPortEx2` .

|Yöntem|Açıklama|
|------------|-----------------|
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)|Yürütülebilir bir dosya başlatır.|
|[ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)|Bir işlemin yürütülmesini sürdürür.|
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugportex2-canterminateprocess.md)|Bir işlemin sonlandırılıp sonlandırılamayacağını belirler.|
|[TerminateProcess](../../../extensibility/debugger/reference/idebugportex2-terminateprocess.md)|Bir işlemi sonlandırır.|
|[GetPortProcessId](../../../extensibility/debugger/reference/idebugportex2-getportprocessid.md)|Bağlantı noktasının işlem KIMLIĞINI alır.|
|[GetProgram](../../../extensibility/debugger/reference/idebugportex2-getprogram.md)|Program düğümüyle ilişkili bir programı alır.|

## <a name="remarks"></a>Açıklamalar
 Bu arabirim, birincil olarak SDM ve özel bağlantı noktası tedarikçisidir.

 İsterseniz, bir hata ayıklama altyapısı (DE), [Launchaskıya alındı](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) öğesine geçirilen [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) arabiriminde bu arabirime bakabilir ve programı başlatmak için [launchaskıya alındı](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md) ' ı kullanır. Ancak bu bir gereksinim değildir ve bir DE, istek programını başlatmak için yapması gereken her şeyi yapabilir.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: portprıv. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
