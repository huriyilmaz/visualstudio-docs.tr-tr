---
description: Bu arabirim, bir programda çalışan bir iş parçacığını temsil eder.
title: IDebugThread2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2
helpviewer_keywords:
- IDebugThread2 interface
ms.assetid: 221b4b1b-4a26-466e-bc29-5eff800fab13
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 02463f51fc05a6ad4a42dd663e0c0b949d7f0c8badba87d13e2afc459be763e6
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121291954"
---
# <a name="idebugthread2"></a>IDebugThread2
Bu arabirim, bir programda çalışan bir iş parçacığını temsil eder.

## <a name="syntax"></a>Syntax

```
IDebugThread2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Hata ayıklama altyapısı (DE), tek bir programda yürütme iş parçacığını temsil etmek için bu arabirimi uygulama.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Şu anda etkin olan iş parçacığını temsil eden bu arabirimi almak için [GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md) çağrısı.

 Bu arabirim bir kesme noktası isteği oluştururken de kullanılır (bkz. [BP_REQUEST_INFO).](../../../extensibility/debugger/reference/bp-request-info.md)

 Bu arabirim bir sınır veya hata kesme noktası çözümleniyorken de döndürülür (bkz. [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) ve [BP_ERROR_RESOLUTION_INFO).](../../../extensibility/debugger/reference/bp-error-resolution-info.md)

## <a name="methods-in-vtable-order"></a>Vtable Sırasına Göre Yöntemler
 Aşağıdaki tabloda yöntemlerini `IDebugThread2` gösterir.

|Yöntem|Açıklama|
|------------|-----------------|
|[EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)|Bu iş parçacığı için yığın çerçevelerinin listesini alın.|
|[GetName](../../../extensibility/debugger/reference/idebugthread2-getname.md)|İş parçacığının adını alır.|
|[SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)|İş parçacığının adını ayarlar.|
|[GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)|Bir iş parçacığının çalıştır olduğu programı alır.|
|[CanSetNextStatement](../../../extensibility/debugger/reference/idebugthread2-cansetnextstatement.md)|Sonraki deyimin verilen yığın çerçevesine ve kod bağlamına ayar olup olmadığını belirler.|
|[SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)|Verilen yığın çerçevesi ve kod bağlamı için sonraki deyimi ayarlar.|
|[GetThreadId](../../../extensibility/debugger/reference/idebugthread2-getthreadid.md)|Sistem iş parçacığı tanımlayıcısını alır.|
|[Askıya Alma](../../../extensibility/debugger/reference/idebugthread2-suspend.md)|Bir iş parçacığını askıya alır.|
|[Sürdür](../../../extensibility/debugger/reference/idebugthread2-resume.md)|Bir iş parçacığını sürdürür.|
|[GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)|Bir iş parçacığını açıklayan özellikleri alır.|
|[GetLogicalThread](../../../extensibility/debugger/reference/idebugthread2-getlogicalthread.md)|Bu fiziksel iş parçacığıyla ilişkili mantıksal iş parçacığını alır.|

## <a name="remarks"></a>Açıklamalar
 Tek bir fiziksel iş parçacığı birden çok programda çalıştırılayana kadar, birden `IDebugThread2` fazla programdan birden fazla aynı fiziksel iş parçacığını temsil ediyor olabilir.

 Bir kesme noktası veya özel durum oluştuğunda, Event çağrılarak bir olay [gönderilir.](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) Bu yöntemin bağımsız değişkenlerinden biri, geçerli iş `IDebugThread2` parçacığını temsil eden bir arabirimdir. [EnumFrameInfo,](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) geçerli yığın çerçevesinin [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) arabirimini almak için kullanılır.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [Olay](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
