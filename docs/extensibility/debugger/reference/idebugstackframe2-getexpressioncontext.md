---
description: Bir yığın çerçevesinin ve iş parçacığının geçerli bağlamında ifade değerlendirmesi için bir değerlendirme bağlamı alır.
title: IDebugStackFrame2::GetExpressionContext | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetExpressionContext
helpviewer_keywords:
- IDebugStackFrame2::GetExpressionContext
ms.assetid: a2604e6a-502d-473b-868f-b11ac64c7a35
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d95af977f77bc48a112d584d613877d3259bdb90
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725129"
---
# <a name="idebugstackframe2getexpressioncontext"></a>IDebugStackFrame2::GetExpressionContext
Bir yığın çerçevesinin ve iş parçacığının geçerli bağlamında ifade değerlendirmesi için bir değerlendirme bağlamı alır.

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
[out] İfade değerlendirmesi [bağlamını temsil eden bir IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Genellikle ifade değerlendirme bağlamı, ifade değerlendirmesi gerçekleştirmek için bir kapsam olarak değerlendirin. Bir [ifadeyi ayrıştırmak için ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) yöntemini çağırma ve ardından ayrıştırilen ifadeyi değerlendirmek için sonuçta elde edilen [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) veya [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) yöntemlerini çağırma.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)
- [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
