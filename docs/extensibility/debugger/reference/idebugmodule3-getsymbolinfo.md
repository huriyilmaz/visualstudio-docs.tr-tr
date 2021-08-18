---
description: Simgeler için aranan yolların yanı sıra her bir yolu aramanın sonuçlarını alır.
title: 'IDebugModule3:: Getsymbolınfo | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule3::GetSymbolInfo
helpviewer_keywords:
- GetSymbolInfo method
- IDebugModule3::GetSymbolInfo method
ms.assetid: dda5e8e1-6878-4aa9-9ee4-e7d0dcc11210
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d187673c7f2a5f33ecdedd5fe88a3b62d518edc0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122133126"
---
# <a name="idebugmodule3getsymbolinfo"></a>IDebugModule3::GetSymbolInfo
Simgeler için aranan yolların yanı sıra her bir yolu aramanın sonuçlarını alır.

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
'ndaki [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) Numaralandırmadaki, doldurulacak alanları belirten bayrakların birleşimi `pInfo` .

`pInfo`\
dışı Üyeleri belirtilen bilgilerle doldurulacak [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md) yapısı. Bu null bir değer ise, bu yöntem döndürür `E_INVALIDARG` .

## <a name="return-value"></a>Dönüş Değeri
Yöntem başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

> [!NOTE]
> Döndürülen dize ( `MODULE_SYMBOL_SEARCH_INFO` yapıda) döndürülse bile boş olabilir `S_OK` . Bu durumda, döndürülecek arama bilgisi yoktu.

## <a name="remarks"></a>Açıklamalar
`bstrVerboseSearchInfo` `MODULE_SYMBOL_SEARCH_INFO` Yapı alanı boş değilse, aranan yolların ve bu aramanın sonuçlarının bir listesini içerir. Liste, bir yol ile, ardından üç nokta ("...") ve ardından sonuç olarak biçimlendirilir. Birden fazla yol sonuç çifti varsa, her çift bir "\r\n" (satır başı/linefeed) çifti ile ayrılır. Bu model şöyle görünür:

\<path>...\<result>\r\n\<path> ... \<result>\r\n\<path> ...\<result>

Son girişin \r\n sırası olmadığına unutmayın.

## <a name="example"></a>Örnek
Bu örnekte, bu yöntem üç farklı arama sonucu olan üç yol döndürür. Her satır, bir satır başı/satır besleme çifti ile sonlandırılır. Örnek çıktı yalnızca arama sonuçlarını tek bir dize olarak yazdırır.

> [!NOTE]
> Durum sonucu, "..." öğesinden hemen sonra gelen her şey olur satırın sonuna kadar.

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

**c:\symbols\user32.pdb... Dosya bulunamadı.** 
 **c:\winnt\symbols\user32.pdb... Sürüm eşleşmiyor.** 
 **\\\symbols\symbols\user32.dll \0A8sd0ad8ad\user32.pdb... Semboller yüklendi.**

## <a name="see-also"></a>Ayrıca bkz.

- [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md)
- [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md)
- [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)
