---
title: Yerel Özellikleri Alma | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, getting local properties
- debugging [Debugging SDK], local properties
- expression evaluation, local properties
ms.assetid: 6c3a79e8-1ba1-4863-97c3-0216c3d9f092
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e084f28257ddede388468f36e1635e87c8f65961
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738623"
---
# <a name="get-local-properties"></a>Yerel özellikleri alın
> [!IMPORTANT]
> Visual Studio 2015'te ifade değerlendiricilerinin bu şekilde uygulanması amortismana uymaktadır. CLR ifade değerlendiricilerinin uygulanması hakkında bilgi [için, bkz.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) [Managed expression evaluator sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

Visual Studio, [EnumChildren'ı](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) **Yerel ler** penceresinde görüntülenecek tüm yerel halka erişim sağlayan bir [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) nesnesi edinmeye çağırır. Visual Studio daha sonra her yerel için görüntülenecek bilgileri almak için [Next'i](../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md) arar. Bu örnekte, `CEnumPropertyInfo` sınıf `IEnumDebugPropertyInfo2` arabirimi uygular.

Bu uygulama `IEnumDebugPropertyInfo2::Next` aşağıdaki görevleri gerçekleştirir:

1. Bilgilerin depolanacak olduğu diziyi temizler.

2. [Döndürülecek](../../extensibility/debugger/reference/ienumdebugfields-next.md) dizide döndürülen [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) depolayan her yerel için Sonraki'yi arar. Bu `CEnumPropertyInfo` sınıf anında yapıldığında [IEnumDebugFields](../../extensibility/debugger/reference/ienumdebugfields.md) nesnesi sağlandı.

## <a name="managed-code"></a>Yönetilen kod
Bu örnek, yönetilen `IEnumDebugPropertyInfo2::EnumChildren` kodda bir yöntemin yerel için bir uygulama gösterir.

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
 Bu örnek, yönetilen `IEnumDebugPropertyInfo2::EnumChildren` olmayan kodda bir yöntemin yerel için bir uygulama gösterir.

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
- [Yerel halktan örnek uygulama](../../extensibility/debugger/sample-implementation-of-locals.md)
- [Yerel halkları sayısallaştırıyor](../../extensibility/debugger/enumerating-locals.md)
