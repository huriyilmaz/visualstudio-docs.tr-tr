---
title: Yerel özellikleri alma | Microsoft Docs
description: Visual Studio, yönetilen ve yönetilmeyen koda yönelik bu örneklerle yerel özellikleri almak için enumchildren 'ı nasıl kullandığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- expression evaluation, getting local properties
- debugging [Debugging SDK], local properties
- expression evaluation, local properties
ms.assetid: 6c3a79e8-1ba1-4863-97c3-0216c3d9f092
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 85f23994292ad7089dbf3215e602347ad7891ddf35ddf933ce13989253150c2d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121361242"
---
# <a name="get-local-properties"></a>Yerel özellikleri al
> [!IMPORTANT]
> Visual Studio 2015 ' de, değerlendiricileri ifadesi uygulama yöntemi kullanım dışıdır. CLR Expression değerlendiricileri 'ı uygulama hakkında daha fazla bilgi için bkz. [clr Expression değerlendiricileri](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [yönetilen ifade değerlendirici örneği](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

Visual Studio, **yereller** penceresinde görüntülenecek tüm yereller için erişim sağlayan bir [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) nesnesi almak üzere [enumchildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) 'ı çağırır. Visual Studio, her bir yerel için görüntülenecek bilgileri almak için [ileri](../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md) ' yi çağırır. Bu örnekte, sınıfı `CEnumPropertyInfo` `IEnumDebugPropertyInfo2` arabirimini uygular.

Bu uygulama `IEnumDebugPropertyInfo2::Next` aşağıdaki görevleri gerçekleştirir:

1. Bilgilerin depolanacağı diziyi temizler.

2. Döndürülen [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) döndürülmek üzere, her bir yerel için [İleri](../../extensibility/debugger/reference/ienumdebugfields-next.md) çağrı yapılır. Bu sınıf örneği oluşturulurken [IEnumDebugFields](../../extensibility/debugger/reference/ienumdebugfields.md) nesnesi sağlandı `CEnumPropertyInfo` .

## <a name="managed-code"></a>Yönetilen kod
Bu örnek, `IEnumDebugPropertyInfo2::EnumChildren` Yönetilen koddaki yöntemin yerelleri için bir uygulamasını gösterir.

```csharp
namespace EEMC
{
    public class CEnumMethodField : IEnumDebugFields
    {
        public HRESULT Next(
                uint                  count,
                DEBUG_PROPERTY_INFO[] properties,
            out uint                  fetched)
        {
            if (count > properties.Length)
                throw new COMException();

            // Zero out the array.
            for (int i= 0; i < count; i++)
            {
                properties[i].bstrFullName = "";
                properties[i].bstrName = "";
                properties[i].bstrType = "";
                properties[i].bstrValue = "";
                properties[i].dwAttrib = 0;
                properties[i].dwFields = 0;
                properties[i].pProperty = null;
            }
            fetched = 0;

            // COM interop.
            HRESULT hr;
            uint innerFetched;
            IDebugField[] field = new IDebugField[1];

            while (fetched < count)
            {
                field[0] = null;
                innerFetched = 0;

                // Get next field.
                if (fetched < fieldCount)
                    hr = fields.Next(1, field, ref innerFetched);
                // No more fields.
                else return COM.S_FALSE;

                if (hr != COM.S_OK || innerFetched != 1 || field[0] == null)
                    throw new COMException("CEnumPropertyInfo.Next");

                // Get property from field.
                CFieldProperty fieldProperty =
                        new CFieldProperty(provider, address, binder, field[0]);

                DEBUG_PROPERTY_INFO[] property =
                        new DEBUG_PROPERTY_INFO[1];
                fieldProperty.GetPropertyInfo((uint) infoFlags, radix, 0, null, 0, property);
                properties[fetched++] = property[0];
            }
            return COM.S_OK;
        }
    }
}
```

## <a name="unmanaged-code"></a>Yönetilmeyen kod
 Bu örnek, `IEnumDebugPropertyInfo2::EnumChildren` yönetilmeyen koddaki yöntemin yerelleri için bir uygulamasını gösterir.

```cpp
STDMETHODIMP CEnumPropertyInfo::Next(
    in  ULONG                count,
    out DEBUG_PROPERTY_INFO* pelements,
    out ULONG*               pfetched )
{
    if (pfetched)
        *pfetched = 0;
    if (!pelements)
        return E_INVALIDARG;
    else
        memset( pelements, 0, count * sizeof(DEBUG_PROPERTY_INFO));

    HRESULT hr  = S_OK;
    ULONG   idx = 0;
    while (idx < count)
    {
        ULONG        fetchedFields;
        IDebugField* pfield;

        //get the next field
        hr = m_fields->Next( 1, &pfield, &fetchedFields );
        if (FAILED(hr))
            return hr;
        if (fetchedFields != 1)
            return E_FAIL;
        idx++;

        //create a CFieldProperty to retrieve the DEBUG_PROPERTY_INFO
        CFieldProperty* pproperty =
            new CFieldProperty( m_provider, m_address, m_binder, pfield );
        pfield->Release();
        if (!pproperty)
            return E_OUTOFMEMORY;

        hr = pproperty->Init();
        if (FAILED(hr))
        {
            pproperty->Release();
            return hr;
        }

        hr = pproperty->GetPropertyInfo( m_infoFlags,
                                         m_radix,
                                         0,
                                         NULL,
                                         0,
                                         pelements + idx - 1);
        pproperty->Release();
        if (FAILED(hr))
            return hr;
    }

    if (pfetched)
        *pfetched = idx;
    return hr;
}
```

## <a name="see-also"></a>Ayrıca bkz.
- [Yereller için örnek uygulama](../../extensibility/debugger/sample-implementation-of-locals.md)
- [Yereller numaralandırılıyor](../../extensibility/debugger/enumerating-locals.md)
