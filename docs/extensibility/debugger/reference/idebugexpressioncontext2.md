---
title: IDebugExpressionContext2 | Microsoft Dokümanlar
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729633"
---
# <a name="idebugexpressioncontext2"></a>IDebugExpressionContext2
Bu arabirim ifade değerlendirmesi için bir bağlam temsil eder

## <a name="syntax"></a>Sözdizimi

```
IDebugExpressionContext2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Hata ayıklama altyapısı (DE), bir ifadenin değerlendirilebileceği bir bağlamı temsil etmek için bu arabirimi uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) için bir çağrı bu arabirimi döndürür. Bu arabirime yalnızca debugged olan program duraklatılmış ve bir yığın çerçeve kullanılabilir olduğunda erişilebilir.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 Aşağıdaki tabloda `IDebugExpressionContext2`.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetName](../../../extensibility/debugger/reference/idebugexpressioncontext2-getname.md)|Değerlendirme bağlamının adını alır.|
|[ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)|Değerlendirme için metin tabanlı bir ifadeyi parslar.|

## <a name="remarks"></a>Açıklamalar
 Bir değerlendirme bağlamı ifade değerlendirmesi gerçekleştirmek için bir kapsam olarak düşünülebilir.

 Bir program durdurulduğunda, oturum hata ayıklama yöneticisi (SDM) [EnumFrameInfo'ya](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)bir çağrı yla DE'den bir yığın çerçevesi alır. SDM daha sonra arabirimi almak `IDebugExpressionContext2` için [GetExpressionContext'ı](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) arar. Bunu, ayrıştırılmış ifadeyi temsil eden bir [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) arabirimi oluşturmak için [ParseText'e](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) yapılan çağrı takip eder.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)
- [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)
