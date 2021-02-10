---
title: IDebugStackFrame3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame3
helpviewer_keywords:
- IDebugStackFrame3 interface
ms.assetid: 39af2f57-0a01-42b8-b093-b7fbc61e2909
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5511624fb69015351d8cc37d6b27ad142a5956d4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99961189"
---
# <a name="idebugstackframe3"></a>IDebugStackFrame3
Bu arabirim, ele geçirilebilecek özel durumları işlemek için [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) 'i genişletir.

## <a name="syntax"></a>Syntax

```
IDebugStackFrame3 : IDebugStackFrame2
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Hata ayıklama altyapısı (DE), bu arabirimi, kesilen özel durumları desteklemek için [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) arabirimini uygulayan aynı nesne üzerinde uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 [](/cpp/atl/queryinterface) `IDebugStackFrame2` Bu arabirimi edinmek Için arabirim üzerinde QueryInterface 'i çağırın.

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)öğesinden devralınan yöntemlere ek olarak `IDebugStackFrame3` aşağıdaki yöntemleri sunar.

|Yöntem|Açıklama|
|------------|-----------------|
|[InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)|Herhangi bir normal özel durum işlemeyle önce geçerli yığın çerçevesi için bir özel durum işler.|
|[GetUnwindCodeContext](../../../extensibility/debugger/reference/idebugstackframe3-getunwindcodecontext.md)|Yığın geriye doğru gerçekleşmesi durumunda kod bağlamını döndürür.|

## <a name="remarks"></a>Açıklamalar
 Oluşan bir özel durum, bir hata ayıklayıcının, normal özel durum işleme yordamlarının çalışma zamanı tarafından çağrılmadan önce bir özel durumu işleyebileceği anlamına gelir. Bir özel durumu kesintiye uğratan önce, çalışma süresinin, olmasa bile bir özel durum işleyicisinin mevcut olduğu anlamına gelir.

- Tüm normal özel durum geri çağırma olayları sırasında [Yakatcurrentexception](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) çağrılır (Bu durum, karma mod kodunda (yönetilen ve yönetilmeyen kod) hata ayıklaması yapıyorsanız, bu durumda özel durum son şans geri çağırması sırasında yakalanamayan bir durumdur. Veya uygulamamazsa `IDebugStackFrame3` veya IDebugStackFrame3:: (gibi) öğesinden bir hata döndürürse, `InterceptCurrentException` `E_NOTIMPL` hata ayıklayıcı özel durumu normal şekilde işleymeyecektir.

 Hata ayıklayıcı, bir özel durumu kesintiye uğratan, kullanıcının hata ayıklamakta olan programın durumunda değişiklik yapmasına ve sonra özel durumun oluşturulduğu noktada yürütmeyi sürdürmesine izin verebilir.

> [!NOTE]
> Yalnızca yönetilen kodda, yani ortak dil çalışma zamanı (CLR) altında çalışan bir programda, ele geçirilebilecek özel durumlara izin verilir.

 Bir hata ayıklama altyapısı, işlevini kullanarak çalışma zamanında "metricExceptions" değerini 1 değerine ayarlayarak, kesintiye uğratan özel durumları desteklediğini belirtir `SetMetric` . Daha fazla bilgi için bkz. [hata ayıklama Için SDK yardımcıları](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md).

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [Hata Ayıklama için SDK Yardımcıları](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
