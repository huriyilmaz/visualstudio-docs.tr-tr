---
title: Ifade değerlendirmesinin örnek uygulama | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80713108"
---
# <a name="sample-implementation-of-expression-evaluation"></a>İfade değerlendirmesinin örnek uygulama
> [!IMPORTANT]
> Visual Studio 2015 ' de, değerlendiricileri ifadesi uygulama yöntemi kullanım dışıdır. CLR Expression değerlendiricileri 'ı uygulama hakkında daha fazla bilgi için bkz. [clr Expression değerlendiricileri](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [yönetilen ifade değerlendirici örneği](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Bir **Gözcü** penceresi ifadesi Için, Visual Studio bir [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) nesnesi üretmek için [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) 'i çağırır. `IDebugExpressionContext2::ParseText`bir ifade değerlendirici (EE) oluşturur ve bir [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) nesnesi almak için [ayrıştırmayı](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) çağırır.

 `IDebugExpressionEvaluator::Parse`Aşağıdaki görevleri gerçekleştirir:

1. [Yalnızca C++] Hataları bulmak için ifadeyi ayrıştırır.

2. Arabirimini çalıştıran bir sınıfı ( `CParsedExpression` Bu örnekte çağırılır) başlatır `IDebugParsedExpression` ve ayrıştırılacak ifade sınıfta depolar.

3. `IDebugParsedExpression`Nesneden arabirimi döndürür `CParsedExpression` .

> [!NOTE]
> Aşağıdaki örneklerde ve MyCEE örneğinde, ifade değerlendirici, ayrıştırmayı değerlendirmeden ayıramaz.

## <a name="managed-code"></a>Yönetilen kod
 Aşağıdaki kod, yönetilen kodda uygulamasının bir uygulamasını gösterir `IDebugExpressionEvaluator::Parse` . Bu yöntemin bu sürümü, ayrıştırma kodu olarak [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) için ayrıştırma için de aynı anda değerlendirilir (bkz. [bir gözcü ifadesini değerlendir](../../extensibility/debugger/evaluating-a-watch-expression.md)).

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
Aşağıdaki kod, yönetilmeyen kodda bir uygulamasıdır `IDebugExpressionEvaluator::Parse` . Bu yöntem, `Parse` ifadeyi ayrıştırmak ve hataları denetlemek için bir yardımcı işlevi çağırır, ancak bu yöntem elde edilen değeri yoksayar. Biçimsel değerlendirme, ifadenin değerlendirildiği sırada ayrıştırıldığında (bkz. [bir gözcü Ifadesini değerlendir](../../extensibility/debugger/evaluating-a-watch-expression.md)) [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) olarak ertelenir.

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
- [izleme penceresi ifadesini değerlendir](../../extensibility/debugger/evaluating-a-watch-window-expression.md)
- [Bir gözcü ifadesini değerlendir](../../extensibility/debugger/evaluating-a-watch-expression.md)
