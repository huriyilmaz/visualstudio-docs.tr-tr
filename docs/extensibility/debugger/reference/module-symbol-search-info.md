---
title: MODULE_SYMBOL_SEARCH_INFO | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_SYMBOL_SEARCH_INFO
helpviewer_keywords:
- MODULE_SYMBOL_SEARCH_INFO structure
ms.assetid: 432aff03-08a5-4c5a-b2d5-e212090fc70a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5f15587759c4f665d1593d1298c47459a0e64aac
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714251"
---
# <a name="module_symbol_search_info"></a>MODULE_SYMBOL_SEARCH_INFO

Aranan simge arama yolları hakkında durum bilgileri içerir.

## <a name="syntax"></a>Sözdizimi

```cpp
typedef struct _tagSYMBOL_SEARCH_INFO
{
    SYMBOL_SEARCH_INFO_FIELDS dwValidFields;
    BSTR                      bstrVerboseSearchInfo;
} MODULE_SYMBOL_SEARCH_INFO;
```

```csharp
public struct MODULE_SYMBOL_SEARCH_INFO {
    public uint   dwValidFields;
    public string bstrVerboseSearchInfo;
}
```

## <a name="members"></a>Üyeler

`dwValidFields`\
Bu yapıda açıklanan arama bilgilerinin türünü belirten [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) numaralandırmadan gelen bayrakların birleşimi.

`bstrVerboseSearchInfo`\
Arama yolu ve sonuçlar tek bir dize halinde sıkıştırılır.

## <a name="remarks"></a>Açıklamalar

Bu yapı [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md) yöntemine yapılan bir çağrıdan döndürülür.

`bstrVerboseSearchInfo` Alan boş değilse, aranan yolların bir listesini ve bu aramanın sonuçlarını içerir. Liste bir yol ile biçimlendirilir, ardından bir elips ("..."), ardından sonuç gelir. Birden fazla yol sonuç çifti varsa, her çift bir "\r\n" (taşıma-döndürme/linefeed) çifti ile ayrılır. Desen şuna benzer:

\<yol>... \<sonuç>\r\n\<yolu>... \<sonuç>\r\n\<yolu>... \<sonuç>

Son girişin \r\n sırası olmadığını unutmayın.

Burada standart `bstrVerboseSearchInfo` dışarı gönderildi olası bir dize.

`c:\symbols\user32.pdb... File not found.`

`c:\winnt\symbols\user32.pdb... Version does not match.`

`\\symbols\symbols\user32.dll\0a8sd0ad8ad\user32.pdb... Symbols loaded.`

## <a name="requirements"></a>Gereksinimler

Üstbilgi: msdbg.h

Ad alanı: Microsoft.VisualStudio.Debugger.Interop

Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.

- [Yapılar ve Birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)
