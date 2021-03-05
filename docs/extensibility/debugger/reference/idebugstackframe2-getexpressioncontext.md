---
description: Yığın çerçevesinin ve iş parçacığının geçerli bağlamı içindeki ifade değerlendirmesi için bir değerlendirme bağlamı alır.
title: 'IDebugStackFrame2:: GetExpressionContext | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetExpressionContext
helpviewer_keywords:
- IDebugStackFrame2::GetExpressionContext
ms.assetid: a2604e6a-502d-473b-868f-b11ac64c7a35
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4780b979102ee2ada499e2cd2e0f8ca728cadd91
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102145943"
---
# <a name="idebugstackframe2getexpressioncontext"></a>IDebugStackFrame2::GetExpressionContext
Yığın çerçevesinin ve iş parçacığının geçerli bağlamı içindeki ifade değerlendirmesi için bir değerlendirme bağlamı alır.

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
dışı İfade değerlendirmesi için bir bağlamı temsil eden bir [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Genellikle, ifade değerlendirme bağlamı ifade değerlendirmesi gerçekleştirmeye yönelik bir kapsam olarak düşünülebilir. Bir ifadeyi ayrıştırmak için [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) yöntemini çağırın ve ardından ayrıştırılmış ifadeyi değerlendirmek için elde edilen [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) veya [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) yöntemlerini çağırın.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)
- [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
