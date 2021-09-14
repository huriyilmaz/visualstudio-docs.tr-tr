---
description: Bu yöntem, ifadeyi zaman uyumsuz olarak değerlendirir.
title: IDebugExpression2::EvaluateAsync | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpression2::EvaluateAsync
helpviewer_keywords:
- IDebugExpression2::EvaluateAsync
ms.assetid: 848fe6cb-0759-42f2-890b-d2b551c527d6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ad7d4c41aae0b1d48502fdb19865e737004696ae
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725794"
---
# <a name="idebugexpression2evaluateasync"></a>IDebugExpression2::EvaluateAsync
Bu yöntem, ifadeyi zaman uyumsuz olarak değerlendirir.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT EvaluateAsync (
    EVALFLAGS             dwFlags,
    IDebugEventCallback2* pExprCallback
);
```

```csharp
int EvaluateAsync(
    enum_EVALFLAGS       dwFlags,
    IDebugEventCallback2 pExprCallback
);
```

## <a name="parameters"></a>Parametreler
`dwFlags`\
[in] İfade değerlendirmesini kontrol eden [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) numaralamasında yer alan bayrakların birleşimi.

`pExprCallback`\
[in] Bu parametre her zaman null değerdir.

## <a name="return-value"></a>Dönüş Değeri
Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür. Tipik bir hata kodu şöyledir:

|Hata|Açıklama|
|-----------|-----------------|
|E_EVALUATE_BUSY_WITH_EVALUATION|Şu anda başka bir ifade değerlendiriliyor ve eşzamanlı ifade değerlendirmesi desteklenmiyor.|

## <a name="remarks"></a>Açıklamalar
Bu yöntem, ifade değerlendirmesini başlattıktan hemen sonra dönmeli. İfade başarıyla değerlendir geldiğinde, Attach veya Attach aracılığıyla sağlandı olarak [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) olay geri çağırmaya bir [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) [gönder](../../../extensibility/debugger/reference/idebugprogram2-attach.md) [gerekir.](../../../extensibility/debugger/reference/idebugengine2-attach.md)

## <a name="example"></a>Örnek
Aşağıdaki örnek, `CExpression` [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) arabirimini uygulayan basit bir nesne için bu yöntemin nasıl uygulandığını gösterir.

```cpp
HRESULT CExpression::EvaluateAsync(EVALFLAGS dwFlags,
                                   IDebugEventCallback2* pExprCallback)
{
    // Set the aborted state to FALSE
    // in case the user tries to redo the evaluation after aborting.
    m_bAborted = FALSE;
    // Post the WM_EVAL_EXPR message in the message queue of the current thread.
    // This starts the expression evaluation on a background thread.
    PostThreadMessage(GetCurrentThreadId(), WM_EVAL_EXPR, 0, (LPARAM) this);
    return S_OK;
}
```

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)
- [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)
- [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
