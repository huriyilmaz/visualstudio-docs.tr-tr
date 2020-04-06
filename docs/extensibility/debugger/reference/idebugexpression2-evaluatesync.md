---
title: IDebugExpression2::EvaluateSync | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpression2::EvaluateSync
helpviewer_keywords:
- IDebugExpression2::EvaluateSync
ms.assetid: 88964915-dce3-4005-b4f3-9f37415e41e4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 306ed6af2a0a0b8fdb4525a112e680e289e6e6df
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729682"
---
# <a name="idebugexpression2evaluatesync"></a>IDebugExpression2::EvaluateSync
Bu yöntem, ifadeyi eşzamanlı olarak değerlendirir.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT EvaluateSync(
    EVALFLAGS             dwFlags,
    DWORD                 dwTimeout,
    IDebugEventCallback2* pExprCallback,
    IDebugProperty2**     ppResult
);
```

```csharp
int EvaluateSync(
    enum_EVALFLAGS       dwFlags,
    uint                 dwTimeout,
    IDebugEventCallback2 pExprCallback,
    out IDebugProperty2  ppResult
);
```

## <a name="parameters"></a>Parametreler
`dwFlags`\
[içinde] İfade değerlendirmesini kontrol eden [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) numaralandırmasından gelen bayrakların birleşimi.

`dwTimeout`\
[içinde] Bu yöntemden dönmeden önce beklemek için milisaniye cinsinden maksimum süre. Süresiz beklemek için kullanın. `INFINITE`

`pExprCallback`\
[içinde] Bu parametre her zaman null bir değerdir.

`ppResult`\
[çıkış] İfade değerlendirme sonucunu içeren [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) nesnesini döndürür.

## <a name="return-value"></a>Dönüş Değeri
Başarılı olursa, `S_OK`döner; aksi takdirde bir hata kodu döndürür. Bazı tipik hata kodları şunlardır:

|Hata|Açıklama|
|-----------|-----------------|
|E_EVALUATE_BUSY_WITH_EVALUATION|Başka bir ifade şu anda değerlendirilmektedir ve eşzamanlı ifade değerlendirmesi desteklenmemektedir.|
|E_EVALUATE_TIMEOUT|Değerlendirme zaman doldu.|

## <a name="remarks"></a>Açıklamalar
Senkron değerlendirme için, değerlendirme tamamlandıktan sonra bir olayı Visual Studio'ya geri göndermeye gerek yoktur.

## <a name="example"></a>Örnek
Aşağıdaki örnek, `CExpression` [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) arabirimini uygulayan basit bir nesne için bu yöntemin nasıl uygulanacağını gösterir.

```cpp
HRESULT CExpression::EvaluateSync(EVALFLAGS dwFlags,
                                  DWORD dwTimeout,
                                  IDebugEventCallback2* pExprCallback,
                                  IDebugProperty2** ppResult)
{
    // Set the aborted state to FALSE.
    m_bAborted = FALSE;
    // Delegate the evaluation to EvalExpression.
    return EvalExpression(TRUE, ppResult);
}

HRESULT CExpression::EvalExpression(BOOL bSynchronous,
                                    IDebugProperty2** ppResult)
{
    HRESULT hr;

    // Get the value of an environment variable.
    PCSTR pszVal = m_pEnvBlock->GetEnv(m_pszVarName);
    // Create and initialize a CEnvVar object with the retrieved value.
    // CEnvVar implements the IDebugProperty2 interface.
    CComObject<CEnvVar> *pEnvVar;
    CComObject<CEnvVar>::CreateInstance(&pEnvVar);
    pEnvVar->Init(m_pszVarName, pszVal, m_pDoc);

    if (pszVal) {
        // Check for synchronous evaluation.
        if (bSynchronous) {
            // Set and AddRef the result, IDebugProperty2 interface.
            *ppResult = pEnvVar;
            (*ppResult)->AddRef();
            hr = S_OK;
        } else {
            //For asynchronous evaluation, send an evaluation complete event.
            CExprEvalEvent *pExprEvent = new CExprEvalEvent(this, pEnvVar);
            pExprEvent->SendEvent(m_pExprCallback, NULL, NULL, NULL);
        }
    } else {
        // If a valid value is not retrieved, return E_FAIL.
        hr = E_FAIL;
    }
    return hr;
}
```

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)
- [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
