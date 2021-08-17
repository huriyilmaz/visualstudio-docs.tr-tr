---
title: Yerel Özellikler | Microsoft Docs
description: Yönetilen Visual Studio ve yönetilemeyen kod örnekleriyle yerel özellikleri almak için EnumChildren'ı nasıl kullandığını öğrenin.
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
ms.openlocfilehash: cd174da02a52a86a29494f4edeaf13714b2d5758
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122057869"
---
# <a name="get-local-properties"></a>Yerel özellikleri al
> [!IMPORTANT]
> 2015 Visual Studio de ifade değerlendiricilerini uygulamanın bu yolu kullanım dışıdır. CLR ifade değerlendiricilerini uygulama hakkında bilgi için bkz. [CLR ifade değerlendiricileri ve](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) [Yönetilen ifade değerlendirici örneği.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

Visual Studio yereller penceresinde görüntülenecek tüm yerellere erişim sağlayan [bir IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) nesnesi almak için [EnumChildren'i](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) çağırıyor.  Visual Studio her yerel [için görüntülenecek](../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md) bilgileri almak için Sonraki'ne çağrır. Bu örnekte, sınıfı `CEnumPropertyInfo` arabirimini `IEnumDebugPropertyInfo2` uygulayan.

Bu uygulaması `IEnumDebugPropertyInfo2::Next` aşağıdaki görevleri gerçekleştirir:

1. Bilgilerin depolandığı diziyi temizler.

2. Her [yerel](../../extensibility/debugger/reference/ienumdebugfields-next.md) için Sonraki'i çağırarak döndürülen [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) döndürülen dizide depolar. Bu [sınıf örneği yken IEnumDebugFields](../../extensibility/debugger/reference/ienumdebugfields.md) `CEnumPropertyInfo` nesnesi sağlandı.

## <a name="managed-code"></a>Yönetilen kod
Bu örnekte, yönetilen `IEnumDebugPropertyInfo2::EnumChildren` kodda bir yöntemin yerelleri için uygulaması gösterir.

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

## <a name="unmanaged-code"></a>Unmanaged code
 Bu örnekte, bir `IEnumDebugPropertyInfo2::EnumChildren` yöntemin yerelleri için bir uygulaması, yönetimsiz kodda gösterir.

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
- [Yerellerin örnek uygulaması](../../extensibility/debugger/sample-implementation-of-locals.md)
- [Yerelleri numaralar](../../extensibility/debugger/enumerating-locals.md)
