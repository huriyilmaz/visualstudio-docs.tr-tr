---
description: Daha sonraki değerlendirme için metin biçimindeki bir ifadeyi ayrıştırır.
title: IDebugExpressionContext2::P arseText | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionContext2::ParseText
helpviewer_keywords:
- IDebugExpressionContext2::ParseText
ms.assetid: f58575db-f926-4ac8-83ff-7b3b86ab61e2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 72cb26cf71b2994b25033d61adea52e8439d2fbd
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105092312"
---
# <a name="idebugexpressioncontext2parsetext"></a>IDebugExpressionContext2::ParseText
Daha sonraki değerlendirme için metin biçimindeki bir ifadeyi ayrıştırır.

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
'ndaki Ayrıştırılacak ifade.

`dwFlags`\
'ndaki Ayrıştırma denetleyen [parseflags](../../../extensibility/debugger/reference/parseflags.md) numaralandırmasındaki bayrakların birleşimi.

`nRadix`\
'ndaki İçinde herhangi bir sayısal bilgi ayrıştırılırken kullanılacak taban tabanı `pszCode` .

`ppExpr`\
dışı Bağlama ve değerlendirme için hazırlanma olan ayrıştırılmış ifadeyi temsil eden [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) nesnesini döndürür.

`pbstrError`\
dışı İfade bir hata içeriyorsa hata iletisini döndürür.

`pichError`\
dışı İfade bir hata içeriyorsa içindeki hatanın karakter dizinini döndürür `pszCode` .

## <a name="return-value"></a>Dönüş Değeri
Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
Bu yöntem çağrıldığında, bir hata ayıklama altyapısı (DE), ifadeyi ayrıştırır ve doğruluğu doğru şekilde doğrular. `pbstrError` `pichError` İfade geçersizse ve parametreleri doldurulmuş olabilir.

İfadenin değerlendirilmediğini ve yalnızca ayrıştırılmadığını unutmayın. Daha sonra [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) veya [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) yöntemlerine yapılan bir çağrı, ayrıştırılmış ifadeyi değerlendirir.

## <a name="example"></a>Örnek
Aşağıdaki örnek, `CEnvBlock` [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) arabirimini kullanıma sunan basit bir nesne için bu yöntemin nasıl uygulanacağını gösterir. Bu örnek, ifadeyi bir ortam değişkeninin adı olarak ayrıştırılacak şekilde değerlendirir ve bu değişkenin değerini alır.

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
