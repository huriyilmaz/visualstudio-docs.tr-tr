---
title: İzleme İfadesi değerlendirme | Microsoft Docs
description: Bir Visual Studio değerini görüntülemeye hazır olduğunda EvaluateSync'i nasıl kullandığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, watch expressions
- watch expressions
ms.assetid: 8317cd52-6fea-4e8f-a739-774dc06bd44b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: c5f6978e6ba45c42777533d0fdd288f3ecc55f2dd8dfd26558f1a106489bf376
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121342979"
---
# <a name="evaluate-a-watch-expression"></a>İzleme ifadesini değerlendirme
> [!IMPORTANT]
> 2015 Visual Studio de ifade değerlendiricilerini uygulamanın bu yolu kullanım dışıdır. CLR ifade değerlendiricilerini uygulama hakkında bilgi için bkz. [CLR ifade değerlendiricileri ve](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) [Yönetilen ifade değerlendirici örneği.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

Bir Visual Studio izleme ifadesinin değerini görüntülemeye hazır olduğunda [EvaluateSync'i](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)çağırarak [EvaluateSync'i çağırtır.](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) Bu işlem, ifadenin değerini ve türünü içeren bir [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) nesnesi oluşturur.

bu `IDebugParsedExpression::EvaluateSync` uygulamasında, ifadesi ayrıştırıldı ve aynı anda değerlendirildi. Bu uygulama aşağıdaki görevleri gerçekleştirir:

1. Değeri ve türünü tutan genel bir nesne üretmek için ifadeyi ayrıştırıyor ve değerlendirir. C# içinde bu, C++ içinde bir while olarak `object` temsil edilen bir olarak temsil `VARIANT` edildi.

2. Arabirimi uygulayan ve döndürülen değeri sınıfında depolar bir sınıf örneği `CValueProperty` `IDebugProperty2` (bu örnekte çağrılır).

3. nesnesinden `IDebugProperty2` arabirimini `CValueProperty` döndürür.

## <a name="managed-code"></a>Yönetilen kod
Bu, yönetilen kodda `IDebugParsedExpression::EvaluateSync` uygulamasının bir uygulamasıdır. Yardımcı yöntemi, `Tokenize` ifadeyi ayrıştırma ağacına ayrıştırıyor. Yardımcı işlevi `EvalToken` belirteci bir değere dönüştürür. Yardımcı işlevi, bir değeri temsil eden her düğümü çağırarak ve ifadede herhangi bir işlemi (toplama veya çıkarma) uygulayarak ayrıştırma ağacında `FindTerm` `EvalToken` özyinelemeli olarak çapraz geçişler sağlar.

```csharp
namespace EEMC
{
    public class CParsedExpression : IDebugParsedExpression
    {
        public HRESULT EvaluateSync(
            uint evalFlags,
            uint timeout,
            IDebugSymbolProvider provider,
            IDebugAddress address,
            IDebugBinder binder,
            string resultType,
            out IDebugProperty2 result)
        {
            HRESULT retval = COM.S_OK;
            this.evalFlags = evalFlags;
            this.timeout = timeout;
            this.provider = provider;
            this.address = address;
            this.binder = binder;
            this.resultType = resultType;

            try
            {
                IDebugField field = null;
                // Tokenize, then parse.
                tokens = Tokenize(expression);
                result = new CValueProperty(
                        expression,
                        (int) FindTerm(EvalToken(tokens[0], out field),1),
                        field,
                        binder);
            }
            catch (ParseException)
            {
                result = new CValueProperty(expression, "Huh?");
                retval = COM.E_INVALIDARG;
            }
            return retval;
        }
    }
}
```

## <a name="unmanaged-code"></a>Unmanaged code
Bu, `IDebugParsedExpression::EvaluateSync` unmanaged code içinde uygulamasının bir uygulamasıdır. Yardımcı işlevi, `Evaluate` elde edilen değeri tutan bir döndürerek ifadeyi `VARIANT` ayrıştırarak değerlendirir. Yardımcı işlevi, `VariantValueToProperty` nesnesini bir `VARIANT` nesnesine `CValueProperty` paketler.

```cpp
STDMETHODIMP CParsedExpression::EvaluateSync(
    in  DWORD                 evalFlags,
    in  DWORD                 dwTimeout,
    in  IDebugSymbolProvider* pprovider,
    in  IDebugAddress*        paddress,
    in  IDebugBinder*         pbinder,
    in  BSTR                  bstrResultType,
    out IDebugProperty2**     ppproperty )
{
    // dwTimeout parameter is ignored in this implementation.
    if (pprovider == NULL)
        return E_INVALIDARG;

    if (paddress == NULL)
        return E_INVALIDARG;

    if (pbinder == NULL)
        return E_INVALIDARG;

    if (ppproperty == NULL)
        return E_INVALIDARG;
    else
        *ppproperty = 0;

    HRESULT hr;
    VARIANT value;
    BSTR    bstrErrorMessage = NULL;
    hr = ::Evaluate( pprovider,
                     paddress,
                     pbinder,
                     m_expr,
                     &bstrErrorMessage,
                     &value );
    if (hr != S_OK)
    {
        if (bstrErrorMessage == NULL)
            return hr;

        //we can display better messages ourselves.
        HRESULT hrLocal = S_OK;
        VARIANT varType;
        VARIANT varErrorMessage;

        VariantInit( &varType );
        VariantInit( &varErrorMessage );
        varErrorMessage.vt      = VT_BSTR;
        varErrorMessage.bstrVal = bstrErrorMessage;

        CValueProperty* valueProperty = new CValueProperty();
        if (valueProperty != NULL)
        {
            hrLocal = valueProperty->Init(m_expr, varType, varErrorMessage);
            if (SUCCEEDED(hrLocal))
            {
                hrLocal = valueProperty->QueryInterface( IID_IDebugProperty2,
                        reinterpret_cast<void**>(ppproperty) );
            }
        }

        VariantClear(&varType);
        VariantClear(&varErrorMessage); //frees BSTR
        if (!valueProperty)
            return hr;
        valueProperty->Release();
        if (FAILED(hrLocal))
            return hr;
    }
    else
    {
        if (bstrErrorMessage != NULL)
            SysFreeString(bstrErrorMessage);

        hr = VariantValueToProperty( pprovider,
                                     paddress,
                                     pbinder,
                                     m_radix,
                                     m_expr,
                                     value,
                                     ppproperty );
        VariantClear(&value);
        if (FAILED(hr))
            return hr;
    }

    return S_OK;
}
```

## <a name="see-also"></a>Ayrıca bkz.
- [Saat penceresi ifadesini değerlendirme](../../extensibility/debugger/evaluating-a-watch-window-expression.md)
- [İfade değerlendirmesinin örnek uygulaması](../../extensibility/debugger/sample-implementation-of-expression-evaluation.md)
