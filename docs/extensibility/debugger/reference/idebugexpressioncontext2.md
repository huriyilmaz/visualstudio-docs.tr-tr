---
title: IDebugExpressionContext2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionContext2
helpviewer_keywords:
- IDebugExpressionContext2 interface
ms.assetid: 577fdaae-4b2d-4112-9839-ab899535fa6f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 344ae287b3784ceca87fbbab09ad2b2e0a304205
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80729633"
---
# <a name="idebugexpressioncontext2"></a>IDebugExpressionContext2
Bu arabirim, ifade değerlendirmesi için bir bağlamı temsil eder

## <a name="syntax"></a>Syntax

```
IDebugExpressionContext2 : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Hata ayıklama altyapısı (DE), bir ifadenin değerlendirilebileceği bir bağlamı göstermek için bu arabirimi uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) çağrısı bu arabirimi döndürür. Bu arabirime yalnızca, hata Ayıklanan program duraklatıldığında ve yığın çerçevesi kullanılabilir olduğunda erişilebilir.

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDebugExpressionContext2` .

|Yöntem|Açıklama|
|------------|-----------------|
|[GetName](../../../extensibility/debugger/reference/idebugexpressioncontext2-getname.md)|Değerlendirme bağlamının adını alır.|
|[ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)|Değerlendirme için metin tabanlı bir ifade ayrıştırır.|

## <a name="remarks"></a>Açıklamalar
 Değerlendirme bağlamı, ifade değerlendirmesi gerçekleştirmeye yönelik bir kapsam olarak düşünülebilir.

 Bir program durdurulduğunda, oturum hata ayıklama Yöneticisi (SDM), bir [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)çağrısıyla de bir yığın çerçevesi edinir. SDM daha sonra arayüzü almak için [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) öğesini çağırır `IDebugExpressionContext2` . Bu, bir [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) arabirimi oluşturmak Için bir [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) çağrısı izler ve bu, değerlendirilmeye hazırmış olan ayrıştırılmış ifadeyi temsil eder.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)
- [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)
