---
title: IDebugStackFrame2::GetExpressionContext | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetExpressionContext
helpviewer_keywords:
- IDebugStackFrame2::GetExpressionContext
ms.assetid: a2604e6a-502d-473b-868f-b11ac64c7a35
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fb1a075d04ed53fdbe2181975a56eddfcbc3b683
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719747"
---
# <a name="idebugstackframe2getexpressioncontext"></a>IDebugStackFrame2::GetExpressionContext
Yığın çerçevesi ve iş parçacığının geçerli bağlamında ifade değerlendirmesi için bir değerlendirme bağlamı alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetExpressionContext ( 
   IDebugExpressionContext2** ppExprCxt
);
```

```csharp
int GetExpressionContext ( 
   out IDebugExpressionContext2 ppExprCxt
);
```

## <a name="parameters"></a>Parametreler
`ppExprCxt`\
[çıkış] İfade değerlendirmesi için bir bağlamı temsil eden bir [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Genel olarak, bir ifade değerlendirme bağlamı ifade değerlendirme gerçekleştirmek için bir kapsam olarak düşünülebilir. [ParseText yöntemini](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) bir ifadeyi ayrışdırmak için arayın ve ardından ayrışmış ifadeyi değerlendirmek için ortaya çıkan [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) veya [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) yöntemlerini çağırın.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)
- [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
