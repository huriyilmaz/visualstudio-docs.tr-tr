---
description: Aranan sembol arama yolları hakkında durum bilgilerini içerir.
title: MODULE_SYMBOL_SEARCH_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_SYMBOL_SEARCH_INFO
helpviewer_keywords:
- MODULE_SYMBOL_SEARCH_INFO structure
ms.assetid: 432aff03-08a5-4c5a-b2d5-e212090fc70a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 266d786df422e5260e212a4005feb7d3167af099
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105057903"
---
# <a name="module_symbol_search_info"></a>MODULE_SYMBOL_SEARCH_INFO

Aranan sembol arama yolları hakkında durum bilgilerini içerir.

## <a name="syntax"></a>Syntax

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
Bu yapıda açıklanan arama bilgilerinin türünü belirten [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) Numaralandırmadaki bayrakların birleşimi.

`bstrVerboseSearchInfo`\
Tek bir dizeye birleştirilmiş arama yolu ve sonuçları.

## <a name="remarks"></a>Açıklamalar

Bu yapı [Getsymbolınfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md) yöntemine yapılan çağrıdan döndürülür.

`bstrVerboseSearchInfo`Alan boş değilse, aranan yolların ve bu aramanın sonuçlarının bir listesini içerir. Liste, bir yol ile, ardından üç nokta ("...") ve ardından sonuç olarak biçimlendirilir. Birden fazla yol sonuç çifti varsa, her çift bir "\r\n" (satır başı/linefeed) çifti ile ayrılır. Bu model şöyle görünür:

\<path>...\<result> \r\n \<path> ... \<result> \r\n \<path> ...\<result>

Son girişin bir \r\n dizisine sahip olmadığına unutmayın.

`bstrVerboseSearchInfo`Standart Out 'a gönderilen olası bir dize aşağıda verilmiştir.

`c:\symbols\user32.pdb... File not found.`

`c:\winnt\symbols\user32.pdb... Version does not match.`

`\\symbols\symbols\user32.dll\0a8sd0ad8ad\user32.pdb... Symbols loaded.`

## <a name="requirements"></a>Gereksinimler

Üst bilgi: msdbg. h

Ad alanı: Microsoft. VisualStudio. Debugger. Interop

Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.

- [Yapılar ve Birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)
