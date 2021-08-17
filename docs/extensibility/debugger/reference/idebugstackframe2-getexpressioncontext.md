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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 97894a07c593a9793f898a7a44b59b5f9f87692c7b0e740b6ace6ce502e8cc57
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121338455"
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
