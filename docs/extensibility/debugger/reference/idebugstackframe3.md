---
title: IDebugStackFrame3 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame3
helpviewer_keywords:
- IDebugStackFrame3 interface
ms.assetid: 39af2f57-0a01-42b8-b093-b7fbc61e2909
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d86997d11e124fd5a47981314cf383f5cd8aff7d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719475"
---
# <a name="idebugstackframe3"></a>IDebugStackFrame3
Bu arabirim, yakalanan özel durumları işlemek için [IDebugStackFrame2'yi](../../../extensibility/debugger/reference/idebugstackframe2.md) genişletir.

## <a name="syntax"></a>Sözdizimi

```
IDebugStackFrame3 : IDebugStackFrame2
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Hata ayıklama altyapısı (DE), yakalanan özel durumları desteklemek için bu arabirimi [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) arabirimini uygulayan nesne üzerinde uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu arabirimi `IDebugStackFrame2` elde etmek için [queryinterface'i](/cpp/atl/queryinterface) bir arabirimden arayın.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 [IDebugStackFrame2'den](../../../extensibility/debugger/reference/idebugstackframe2.md)devralınan yöntemlere `IDebugStackFrame3` ek olarak, aşağıdaki yöntemleri ortaya çıkarır.

|Yöntem|Açıklama|
|------------|-----------------|
|[InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)|Normal bir özel durum işlemeden önce geçerli yığın çerçevesi için bir özel durum işler.|
|[GetUnwindCodeContext](../../../extensibility/debugger/reference/idebugstackframe3-getunwindcodecontext.md)|Yığın gevşemesi meydana gelirse kod bağlamı döndürür.|

## <a name="remarks"></a>Açıklamalar
 Yakalanan özel durum, normal bir özel durum işleme yordamları çalışma süresine göre çağrılmadan önce bir hata ayıklama nın bir özel durum işleyebilir anlamına gelir. Bir özel durumu engellemek, aslında çalışma süresini, olmadığında bile bir özel durum işleyicisi varmış gibi davranmayı sağlamak anlamına gelir.

- [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) tüm normal özel durum geri arama olayları sırasında çağrılır (bunun tek istisnası karışık mod kodunu (yönetilen ve yönetilmeyen kod) hata ayıklama iseniz, bu durumda özel durum son şans geri arama sırasında ele geçirilemez). DE uygulamaz `IDebugStackFrame3`veya DE IDebugStackFrame3 bir hata döndürür::`InterceptCurrentException` `E_NOTIMPL`(gibi), sonra hata ayıklayıcı normal özel durum işleyecektir.

 Bir özel durum engelleyerek, hata ayıklama kullanıcı nın program debugged durumu değişiklik yapmak ve sonra özel durum atıldı noktada yürütme devam etmesine izin verebilir.

> [!NOTE]
> Yakalanan özel durumlara yalnızca yönetilen kodda, yani Ortak Dil Çalışma Zamanı (CLR) altında çalışan bir programda izin verilir.

 Hata ayıklama altyapısı, işlevi kullanarak çalışma zamanında 1 değerine "metricExceptions" ayarlayarak `SetMetric` özel durumları engellemeyi desteklediğini gösterir. Daha fazla bilgi için Hata [Ayıklama için SDK Yardımcıları bölümüne](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)bakın.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [Hata Ayıklama için SDK Yardımcıları](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
