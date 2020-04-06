---
title: IDebugSymbolProvider | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider
helpviewer_keywords:
- IDebugSymbolProvider interface
ms.assetid: df5f095f-1dee-46f9-84cf-92417c71d5fb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 11e180288a9312d9af5a3d3b1bd63d8f2266f581
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719177"
---
# <a name="idebugsymbolprovider"></a>IDebugSymbolProvider
Bu arabirim, semboller ve türler sağlayan ve bunları alan olarak döndüren bir sembol sağlayıcısını temsil eder.

## <a name="syntax"></a>Sözdizimi

```
IDebugSymbolProvider : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
Bir sembol sağlayıcısı, bir ifade değerlendiricisine sembol sağlamak ve bilgi yazmak için bu arabirimi uygulamalıdır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
Bu arabirim, COM'un `CoCreateInstance` işlevini kullanarak (yönetilmeyen sembol sağlayıcıları için) veya uygun yönetilen kod derlemesinin yüklenmesi ve bu derlemede bulunan bilgilere göre sembol sağlayıcısının anlık olarak yüklenmesiyle elde edilir. Hata ayıklama motoru, ifade değerlendiricisi ile eşgüdüm içinde çalışması için sembol sağlayıcısını anında işler. Bu arabirimi anında kullanma için bir yaklaşım için Örnek'e bakın.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
Aşağıdaki tabloda `IDebugSymbolProvider`.

|Yöntem|Açıklama|
|------------|-----------------|
|`Initialize`|Kullanım dışı. Kullanmayın.|
|`Uninitialize`|Kullanım dışı. Kullanmayın.|
|[GetContainerField](../../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md)|Hata ayıklama adresini içeren alanı alır.|
|`GetField`|Kullanım dışı. Kullanmayın.|
|[GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)|Belge konumunu hata ayıklama adresleri dizisine eşler.|
|[GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)|Belge bağlamını hata ayıklama adresleri dizisine eşler.|
|[GetContextFromAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getcontextfromaddress.md)|Hata ayıklama adresini belge bağlamına eşler.|
|[GetLanguage](../../../extensibility/debugger/reference/idebugsymbolprovider-getlanguage.md)|Hata ayıklama adresindeki kodu derlemek için kullanılan dili alır.|
|`GetGlobalContainer`|Kullanım dışı. Kullanmayın.|
|[GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)|Tam nitelikli bir yöntem adını temsil eden alanı alır.|
|[GetClassTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getclasstypebyname.md)|Tam nitelikli bir sınıf adını temsil eden sınıf alanı türünü alır.|
|[GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)|Hata ayıklama adresiyle ilişkili ad alanları için bir sayısallaştırıcı oluşturur.|
|[GetTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-gettypebyname.md)|Sembol adını sembol türüyle eşler.|
|[GetNextAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnextaddress.md)|Bir yöntemde belirli bir hata ayıklama adresini izleyen hata ayıklama adresini alır.|

## <a name="remarks"></a>Açıklamalar
Bu arabirim, belge konumlarını hata ayıklama adreslerine ve tam tersi olarak eşler.

## <a name="requirements"></a>Gereksinimler
Üstbilgi: sh.h

Ad alanı: Microsoft.VisualStudio.Debugger.Interop

Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Örnek
Bu örnek, GUID 'i (hata ayıklama motoru nun bu değeri bilmesi gerekir) göz önüne alındığında, sembol sağlayıcısının anlık olarak nasıl anında nasıl açileceğini gösterir.

```cpp
// A debug engine uses its own symbol provider and would know the GUID
// of that provider.
IDebugSymbolProvider *GetSymbolProvider(GUID *pSymbolProviderGuid)
{
    // This is typically defined globally. For this example, it is
    // defined here.
    static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0Exp";
    IDebugSymbolProvider *pProvider = NULL;
    if (pSymbolProviderGuid != NULL) {
        CLSID clsidProvider = { 0 };
        ::GetSPMetric(*pSymbolProviderGuid,
                      storetypeFile,
                      metricCLSID,
                      &clsidProvider,
                      strRegistrationRoot);
        if (IsEqualGUID(clsidProvider,GUID_NULL)) {
            // No file type provider, try metadata provider.
            ::GetSPMetric(*pSymbolProviderGuid,
                          ::storetypeMetadata,
                          metricCLSID,
                          &clsidProvider,
                          strRegistrationRoot);
        }
        if (!IsEqualGUID(clsidProvider,GUID_NULL)) {
            CComPtr<IDebugSymbolProvider> spSymbolProvider;
            spSymbolProvider.CoCreateInstance(clsidProvider);
            if (spSymbolProvider != NULL) {
                pProvider = spSymbolProvider.Detach();
            }
        }
    }
    return(pProvider);
}
```

## <a name="see-also"></a>Ayrıca bkz.
- [Sembol Sağlayıcısı Arabirimleri](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
