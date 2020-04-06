---
title: IDebugExpression2::EvaluateAsync | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpression2::EvaluateAsync
helpviewer_keywords:
- IDebugExpression2::EvaluateAsync
ms.assetid: 848fe6cb-0759-42f2-890b-d2b551c527d6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2cd1eba56f8e3c5a1a779acc3330790e9ba2bc96
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729756"
---
# <a name="idebugexpression2evaluateasync"></a>IDebugExpression2::EvaluateAsync
Bu yöntem ifadeyi eşsenkronize olarak değerlendirir.

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
[içinde] İfade değerlendirmesini kontrol eden [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) numaralandırmasından gelen bayrakların birleşimi.

`pExprCallback`\
[içinde] Bu parametre her zaman null bir değerdir.

## <a name="return-value"></a>Dönüş Değeri
Başarılı olursa, `S_OK`döner; aksi takdirde bir hata kodu döndürür. Tipik bir hata kodu:

|Hata|Açıklama|
|-----------|-----------------|
|E_EVALUATE_BUSY_WITH_EVALUATION|Başka bir ifade şu anda değerlendirilmektedir ve eşzamanlı ifade değerlendirmesi desteklenmemektedir.|

## <a name="remarks"></a>Açıklamalar
Bu yöntem, ifade değerlendirmesine başladıktan hemen sonra geri dönmelidir. İfade başarıyla değerlendirildiğinde, [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) Ekle veya [Ekle](../../../extensibility/debugger/reference/idebugprogram2-attach.md) aracılığıyla sağlanan [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) olay geri [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)çağırmasına gönderilmelidir.

## <a name="example"></a>Örnek
Aşağıdaki örnek, `CExpression` [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) arabirimini uygulayan basit bir nesne için bu yöntemin nasıl uygulanacağını gösterir.

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
