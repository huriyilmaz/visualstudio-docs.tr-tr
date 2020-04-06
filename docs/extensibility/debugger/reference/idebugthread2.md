---
title: IDebugThread2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2
helpviewer_keywords:
- IDebugThread2 interface
ms.assetid: 221b4b1b-4a26-466e-bc29-5eff800fab13
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1965ff1b4cfa89e4584c194942dec7ae486473ff
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718587"
---
# <a name="idebugthread2"></a>IDebugThread2
Bu arabirim, bir programda çalışan bir iş parçacığı temsil eder.

## <a name="syntax"></a>Sözdizimi

```
IDebugThread2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Hata ayıklama altyapısı (DE) tek bir programda yürütme iş parçacığı temsil etmek için bu arabirimi uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Şu anda etkin olan iş parçacığı temsil eden bu arabirimi elde etmek için [GetThread'i](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md) arayın.

 Bu arabirim, kesme noktası isteği oluştururken de kullanılır (bkz. [BP_REQUEST_INFO).](../../../extensibility/debugger/reference/bp-request-info.md)

 Bu arabirim, bağlı veya hata kesme noktasını çözerken de döndürülür (bkz. [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) ve [BP_ERROR_RESOLUTION_INFO).](../../../extensibility/debugger/reference/bp-error-resolution-info.md)

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 Aşağıdaki tabloda `IDebugThread2`.

|Yöntem|Açıklama|
|------------|-----------------|
|[EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)|Bu iş parçacığı için yığın çerçevelerinin listesini alır.|
|[GetName](../../../extensibility/debugger/reference/idebugthread2-getname.md)|İş parçacığının adını alır.|
|[SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)|İş parçacığının adını ayarlar.|
|[GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)|İş parçacığının çalıştırıldığı programı alır.|
|[CanSetNextStatement](../../../extensibility/debugger/reference/idebugthread2-cansetnextstatement.md)|Bir sonraki deyimin verilen yığın çerçevesi ve kod bağlamına ayarlanıp ayarlanamayacağını belirler.|
|[SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)|Sonraki deyimi verilen yığın çerçevesi ve kod bağlamına ayarlar.|
|[GetThreadId](../../../extensibility/debugger/reference/idebugthread2-getthreadid.md)|Sistem iş parçacığı tanımlayıcısını alır.|
|[Suspend](../../../extensibility/debugger/reference/idebugthread2-suspend.md)|İş parçacığı askıya alınır.|
|[Sürdür](../../../extensibility/debugger/reference/idebugthread2-resume.md)|Bir iş parçacığı devam eder.|
|[GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)|İş parçacığı açıklayan özellikleri alır.|
|[GetLogicalThread](../../../extensibility/debugger/reference/idebugthread2-getlogicalthread.md)|Bu fiziksel iş parçacığı ile ilişkili mantıksal iş parçacığı alır.|

## <a name="remarks"></a>Açıklamalar
 Tek bir fiziksel iş parçacığı birden çok `IDebugThread2` programda çalıştırılabildiği için, birden fazla programdan birden fazla kişi aynı fiziksel iş parçacığı temsil edebilir.

 Bir kesme noktası veya özel durum oluştuğunda, [olay Olay'ı](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)arayarak bir olay gönderilir. Bu yöntemin bağımsız değişkenlerinden `IDebugThread2` biri geçerli iş parçacığı temsil eden bir arabirimdir. [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) geçerli yığın çerçevesi için [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) arabirimini elde etmek için kullanılır.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [Olay](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
