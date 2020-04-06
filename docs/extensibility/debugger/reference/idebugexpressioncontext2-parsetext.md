---
title: IDebugExpressionContext2::ParseText | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionContext2::ParseText
helpviewer_keywords:
- IDebugExpressionContext2::ParseText
ms.assetid: f58575db-f926-4ac8-83ff-7b3b86ab61e2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a8494c9c90c4cb6e94115c542a25e12e948f7064
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729652"
---
# <a name="idebugexpressioncontext2parsetext"></a>IDebugExpressionContext2::ParseText
Daha sonraki değerlendirme için metin biçiminde bir ifade parses.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT ParseText(
    LPCOLESTR           pszCode,
    PARSEFLAGS          dwFlags,
    UINT                nRadix,
    IDebugExpression2** ppExpr,
    BSTR*               pbstrError,
    UINT*               pichError
);
```

```csharp
int ParseText(
    string                pszCode,
    enum_PARSEFLAGS       dwFlags,
    uint                  nRadix,
    out IDebugExpression2 ppExpr,
    out string            pbstrError,
    out uint              pichError
);
```

## <a name="parameters"></a>Parametreler
`pszCode`\
[içinde] Ayrışdırılması gereken ifade.

`dwFlags`\
[içinde] Ayrıştırma denetimleri [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md) numaralandırma gelen bayrakların bir kombinasyonu.

`nRadix`\
[içinde] Herhangi bir sayısal bilginin ayrışdırılmasında `pszCode`kullanılacak radix.

`ppExpr`\
[çıkış] Bağlama ve değerlendirmeye hazır ayrıştırılmış ifadeyi temsil eden [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) nesnesini döndürür.

`pbstrError`\
[çıkış] İfade bir hata içeriyorsa hata iletisini döndürür.

`pichError`\
[çıkış] İfade bir hata içeriyorsa hatanın `pszCode` karakter dizini döndürür.

## <a name="return-value"></a>Dönüş Değeri
Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
Bu yöntem çağrıldığında, hata ayıklama altyapısı (DE) ifadeyi ayrıştırmalı ve doğruluk için doğrulamalıdır. İfade `pbstrError` `pichError` geçersizse ve parametreler doldurulabilir.

İfadenin değerlendirilmediğini, yalnızca ayrıştırılmış olduğunu unutmayın. [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) veya [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) yöntemlerine daha sonra yapılan bir çağrı, ayrışmış ifadeyi değerlendirir.

## <a name="example"></a>Örnek
Aşağıdaki örnek, [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) `CEnvBlock` arabirimini ortaya çıkaran basit bir nesne için bu yöntemin nasıl uygulanacağını gösterir. Bu örnek, ifadeyi bir ortam değişkeninin adı olarak ayrıştını dikkate alır ve bu değişkenden değeri alır.

```cpp
HRESULT CEnvBlock::ParseText(
    LPCOLESTR           pszCode,
    PARSEFLAGS          dwFlags,
    UINT                nRadix,
    IDebugExpression2 **ppExpr,
    BSTR               *pbstrError,
    UINT               *pichError)
{
    HRESULT hr = E_OUTOFMEMORY;
    // Create an integer variable with a value equal to one plus
    // twice the length of the passed expression to be parsed.
    int iAnsiLen      = 2 * (wcslen(pszCode)) + 1;
    // Allocate a character string of the same length.
    char *pszAnsiCode = (char *) malloc(iAnsiLen);

    // Check for successful memory allocation.
    if (pszAnsiCode) {
        // Map the wide-character pszCode string to the new pszAnsiCode character string.
        WideCharToMultiByte(CP_ACP, 0, pszCode, -1, pszAnsiCode, iAnsiLen, NULL, NULL);
        // Check to see if the app can succesfully get the environment variable.
        if (GetEnv(pszAnsiCode)) {

            // Create and initialize a CExpression object.
            CComObject<CExpression> *pExpr;
            CComObject<CExpression>::CreateInstance(&pExpr);
            pExpr->Init(pszAnsiCode, this, NULL);

            // Assign the pointer to the new object to the passed argument
            // and AddRef the object.
            *ppExpr = pExpr;
            (*ppExpr)->AddRef();
            hr = S_OK;
        // If the program cannot succesfully get the environment variable.
        } else {
            // Set the errror message and return E_FAIL.
            *pbstrError = SysAllocString(L"No such environment variable.");
            hr = E_FAIL;
        }
        // Free the local character string.
        free(pszAnsiCode);
    }
    return hr;
}
```

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)
- [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md)
- [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)
