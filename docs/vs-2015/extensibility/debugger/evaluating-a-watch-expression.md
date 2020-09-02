---
title: Bir gözcü Ifadesini değerlendirme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, watch expressions
- watch expressions
ms.assetid: 8317cd52-6fea-4e8f-a739-774dc06bd44b
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fd33a7c225e0cdc14ac3f1af9f4c78a7c1459615
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64784441"
---
# <a name="evaluating-a-watch-expression"></a>Bir Gözcü İfadesini Değerlendirme
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> Visual Studio 2015 ' de, değerlendiricileri ifadesi uygulama yöntemi kullanım dışıdır. CLR Expression değerlendiricileri 'ı uygulama hakkında daha fazla bilgi için lütfen bkz. [clr Expression değerlendiricileri](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [yönetilen ifade değerlendirici örneği](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Visual Studio, bir Gözcü ifadesinin değerini görüntülemeye hazırsa, [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) çağırır ve bu, [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)öğesini çağırır. Bu, ifadenin değerini ve türünü içeren bir [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) nesnesi oluşturur.  
  
 Bu uygulamada `IDebugParsedExpression::EvaluateSync` , ifade ayrıştırılıp aynı anda değerlendirilir. Bu uygulama aşağıdaki görevleri gerçekleştirir:  
  
1. Değeri ve türünü tutan genel bir nesne oluşturmak için ifadeyi ayrıştırır ve değerlendirir. C# dilinde bu, C++ ' da olduğu gibi temsil edilir `object` `VARIANT` .  
  
2. Arabirimini uygulayan bir sınıf ( `CValueProperty` Bu örnekte çağırılır) başlatır `IDebugProperty2` ve döndürülecek değer sınıfında depolar.  
  
3. `IDebugProperty2`Nesneden arabirimi döndürür `CValueProperty` .  
  
## <a name="managed-code"></a>Yönetilen kod  
 Bu, yönetilen kodun bir uygulamasıdır `IDebugParsedExpression::EvaluateSync` . Yardımcı yöntemi, `Tokenize` ifadeyi bir ayrıştırma ağacı olarak ayrıştırır. Yardımcı işlevi, `EvalToken` belirteci bir değere dönüştürür. Yardımcı işlevi, `FindTerm` `EvalToken` bir değeri temsil eden her düğüm için çağıran ve ifadeye herhangi bir işlem (ekleme veya çıkarma) uygulayan ayrıştırma ağacını yinelemeli olarak inceler.  
  
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
  
## <a name="unmanaged-code"></a>Yönetilmeyen Kod  
 Bu, yönetilmeyen kodun bir uygulamasıdır `IDebugParsedExpression::EvaluateSync` . Yardımcı işlevi, `Evaluate` ifadeyi ayrıştırır ve değerlendirir ve `VARIANT` sonuçta elde edilen değeri tutan bir değer döndürür. Yardımcı işlevi `VariantValueToProperty` , öğesini `VARIANT` bir nesnesine paketler `CValueProperty` .  
  
```  
[C++]  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Gözcü penceresi Ifadesini değerlendirme](../../extensibility/debugger/evaluating-a-watch-window-expression.md)   
 [Örnek İfade Değerlendirme Uygulaması](../../extensibility/debugger/sample-implementation-of-expression-evaluation.md)
