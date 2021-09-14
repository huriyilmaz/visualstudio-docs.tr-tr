---
description: Bu yöntem EvaluateAsync) yöntemine yapılan bir çağrı tarafından başlatan zaman uyumsuz ifade değerlendirmesini iptal eder.
title: IDebugExpression2::Abort | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpression2::Abort
helpviewer_keywords:
- IDebugExpression2::Abort
ms.assetid: 4fcb712e-1bdb-4b75-a440-35cc79ee147e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: be5637b350e9448b5c02ede5087fed6c2df26bb4
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725800"
---
# <a name="idebugexpression2abort"></a>IDebugExpression2::Abort
Bu yöntem [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) yöntemine yapılan bir çağrı tarafından başlatan zaman uyumsuz ifade değerlendirmesini iptal eder.

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
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Zaman uyumsuz ifade değerlendirmesi iptal edilirken, [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md) veya [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) yöntemlerine geçirilen olay geri çağırmaya [bir IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) olayı gönderilmez.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)
- [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
