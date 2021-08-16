---
title: Yereller numaralandırılıyor | Microsoft Docs
description: 'Visual Studio IDebugProperty2:: enumchildren kullanarak yereller penceresini nasıl doldururun ayrıntıları hakkında bilgi edinin.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], enumerating locals
- expression evaluation, enumerating locals
ms.assetid: 254a88e7-d3a7-447a-bd0c-8985e73d85cf
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 01392932831ab7ba5fec867a427b4a2c8868070abdda93de53593e9c3f27beb2
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121378226"
---
# <a name="enumerate-locals"></a>Yerelleri listeleme
> [!IMPORTANT]
> Visual Studio 2015 ' de, değerlendiricileri ifadesi uygulama yöntemi kullanım dışıdır. CLR Expression değerlendiricileri 'ı uygulama hakkında daha fazla bilgi için bkz. [clr Expression değerlendiricileri](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [yönetilen ifade değerlendirici örneği](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

**yereller** penceresini doldurmak için Visual Studio, [getmethodproperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) 'den döndürülen [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) nesnesinde [enumchildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) 'ı çağırır (bkz. [getmethodproperty uygulama](../../extensibility/debugger/implementing-getmethodproperty.md)). `IDebugProperty2::EnumChildren` bir [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) nesnesi döndürür.

Uygulama `IDebugProperty2::EnumChildren` aşağıdaki görevleri gerçekleştirir:

1. Bunun bir yöntemi temsil eder.

2. , `guidFilter` [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) nesnesinde hangi yöntemin çağrılacağını belirleyen bağımsız değişkenini kullanır. `guidFilter`Eşittir ise:

    1. `guidFilterLocals`, bir [IEnumDebugFields](../../extensibility/debugger/reference/ienumdebugfields.md) nesnesi almak Için [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) öğesini çağırın.

    2. `guidFilterArgs`, bir nesne almak için [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) çağırın `IEnumDebugFields` .

    3. `guidFilterLocalsPlusArgs`, ve sonuçlarını birleştiren bir sabit listesini sentezleştirme `IDebugMethodField::EnumLocals` `IDebugMethodField::EnumArguments` . Bu birleştirbir sınıf tarafından temsil edilir `CEnumMethodField` .

3. `CEnumPropertyInfo` `IEnumDebugPropertyInfo2` Arabirimini uygulayan ve nesnesini içeren bir sınıfı (Bu örnekte çağırılır) başlatır `IEnumDebugFields` .

4. `IEnumDebugProperty2Info2`Nesneden arabirimi döndürür `CEnumPropertyInfo` .

## <a name="managed-code"></a>Yönetilen kod
Bu örnek, yönetilen kodda uygulamasının bir uygulamasını gösterir `IDebugProperty2::EnumChildren` .

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
 Bu örnek, yönetilmeyen kodda uygulamasının bir uygulamasını gösterir `IDebugProperty2::EnumChildren` .

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
- [Yereller için örnek uygulama](../../extensibility/debugger/sample-implementation-of-locals.md)
- [GetMethodProperty Uygula](../../extensibility/debugger/implementing-getmethodproperty.md)
- [Değerlendirme bağlamı](../../extensibility/debugger/evaluation-context.md)
