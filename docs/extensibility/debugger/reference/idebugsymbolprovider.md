---
description: Bu arabirim sembolleri ve türleri sağlayan bir sembol sağlayıcısını temsil eder ve bunları alan olarak döndürür.
title: IDebugSymbolProvider | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider
helpviewer_keywords:
- IDebugSymbolProvider interface
ms.assetid: df5f095f-1dee-46f9-84cf-92417c71d5fb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 9bdbf198b65483a8241de571e2f5fde307a312d25225480c63898da9323898f6
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121306770"
---
# <a name="idebugsymbolprovider"></a>IDebugSymbolProvider
Bu arabirim sembolleri ve türleri sağlayan bir sembol sağlayıcısını temsil eder ve bunları alan olarak döndürür.

## <a name="syntax"></a>Syntax

```
IDebugSymbolProvider : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
Bir sembol sağlayıcısı, bir ifade değerlendiricisi için sembol ve tür bilgilerini sağlamak üzere bu arabirimi uygulamalıdır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
Bu arabirim, COM işlevi kullanılarak elde edilir `CoCreateInstance` (yönetilmeyen sembol sağlayıcıları için) veya uygun yönetilen kod derlemesini yükleyerek ve söz konusu derlemede bulunan bilgilere göre sembol sağlayıcısını örnekleyerek. Hata ayıklama altyapısı, sembol sağlayıcısını ifade değerlendiricisi ile koordine halinde çalışacak şekilde oluşturur. Bu arabirimin örneğini oluşturmak için bir yaklaşım örneğine bakın.

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDebugSymbolProvider` .

|Yöntem|Açıklama|
|------------|-----------------|
|`Initialize`|Kullanım dışı. Kullanmayın.|
|`Uninitialize`|Kullanım dışı. Kullanmayın.|
|[GetContainerField](../../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md)|Hata ayıklama adresini içeren alanı alır.|
|`GetField`|Kullanım dışı. Kullanmayın.|
|[GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)|bir belge konumunu hata ayıklama adresleri dizisine Haritalar.|
|[GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)|bir belge bağlamını hata ayıklama adresleri dizisine Haritalar.|
|[GetContextFromAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getcontextfromaddress.md)|bir hata ayıklama adresini bir belge bağlamına Haritalar.|
|[GetLanguage](../../../extensibility/debugger/reference/idebugsymbolprovider-getlanguage.md)|Hata ayıklama adresinde kodu derlemek için kullanılan dili alır.|
|`GetGlobalContainer`|Kullanım dışı. Kullanmayın.|
|[GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)|Tam nitelikli bir yöntem adını temsil eden alanı alır.|
|[GetClassTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getclasstypebyname.md)|Tam sınıf adını temsil eden sınıf alanı türünü alır.|
|[GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)|Hata ayıklama adresiyle ilişkili ad alanları için bir Numaralandırıcı oluşturur.|
|[GetTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-gettypebyname.md)|sembol adına bir sembol adı Haritalar.|
|[GetNextAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnextaddress.md)|Bir yöntemde belirli bir hata ayıklama adresini izleyen hata ayıklama adresini alır.|

## <a name="remarks"></a>Açıklamalar
Bu arabirim, belge konumlarını hata ayıklama adresleriyle ve tam tersi olarak eşler.

## <a name="requirements"></a>Gereksinimler
Üstbilgi: SH. h

Ad alanı: Microsoft. VisualStudio. Debugger. Interop

Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Örnek
Bu örnek, bir sembol sağlayıcısının GUID 'sine (bir hata ayıklama altyapısı bu değeri bilmelidir) göre nasıl örneklendirileyeceğinizi gösterir.

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
