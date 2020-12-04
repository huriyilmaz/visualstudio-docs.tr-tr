---
title: GetMethodProperty uygulama | Microsoft Docs
description: Hata ayıklama altyapısının GetDebugProperty 'sini kullanarak Visual Studio 'Nun yığın çerçevesindeki geçerli yöntem hakkında bilgi edindiğini öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- GetMethodProperty method
- IDebugExpressionEvaluator2 property
ms.assetid: 6305874f-a2c4-4432-834c-07530ea84bff
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6028bd92611e7d5dc8a7e05fcf98bc360de7e9ed
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2020
ms.locfileid: "96559920"
---
# <a name="implement-getmethodproperty"></a>GetMethodProperty Uygula
> [!IMPORTANT]
> Visual Studio 2015 ' de, değerlendiricileri ifadesi uygulama yöntemi kullanım dışıdır. CLR Expression değerlendiricileri 'ı uygulama hakkında daha fazla bilgi için bkz. [clr Expression değerlendiricileri](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [yönetilen ifade değerlendirici örneği](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

Visual Studio, hata ayıklama altyapısının (DE) [GetDebugProperty](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)öğesini çağırır, bu da yığın çerçevesindeki geçerli yöntem hakkında bilgi almak Için [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) öğesini çağırır.

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
