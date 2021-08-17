---
description: Bu arabirim, araya gelen özel durumları işlemek için IDebugStackFrame2'nin genişletmesini sağlar.
title: IDebugStackFrame3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame3
helpviewer_keywords:
- IDebugStackFrame3 interface
ms.assetid: 39af2f57-0a01-42b8-b093-b7fbc61e2909
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 6dbe76962d525daf22d276c229011ef318ba266d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122126134"
---
# <a name="idebugstackframe3"></a>IDebugStackFrame3
Bu arabirim, [araya gelen özel durumları işlemek için IDebugStackFrame2'nin](../../../extensibility/debugger/reference/idebugstackframe2.md) genişletmesini sağlar.

## <a name="syntax"></a>Syntax

```
IDebugStackFrame3 : IDebugStackFrame2
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Hata ayıklama altyapısı (DE), bu arabirimi, araya konulan özel durumları desteklemek için [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) arabirimini uygulayan nesnede de uygulamaya almaktadır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu arabirimi almak için bir arabirimde [QueryInterface](/cpp/atl/queryinterface) `IDebugStackFrame2` çağrısı yapmak.

## <a name="methods-in-vtable-order"></a>Vtable Sırasına Göre Yöntemler
 [IDebugStackFrame2'den](../../../extensibility/debugger/reference/idebugstackframe2.md)devralınan yöntemlere ek olarak `IDebugStackFrame3` aşağıdaki yöntemleri gösterir.

|Yöntem|Açıklama|
|------------|-----------------|
|[InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)|Herhangi bir normal özel durum işlemeden önce geçerli yığın çerçevesi için bir özel durumu işleme.|
|[GetUnwindCodeContext](../../../extensibility/debugger/reference/idebugstackframe3-getunwindcodecontext.md)|Yığın geriye doğru izleme gerçekleşirse bir kod bağlamı döndürür.|

## <a name="remarks"></a>Açıklamalar
 Araya alınan özel durum, bir hata ayıklayıcının herhangi bir normal özel durum işleme yordamı çalışma zamanı tarafından çağrılmadan önce bir özel durumu işleyebilirsiniz. Bir özel durumun araya olması, çalışma zamanında, mevcut bir özel durum işleyicisi olmadığını varsama anlamına gelir.

- [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) tüm normal özel durum geri çağırma olayları sırasında çağrılır (karma mod kodunda (yönetilen ve yönetilemeyen kod) hata ayıklaması yapmak için tek özel durumdur; bu durumda son şans geri çağırma sırasında özel durum kesilemez). DE uygulamazsa veya `IDebugStackFrame3` DE, IDebugStackFrame3:: (gibi) hata döndürürse, hata ayıklayıcı özel durumu `InterceptCurrentException` normal şekilde `E_NOTIMPL` işler.

 Hata ayıklayıcı, bir özel durumu keserek, kullanıcının hata ayıklama yapılan programın durumu üzerinde değişiklik yapmalarına ve ardından yürütmeyi özel durumun at olduğu noktada sürdürmesine izin verebilir.

> [!NOTE]
> Araya gelen özel durumlara yalnızca yönetilen kodda, yani Ortak Dil Çalışma Zamanı (CLR) altında çalışan bir programda izin verilir.

 Hata ayıklama altyapısı, işlevini kullanarak "metricExceptions" değerini çalışma zamanında 1 değerine ayarerek özel durumların araya müdahalesini desteklediğini `SetMetric` gösterir. Daha fazla bilgi için bkz. [Hata Ayıklama için SDK Yardımcıları.](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [Hata Ayıklama için SDK Yardımcıları](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
