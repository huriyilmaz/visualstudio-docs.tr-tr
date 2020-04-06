---
title: Yerel Leri Sayısala | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], enumerating locals
- expression evaluation, enumerating locals
ms.assetid: 254a88e7-d3a7-447a-bd0c-8985e73d85cf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 540c062d3d4f73a5468b39629fc277e6fd10df7d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738865"
---
# <a name="enumerate-locals"></a>Yerel leri sayısal
> [!IMPORTANT]
> Visual Studio 2015'te ifade değerlendiricilerinin bu şekilde uygulanması amortismana uymaktadır. CLR ifade değerlendiricilerinin uygulanması hakkında bilgi [için, bkz.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) [Managed expression evaluator sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

Visual Studio **Yerel ler** penceresini doldurmaya hazır olduğunda, [GetMethodProperty'den](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) döndürülen [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) nesnesindeki [EnumChildren'ı](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) çağırır (bkz. [GetMethodProperty uygulama).](../../extensibility/debugger/implementing-getmethodproperty.md) `IDebugProperty2::EnumChildren`bir [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) nesnesi döndürür.

Uygulama `IDebugProperty2::EnumChildren` aşağıdaki görevleri gerçekleştirir:

1. Bunun bir yöntemi temsil ettiğini sağlar.

2. `guidFilter` [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) nesnesine hangi yöntemi çağıracaklarını belirlemek için bağımsız değişkeni kullanır. Eşitse: `guidFilter`

    1. `guidFilterLocals`, [Bir IEnumDebugFields](../../extensibility/debugger/reference/ienumdebugfields.md) nesnesi elde etmek için [EnumLocals'ı](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) arayın.

    2. `guidFilterArgs`, Bir `IEnumDebugFields` nesne elde etmek için [EnumArguments'ı](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) arayın.

    3. `guidFilterLocalsPlusArgs`, sonuçları birleştiren bir numaralandırma `IDebugMethodField::EnumLocals` sentezlemek ve `IDebugMethodField::EnumArguments`. Bu sentez sınıf `CEnumMethodField`tarafından temsil edilir.

3. Arabirimi uygulayan ve `CEnumPropertyInfo` `IEnumDebugFields` nesneyi içeren bir sınıfı (bu örnekte çağrılır) anında uygular. `IEnumDebugPropertyInfo2`

4. `CEnumPropertyInfo` Nesneden `IEnumDebugProperty2Info2` arabirimi döndürür.

## <a name="managed-code"></a>Yönetilen kod
Bu `IDebugProperty2::EnumChildren` örnek, yönetilen kodda bir uygulama gösterir.

```csharp
namespace EEMC
{
    public class CFieldProperty : IDebugProperty2
    {
        public HRESULT EnumChildren (
                uint                    dwFields,
                uint                    radix,
            ref Guid                    guidFilter,
                ulong                   attribFilter,
                string                  nameFilter,
                uint                    timeout,
            out IEnumDebugPropertyInfo2 properties)
        {
            properties = null;
            IEnumDebugFields fields = null;

            // If this field is a method...
            if (0 != ((uint) fieldKind & (uint) FIELD_KIND.FIELD_TYPE_METHOD))
            {
                IDebugMethodField methodField = (IDebugMethodField) field;

                // Enumerate parameters.
                if (guidFilter == FilterGuids.guidFilterArgs)
                {
                    methodField.EnumParameters(out fields);
                }
                // Enumerate local variables.
                else if (guidFilter == FilterGuids.guidFilterLocals)
                {
                    methodField.EnumLocals(address, out fields);
                }
                // Enumerate all local variables, including invisible compiler temps.
                else if (guidFilter == FilterGuids.guidFilterAllLocals)
                {
                    methodField.EnumAllLocals(address, out fields);
                }
                // Enumerate "this", if any, and all parameters and local variables.
                else if (guidFilter == FilterGuids.guidFilterLocalsPlusArgs)
                {
                    IDebugClassField fieldThis  = null;
                    IEnumDebugFields parameters = null;
                    IEnumDebugFields locals     = null;

                    methodField.GetThis(out fieldThis);
                    methodField.EnumParameters(out parameters);
                    methodField.EnumLocals(address, out locals);

                    CEnumMethodField enumMethodField =
                        new CEnumMethodField(fieldThis, parameters, locals);
                    fields = (IEnumDebugFields) enumMethodField;
                }
                // Enumerate only "this".
                else if (guidFilter == FilterGuids.guidFilterThis)
                {
                    IDebugClassField fieldThis = null;
                    methodField.GetThis(out fieldThis);

                    CEnumMethodField enumMethodField =
                        new CEnumMethodField(fieldThis, null, null);
                    fields = (IEnumDebugFields) enumMethodField;
                }
                else throw new COMException();// E_FAIL
            }
            // Wrap a property enumerator around the field enumerator.
            CEnumPropertyInfo propertiesInfo =
                new CEnumPropertyInfo(provider, address, binder, radix, fields,
                (DEBUGPROP_INFO_FLAGS) dwFields);

            properties = (IEnumDebugPropertyInfo2) propertiesInfo;
            return COM.S_OK;
        }
    }
}
```

## <a name="unmanaged-code"></a>Yönetilmeyen kod
 Bu örnek, yönetilmeyen kod `IDebugProperty2::EnumChildren` bir uygulama gösterir.

```cpp
STDMETHODIMP CFieldProperty::EnumChildren(
        in DEBUGPROP_INFO_FLAGS        infoFlags,
        in DWORD                       radix,
        in REFGUID                     guidFilter,
        in DBG_ATTRIB_FLAGS            attribFilter,
        in LPCOLESTR                   pszNameFilter,
        in DWORD                       timeout,
        out IEnumDebugPropertyInfo2 ** ppchildren )
{
    if (ppchildren == NULL)
        return E_INVALIDARG;
    else
        *ppchildren = 0;

    //get enumeration
    HRESULT hr;
    IEnumDebugFields*     pfields    = NULL;

    if (m_fieldKind & FIELD_TYPE_METHOD)
    {
        //-----------------------------------------------------
        // A Method

        IDebugMethodField*  pmethod    = NULL;

        //enumerate the requested properties
        hr = m_field->QueryInterface( IID_IDebugMethodField,
            reinterpret_cast<void**>(&pmethod) );
        if (FAILED(hr))
            return hr;

        if (guidFilter == guidFilterArgs)
        {
            hr = pmethod->EnumParameters( &pfields );
        }
        else if (guidFilter == guidFilterLocals)
        {
            hr = pmethod->EnumLocals( m_address, &pfields );
        }
        else if (guidFilter == guidFilterAllLocals)
        {
            hr = pmethod->EnumAllLocals( m_address, &pfields );
        }
        else if (guidFilter == guidFilterLocalsPlusArgs)
        {
            //we create a special enumerator for this
            IDebugClassField* pfieldThis  = NULL;
            IEnumDebugFields* pparameters = NULL;
            IEnumDebugFields* plocals     = NULL;

            pmethod->GetThis( &pfieldThis );
            pmethod->EnumParameters( &pparameters );
            pmethod->EnumLocals( m_address, &plocals );

            CEnumMethodField* penumMethodField =
                new CEnumMethodField( pfieldThis, pparameters, plocals );
            if (pfieldThis != NULL)
                pfieldThis->Release();
            if (pparameters != NULL)
                pparameters->Release();
            if (plocals != NULL)
                plocals->Release();
            if (!penumMethodField)
            {
                hr = E_OUTOFMEMORY;
            }
            else
            {
                hr = penumMethodField->QueryInterface( IID_IEnumDebugFields,
                        reinterpret_cast<void**>(&pfields) );
                penumMethodField->Release();
            }
        }
        else if (guidFilter == guidFilterThis )
        {
            IDebugClassField* pfieldThis = NULL;

            hr = pmethod->GetThis( &pfieldThis );
            if (SUCCEEDED(hr))
            {
                CEnumMethodField* penumMethodField =
                    new CEnumMethodField( pfieldThis, NULL, NULL );
                pfieldThis->Release();
                if (!penumMethodField)
                {
                    hr = E_OUTOFMEMORY;
                }
                else
                {
                    hr = penumMethodField->QueryInterface( IID_IEnumDebugFields,
                        reinterpret_cast<void**>(&pfields) );
                    penumMethodField->Release();
                }
            }
        }
        else
        {
            hr = E_FAIL;
        }

        pmethod->Release();
        if (hr != S_OK)
            return hr;
    }

    //create a property info enumeration around the field enumerator
    CEnumPropertyInfo* pproperties =
        new CEnumPropertyInfo( m_provider, m_address, m_binder,
                               radix, pfields, infoFlags );
    if (pfields != NULL)
        pfields->Release();
    if (pproperties == NULL)
        return E_OUTOFMEMORY;

    hr = pproperties->QueryInterface( IID_IEnumDebugPropertyInfo2,
        reinterpret_cast<void**>(ppchildren) );
    pproperties->Release();

    return hr;
}
```

## <a name="see-also"></a>Ayrıca bkz.
- [Yerel halktan örnek uygulama](../../extensibility/debugger/sample-implementation-of-locals.md)
- [GetMethodProperty uygula](../../extensibility/debugger/implementing-getmethodproperty.md)
- [Değerlendirme bağlamı](../../extensibility/debugger/evaluation-context.md)
