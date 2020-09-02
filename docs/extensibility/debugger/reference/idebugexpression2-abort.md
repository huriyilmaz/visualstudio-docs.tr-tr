---
title: 'IDebugExpression2:: Abort | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpression2::Abort
helpviewer_keywords:
- IDebugExpression2::Abort
ms.assetid: 4fcb712e-1bdb-4b75-a440-35cc79ee147e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5de2e34a8ae1e038c2109627099dacc5bd03a1ac
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80729768"
---
# <a name="idebugexpression2abort"></a>IDebugExpression2::Abort
Bu yöntem, [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) yöntemine yapılan bir çağrı tarafından başlatılan zaman uyumsuz ifade değerlendirmesini iptal eder.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Abort(
   void
);
```

```csharp
int Abort();
```

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Zaman uyumsuz ifade değerlendirmesi iptal edildiğinde, [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md) veya [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) yöntemlerine geçirilen olay geri çağırması için bir [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) olayı göndermeyin.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)
- [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
