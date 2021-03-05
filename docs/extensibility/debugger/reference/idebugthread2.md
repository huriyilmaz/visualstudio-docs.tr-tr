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
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d8b09aa546e4711b1c11623a3596ba0e385b2a14
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102164428"
---
# <a name="idebugthread2"></a>IDebugThread2
Bu arabirim, bir programda çalışan bir iş parçacığını temsil eder.

## <a name="syntax"></a>Syntax

```
IDebugThread2 : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Hata ayıklama altyapısı (DE), bu arabirimi tek bir programda yürütmenin iş parçacığını temsil etmek için uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Şu anda etkin olan iş parçacığını temsil eden bu arabirimi edinmek için [GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md) 'i çağırın.

 Bu arabirim ayrıca kesme noktası isteği oluştururken de kullanılır (bkz. [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)).

 Bu arabirim, bir bağlantılı veya hata kesme noktası çözümlenirken de döndürülür (bkz. [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) ve [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)).

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDebugThread2` .

|Yöntem|Açıklama|
|------------|-----------------|
|[EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)|Bu iş parçacığının yığın çerçevelerinin bir listesini alır.|
|[GetName](../../../extensibility/debugger/reference/idebugthread2-getname.md)|İş parçacığının adını alır.|
|[SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)|İş parçacığının adını ayarlar.|
|[GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)|Bir iş parçacığının çalıştığı programı alır.|
|[CanSetNextStatement](../../../extensibility/debugger/reference/idebugthread2-cansetnextstatement.md)|Sonraki deyimin verilen yığın çerçevesine ve kod bağlamına ayarlanamayacağını belirler.|
|[SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)|Sonraki ifadeyi verilen yığın çerçevesine ve kod bağlamına ayarlar.|
|[GetThreadId](../../../extensibility/debugger/reference/idebugthread2-getthreadid.md)|Sistem iş parçacığı tanımlayıcısını alır.|
|[Askıya Alma](../../../extensibility/debugger/reference/idebugthread2-suspend.md)|Bir iş parçacığını askıya alır.|
|[Sürdür](../../../extensibility/debugger/reference/idebugthread2-resume.md)|Bir iş parçacığını sürdürür.|
|[GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)|Bir iş parçacığını tanımlayan özellikleri alır.|
|[GetLogicalThread](../../../extensibility/debugger/reference/idebugthread2-getlogicalthread.md)|Bu fiziksel iş parçacığı ile ilişkili mantıksal iş parçacığını alır.|

## <a name="remarks"></a>Açıklamalar
 Tek bir fiziksel iş parçacığı birden çok programda çalıştırılabildiğinden, birden fazla programdan birden fazla `IDebugThread2` Program aynı fiziksel iş parçacığını temsil edebilir.

 Kesme noktası veya özel durum oluştuğunda [olay çağırarak bir olay gönderilir](../../../extensibility/debugger/reference/idebugeventcallback2-event.md). Bu yöntemin bağımsız değişkenlerinden biri, `IDebugThread2` geçerli iş parçacığını temsil eden bir arabirimdir. [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) , geçerli yığın çerçevesinin [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) arabirimini almak için kullanılır.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [Olay](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
