---
title: NameSearchOptions | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 61905c0c6c40d893cc8723b711d67690133a7155
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738623"
---
# <a name="namesearchoptions"></a>NameSearchOptions
Sembol ve dosya adları için arama seçeneklerini belirtir.

## <a name="syntax"></a>Sözdizimi

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
`nsNone` seçenek belirtilmedi.

`nsfCaseSensitive`, büyük/küçük harfe duyarlı bir ad eşleşmesi uygular.

`nsfCaseInsensitive`, büyük/küçük harfe duyarsız bir ad eşleşmesi uygular.

`nsfFNameExt` adları yollar olarak değerlendirir ve bir FileName. ext adı eşleşmesi uygular.

`nsfRegularExpression`, joker karakter olarak yıldız (*) ve soru işareti (?) kullanarak büyük/küçük harfe duyarlı bir ad eşleşmesi uygular. (Diğer yaygın normal ifade karakterleri desteklenmez.)

`nsfUndecoratedName` yalnızca, hem düzenlenmiş hem de düzenlenmiş adlara sahip semboller için geçerlidir.

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
