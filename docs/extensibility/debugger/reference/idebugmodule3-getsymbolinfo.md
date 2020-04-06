---
title: IDebugModule3::GetSymbolInfo | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule3::GetSymbolInfo
helpviewer_keywords:
- GetSymbolInfo method
- IDebugModule3::GetSymbolInfo method
ms.assetid: dda5e8e1-6878-4aa9-9ee4-e7d0dcc11210
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3aafb28715f58eaba4499b47a2e1dee15b82ed14
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726895"
---
# <a name="idebugmodule3getsymbolinfo"></a>IDebugModule3::GetSymbolInfo
Sembolleriçin aranan yolların listesini ve her yolu aramanın sonuçlarını alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetSymbolInfo(
    SYMBOL_SEARCH_INFO_FIELDS  dwFields,
    MODULE_SYMBOL_SEARCH_INFO* pInfo
);
```

```csharp
int GetSymbolInfo(
    enum_SYMBOL_SEARCH_INFO_FIELDS dwFields,
    MODULE_SYMBOL_SEARCH_INFO[]    pinfo
);
```

## <a name="parameters"></a>Parametreler
`dwFields`\
[içinde] Hangi alanların dolduruleceğini belirten [numaralandırma SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) gelen `pInfo` bayrakların birleşimi.

`pInfo`\
[çıkış] Üyeleri belirtilen bilgilerle doldurulacak [olan MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md) bir yapı. Bu null değeri ise, bu `E_INVALIDARG`yöntem döndürür.

## <a name="return-value"></a>Dönüş Değeri
Yöntem başarılı olursa, geri `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

> [!NOTE]
> Döndürülen dize `MODULE_SYMBOL_SEARCH_INFO` (yapıdaki) döndürülse `S_OK` bile boş olabilir. Bu durumda, döndürülecek arama bilgisi yoktu.

## <a name="remarks"></a>Açıklamalar
`MODULE_SYMBOL_SEARCH_INFO` Yapının `bstrVerboseSearchInfo` alanı boş değilse, aranan yolların bir listesini ve bu aramanın sonuçlarını içerir. Liste bir yol ile biçimlendirilir, ardından bir elips ("..."), ardından sonuç gelir. Birden fazla yol sonuç çifti varsa, her çift bir "\r\n" (taşıma-döndürme/linefeed) çifti ile ayrılır. Desen şuna benzer:

\<yol>... \<sonuç>\r\n\<yolu>... \<sonuç>\r\n\<yolu>... \<sonuç>

Son girişin \r\n sırası olmadığını unutmayın.

## <a name="example"></a>Örnek
Bu örnekte, bu yöntem üç farklı arama sonucuyla üç yol döndürür. Her satır bir satır döndürme/linefeed çifti ile sonlandırılır. Örnek çıktı, arama sonuçlarını tek bir dize olarak yazdırır.

> [!NOTE]
> Durum sonucu hemen aşağıdaki her şey "..." hattın sonuna kadar.

```cpp
void ShowSymbolSearchResults(IDebugModule3 *pIDebugModule3)
{
    MODULE_SYMBOL_SEARCH_INFO ssi = { 0 };
    HRESULT hr;
    hr = pIDebugModule3->GetSymbolInfo(SSIF_VERBOSE_SEARCH_INFO,&ssi);
    if (SUCCEEDED(hr)) {
        CComBSTR searchInfo = ssi.bstrVerboseSearchInfo;
        if (searchInfo.Length() != 0) {
            std::wcout << (wchar_t *)(BSTR)searchInfo;
            std::wcout << std::endl;
        }
    }
}
```

**c:\semboller\user32.pdb... Dosya bulunamadı.** 
 **c:\winnt\symbols\user32.pdb... Sürüm eşleşmez.** 
 ** \\\symbols\symbols\user32.dll\0a8sd0ad8ad\user32.pdb... Semboller yüklendi.**

## <a name="see-also"></a>Ayrıca bkz.

- [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md)
- [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md)
- [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)
