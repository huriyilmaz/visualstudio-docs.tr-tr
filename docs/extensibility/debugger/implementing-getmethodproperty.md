---
title: GetMethodProperty'in Uygulanması | Microsoft Dokümanlar
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
ms.openlocfilehash: 252d09eee9c69ca75cb46d28dde807f2c500737f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738520"
---
# <a name="implement-getmethodproperty"></a>GetMethodProperty uygula
> [!IMPORTANT]
> Visual Studio 2015'te ifade değerlendiricilerinin bu şekilde uygulanması amortismana uymaktadır. CLR ifade değerlendiricilerinin uygulanması hakkında bilgi [için, bkz.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) [Managed expression evaluator sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

Visual Studio hata ayıklama motorunun (DE) [GetDebugProperty](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)çağırır, sırayla yığın çerçevesinde geçerli yöntem hakkında bilgi almak için [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) çağırır.

Bu uygulama `IDebugExpressionEvaluator::GetMethodProperty` aşağıdaki görevleri gerçekleştirir:

1. [GetContainerField'ı](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md)çağırır, [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) nesnesinde geçer. Sembol sağlayıcı (SP), belirtilen adresi içeren yöntemi temsil eden bir [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) döndürür.

2. [IDebugMethodField'ı](../../extensibility/debugger/reference/idebugmethodfield.md) `IDebugContainerField`.

3. [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) arabirimini uygulayan ve SP'den döndürülen `IDebugMethodField` nesneyi içeren bir sınıfı (bu örnekte çağrılır) `CFieldProperty` anında sunar.

4. `CFieldProperty` Nesneden `IDebugProperty2` arabirimi döndürür.

## <a name="managed-code"></a>Yönetilen kod
Bu `IDebugExpressionEvaluator::GetMethodProperty` örnek, yönetilen kodda bir uygulama gösterir.

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
Bu örnek, yönetilmeyen kod `IDebugExpressionEvaluator::GetMethodProperty` bir uygulama gösterir.

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
- [Yerel halktan örnek uygulama](../../extensibility/debugger/sample-implementation-of-locals.md)
