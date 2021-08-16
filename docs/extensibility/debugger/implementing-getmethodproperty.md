---
title: GetMethodProperty | Microsoft Docs
description: Hata ayıklama Visual Studio GetDebugProperty kullanarak yığın çerçevesindeki geçerli yöntem hakkında nasıl bilgi edinir?
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
ms.openlocfilehash: 17f846e9dcb70300b27aa7248c4c4c2783b02887f6ba9d6071f636cbf48b78b0
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121361112"
---
# <a name="implement-getmethodproperty"></a>GetMethodProperty uygulama
> [!IMPORTANT]
> 2015 Visual Studio de ifade değerlendiricilerini uygulamanın bu yolu kullanım dışıdır. CLR ifade değerlendiricilerini uygulama hakkında bilgi için bkz. [CLR ifade değerlendiricileri ve](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) [Yönetilen ifade değerlendirici örneği.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

Visual Studio, hata ayıklama altyapısının (DE) [GetDebugProperty'sini](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)çağırarak yığın çerçevesindeki geçerli yöntem hakkında bilgi almak için [GetMethodProperty'ye](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) çağrılar.

Bu uygulaması `IDebugExpressionEvaluator::GetMethodProperty` aşağıdaki görevleri gerçekleştirir:

1. [GetContainerField'i](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md)çağırarak [IDebugAddress nesnesini](../../extensibility/debugger/reference/idebugaddress.md) iletir. Sembol sağlayıcısı (SP), belirtilen adresi içeren [yöntemi temsil eden bir IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) döndürür.

2. [IDebugMethodField'i 'den](../../extensibility/debugger/reference/idebugmethodfield.md) elde `IDebugContainerField` ediyor.

3. `CFieldProperty` [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) arabirimini uygulayan ve SP'den döndürülen nesneyi içeren bir sınıf (bu örnekte çağrılır) `IDebugMethodField` örneği oluşturur.

4. nesnesinden `IDebugProperty2` arabirimini `CFieldProperty` döndürür.

## <a name="managed-code"></a>Yönetilen kod
Bu örnek, yönetilen kodda `IDebugExpressionEvaluator::GetMethodProperty` uygulamasının nasıl olduğunu gösterir.

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

## <a name="unmanaged-code"></a>Unmanaged code
Bu örnekte, bir `IDebugExpressionEvaluator::GetMethodProperty` uygulaması, unmanaged code içinde gösterir.

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
- [Yerellerin örnek uygulaması](../../extensibility/debugger/sample-implementation-of-locals.md)
