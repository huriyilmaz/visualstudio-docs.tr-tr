---
title: NameSearchOptions | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- NameSearchOptions enumeration
ms.assetid: 67dfbede-2678-47df-b664-5c49841d0b9b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 696ad3e659b503b27da73056dafb57c5852d5133
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85461177"
---
# <a name="namesearchoptions"></a>NameSearchOptions
Sembol ve dosya adları için arama seçeneklerini belirtir.

## <a name="syntax"></a>Syntax

```C++
enum NameSearchOptions {
    nsNone,
    nsfCaseSensitive     = 0x1,
    nsfCaseInsensitive   = 0x2,
    nsfFNameExt          = 0x4,
    nsfRegularExpression = 0x8,
    nsfUndecoratedName   = 0x10,

// For backward compatibility:
    nsCaseSensitive           = nsfCaseSensitive,
    nsCaseInsensitive         = nsfCaseInsensitive,
    nsFNameExt                = nsfCaseInsensitive | nsfFNameExt,
    nsRegularExpression       = nsfRegularExpression | nsfCaseSensitive,
    nsCaseInRegularExpression = nsfRegularExpression | nsfCaseInsensitive
};
```

## <a name="elements"></a>Öğeler
`nsNone` Hiçbir seçenek belirtilmedi.

`nsfCaseSensitive` Büyük/küçük harfe duyarlı bir ad eşleşmesi uygular.

`nsfCaseInsensitive` Büyük/küçük harf duyarsız bir ad eşleşmesi uygular.

`nsfFNameExt` Adları yollar olarak değerlendirir ve bir FileName. ext adı eşleşmesi uygular.

`nsfRegularExpression` Joker karakter olarak yıldız (*) ve soru işareti (?) kullanarak büyük/küçük harfe duyarlı bir ad eşleşmesi uygular. (Diğer yaygın normal ifade karakterleri desteklenmez.)

`nsfUndecoratedName` Yalnızca, hem düzenlenmiş hem de düzenlenmiş adlara sahip semboller için geçerlidir.

## <a name="remarks"></a>Açıklamalar
Bu Numaralandırmadaki değerler aşağıdaki yöntemlere geçirilir:

- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)

- [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)

- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)

## <a name="requirements"></a>Gereksinimler
Üstbilgi: dia2. h

## <a name="see-also"></a>Ayrıca bkz.
- [Enumerations and Structures](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)
- [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)
- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)
