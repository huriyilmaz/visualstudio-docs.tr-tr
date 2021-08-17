---
title: GetMethodProperty uygulama | Microsoft Docs
description: Visual Studio hata ayıklama altyapısının getdebugözelliğini kullanarak yığın çerçevesindeki geçerli yöntem hakkında bilgi elde edin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- GetMethodProperty method
- IDebugExpressionEvaluator2 property
ms.assetid: 6305874f-a2c4-4432-834c-07530ea84bff
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 5e435ce59d13fcc9d60c61468520fddd8185fdd0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122089387"
---
# <a name="implement-getmethodproperty"></a>GetMethodProperty Uygula
> [!IMPORTANT]
> Visual Studio 2015 ' de, değerlendiricileri ifadesi uygulama yöntemi kullanım dışıdır. CLR Expression değerlendiricileri 'ı uygulama hakkında daha fazla bilgi için bkz. [clr Expression değerlendiricileri](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [yönetilen ifade değerlendirici örneği](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

Visual Studio, hata ayıklama altyapısının (de) [getdebugproperty](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)çağırır, bu da yığın çerçevesindeki geçerli yöntem hakkında bilgi almak için [getmethodproperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) öğesini çağırır.

Bu uygulama `IDebugExpressionEvaluator::GetMethodProperty` aşağıdaki görevleri gerçekleştirir:

1. [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) nesnesine geçirerek [GetContainerField](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md)öğesini çağırır. Sembol sağlayıcısı (SP), belirtilen adresi içeren yöntemi temsil eden bir [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) döndürüyor.

2. Öğesinden [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) 'ı alır `IDebugContainerField` .

3. `CFieldProperty` [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) ARABIRIMINI uygulayan ve `IDebugMethodField` SP 'den döndürülen nesneyi içeren bir sınıfı (Bu örnekte çağırılır) başlatır.

4. `IDebugProperty2`Nesneden arabirimi döndürür `CFieldProperty` .

## <a name="managed-code"></a>Yönetilen kod
Bu örnek, yönetilen kodda uygulamasının bir uygulamasını gösterir `IDebugExpressionEvaluator::GetMethodProperty` .

```csharp
namespace EEMC
{
    [GuidAttribute("462D4A3D-B257-4AEE-97CD-5918C7531757")]
    public class EEMCClass : IDebugExpressionEvaluator
    {
        public HRESULT GetMethodProperty(
                IDebugSymbolProvider symbolProvider,
                IDebugAddress        address,
                IDebugBinder         binder,
                int                  includeHiddenLocals,
            out IDebugProperty2      property)
        {
            IDebugContainerField containerField = null;
            IDebugMethodField methodField       = null;
            property = null;

            // Get the containing method field.
            symbolProvider.GetContainerField(address, out containerField);
            methodField = (IDebugMethodField) containerField;

            // Return the property of method field.
            property = new CFieldProperty(symbolProvider, address, binder, methodField);
            return COM.S_OK;
        }
    }
}
```

## <a name="unmanaged-code"></a>Yönetilmeyen kod
Bu örnek, yönetilmeyen kodda uygulamasının bir uygulamasını gösterir `IDebugExpressionEvaluator::GetMethodProperty` .

```
[CPP]
STDMETHODIMP CExpressionEvaluator::GetMethodProperty(
        in IDebugSymbolProvider *pprovider,
        in IDebugAddress        *paddress,
        in IDebugBinder         *pbinder,
        in BOOL                  includeHiddenLocals,
        out IDebugProperty2    **ppproperty
    )
{
    if (pprovider == NULL)
        return E_INVALIDARG;

    if (ppproperty == NULL)
        return E_INVALIDARG;
    else
        *ppproperty = 0;

    HRESULT hr;
    IDebugContainerField* pcontainer = NULL;

    hr = pprovider->GetContainerField(paddress, &pcontainer);
    if (FAILED(hr))
        return hr;

    IDebugMethodField*    pmethod    = NULL;
    hr = pcontainer->QueryInterface( IID_IDebugMethodField,
            reinterpret_cast<void**>(&pmethod));
    pcontainer->Release();
    if (FAILED(hr))
        return hr;

    CFieldProperty* pfieldProperty = new CFieldProperty( pprovider,
                                                         paddress,
                                                         pbinder,
                                                         pmethod );
    pmethod->Release();
    if (!pfieldProperty)
        return E_OUTOFMEMORY;

    hr = pfieldProperty->Init();
    if (FAILED(hr))
    {
        pfieldProperty->Release();
        return hr;
    }

    hr = pfieldProperty->QueryInterface( IID_IDebugProperty2,
            reinterpret_cast<void**>(ppproperty));
    pfieldProperty->Release();

    return hr;
}
```

## <a name="see-also"></a>Ayrıca bkz.
- [Yereller için örnek uygulama](../../extensibility/debugger/sample-implementation-of-locals.md)
