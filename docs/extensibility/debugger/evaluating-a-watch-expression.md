---
title: Bir Saat İfadesini Değerlendirme | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, watch expressions
- watch expressions
ms.assetid: 8317cd52-6fea-4e8f-a739-774dc06bd44b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9a239e430338e88a0be4bc35ad1c357925f7d8f5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738859"
---
# <a name="evaluate-a-watch-expression"></a>Saat ifadesini değerlendirme
> [!IMPORTANT]
> Visual Studio 2015'te ifade değerlendiricilerinin bu şekilde uygulanması amortismana uymaktadır. CLR ifade değerlendiricilerinin uygulanması hakkında bilgi [için, bkz.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) [Managed expression evaluator sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

Visual Studio bir saat ifadesinin değerini görüntülemeye hazır olduğunda, [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)çağırır , sırayla [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)çağırır. Bu işlem, ifadenin değerini ve türünü içeren bir [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) nesnesi üretir.

Bu uygulamada `IDebugParsedExpression::EvaluateSync`, ifade ayrıştırılır ve aynı anda değerlendirilir. Bu uygulama aşağıdaki görevleri gerçekleştirir:

1. Değeri ve türünü tutan genel bir nesne üretmek için ifadeyi parslar ve değerlendirir. C#'da bu, C++'da bir `object` while olarak temsil `VARIANT`edilir, bu bir . olarak temsil edilir

2. Arabirimi uygulayan bir sınıfı `CValueProperty` (bu örnekte çağrıldı) anında uygular ve sınıfta döndürülecek değeri depolar. `IDebugProperty2`

3. `CValueProperty` Nesneden `IDebugProperty2` arabirimi döndürür.

## <a name="managed-code"></a>Yönetilen kod
Bu, yönetilen kodun `IDebugParsedExpression::EvaluateSync` bir uygulamasıdır. Yardımcı yöntem `Tokenize` ifadeyi ayrışdırıcı bir ağaca ayrışdırır. Yardımcı işlevi `EvalToken` belirteci bir değere dönüştürür. Yardımcı işlev, `FindTerm` bir değeri temsil eden her düğüm için `EvalToken` çağrıda bulunarak ve ifadede herhangi bir işlem (ekleme veya çıkarma) uygulayarak ayrıştırma ağacından özyinelemeli olarak geçer.

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

## <a name="unmanaged-code"></a>Yönetilmeyen kod
Bu, yönetilmeyen `IDebugParsedExpression::EvaluateSync` kodun bir uygulamasıdır. Yardımcı işlev `Evaluate` ayrışır ve ifadedeğerlendirir, bir `VARIANT` tutarak elde edilen değeri döndürdü. Yardımcı işlevi `VariantValueToProperty` bir `VARIANT` `CValueProperty` nesneye bir araya getirir.

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
- [İfade değerlendirmesinin örnek uygulanması](../../extensibility/debugger/sample-implementation-of-expression-evaluation.md)
