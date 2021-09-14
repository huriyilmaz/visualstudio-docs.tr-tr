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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 78308844f64e87c95a41b662c2055f770809f262
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627357"
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
Bu yapıda açıklanan [arama SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) belirten bir numaralama enumerasyonundan gelen bayrakların birleşimi.

`bstrVerboseSearchInfo`\
Arama yolu ve sonuçları tek bir dizede birlenmiş.

## <a name="remarks"></a>Açıklamalar

Bu yapı [GetSymbolInfo yöntemine yapılan bir çağrıdan](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md) döndürülür.

Alan `bstrVerboseSearchInfo` boş yoksa, arama yapılan yolların listesini ve bu aramanın sonuçlarını içerir. Liste bir yol, ardından üç nokta ("..." ) ve ardından sonuç ile biçimlendirildi. Birden fazla yol sonuç çifti varsa, her çift bir "\r\n" (satır başı/satır besleme) çifti ile ayrılır. Desen şu şekildedir:

\<path>...\<result>\r\n... \<path> \<result> \<path>\r\n...\<result>

Son girdinin bir \r\n unutmayın.

Standart dışı bir `bstrVerboseSearchInfo` dizeye gönderilen olası bir dizeyi burada açık şekilde sınız.

`c:\symbols\user32.pdb... File not found.`

`c:\winnt\symbols\user32.pdb... Version does not match.`

`\\symbols\symbols\user32.dll\0a8sd0ad8ad\user32.pdb... Symbols loaded.`

## <a name="requirements"></a>Gereksinimler

Üst bilgi: msdbg.h

Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.

- [Yapılar ve Birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)
