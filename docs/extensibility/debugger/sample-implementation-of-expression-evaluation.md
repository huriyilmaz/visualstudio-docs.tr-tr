---
title: İfade Değerlendirme Örnek Uygulaması | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
- expression evaluation, examples
ms.assetid: 2a5f04b8-6c65-4232-bddd-9093653a22c4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cf994a61ed9283463cd01aa468018f6acce5e209
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713108"
---
# <a name="sample-implementation-of-expression-evaluation"></a>İfade değerlendirmesinin örnek uygulanması
> [!IMPORTANT]
> Visual Studio 2015'te ifade değerlendiricilerinin bu şekilde uygulanması amortismana uymaktadır. CLR ifade değerlendiricilerinin uygulanması hakkında bilgi [için, bkz.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) [Managed expression evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

 **Watch** penceresi ifadesi için Visual Studio, Bir [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) nesnesi oluşturmak için [ParseText'i](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) çağırır. `IDebugExpressionContext2::ParseText`bir ifade değerlendiricisi (EE) anında alır ve Bir [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) nesnealmak için [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) çağırır.

 Aşağıdaki `IDebugExpressionEvaluator::Parse` görevleri gerçekleştirir:

1. [Yalnızca C++ ] Hataları aramak için ifadeyi parses.

2. Arabirimi çalıştıran ve `CParsedExpression` ayrıştırılacak ifadeyi sınıfta depolayan bir sınıfı (bu örnekte çağrıldı) anında alatır. `IDebugParsedExpression`

3. `CParsedExpression` Nesneden `IDebugParsedExpression` arabirimi döndürür.

> [!NOTE]
> Aşağıdaki örneklerde ve MyCEE örneğinde, ifade değerlendiricisi ayrıştayı değerlendirmeden ayırmaz.

## <a name="managed-code"></a>Yönetilen kod
 Aşağıdaki kod yönetilen `IDebugExpressionEvaluator::Parse` kodda bir uygulama gösterir. Yöntemin bu sürümü, ayrıştırma kodu da aynı anda değerlendirildiği için Ayrıştırmayı [EvaluateSync'e](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) erteler [(bkz.](../../extensibility/debugger/evaluating-a-watch-expression.md)

```csharp
namespace EEMC
{
    public class CParsedExpression : IDebugParsedExpression
    {
        public HRESULT Parse(
                string                 expression,
                uint                   parseFlags,
                uint                   radix,
            out string                 errorMessage,
            out uint                   errorPosition,
            out IDebugParsedExpression parsedExpression)
        {
            errorMessage = "";
            errorPosition = 0;

            parsedExpression =
                new CParsedExpression(parseFlags, radix, expression);
            return COM.S_OK;
        }
    }
}
```

## <a name="unmanaged-code"></a>Yönetilmeyen kod
Aşağıdaki kod yönetilmeyen `IDebugExpressionEvaluator::Parse` kod bir uygulamadır. Bu yöntem, `Parse`ifadeyi ayrışdırmak ve hataları denetlemek için bir yardımcı işlev çağırır, ancak bu yöntem ortaya çıkan değeri yoksa. Resmi değerlendirme, ifade değerlendirilirken ayrıştırıldığı [Sync'e](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) ertelenir [(bkz.](../../extensibility/debugger/evaluating-a-watch-expression.md)

```cpp
STDMETHODIMP CExpressionEvaluator::Parse(
        in    LPCOLESTR                 pszExpression,
        in    PARSEFLAGS                flags,
        in    UINT                      radix,
        out   BSTR                     *pbstrErrorMessages,
        inout UINT                     *perrorCount,
        out   IDebugParsedExpression  **ppparsedExpression
    )
{
    if (pbstrErrorMessages == NULL)
        return E_INVALIDARG;
    else
        *pbstrErrormessages = 0;

    if (pparsedExpression == NULL)
        return E_INVALIDARG;
    else
        *pparsedExpression = 0;

    if (perrorCount == NULL)
        return E_INVALIDARG;

    HRESULT hr;
    // Look for errors in the expression but ignore results
    hr = ::Parse( pszExpression, pbstrErrorMessages );
    if (hr != S_OK)
        return hr;

    CParsedExpression* pparsedExpr = new CParsedExpression( radix, flags, pszExpression );
    if (!pparsedExpr)
        return E_OUTOFMEMORY;

    hr = pparsedExpr->QueryInterface( IID_IDebugParsedExpression,
                                      reinterpret_cast<void**>(ppparsedExpression) );
    pparsedExpr->Release();

    return hr;
}
```

## <a name="see-also"></a>Ayrıca bkz.
- [İzleme penceresi ifadesini değerlendirme](../../extensibility/debugger/evaluating-a-watch-window-expression.md)
- [Bir Watch ifadesini değerlendirme](../../extensibility/debugger/evaluating-a-watch-expression.md)
