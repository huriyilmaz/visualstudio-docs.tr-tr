---
description: Bir sembolü benzersiz tanımlayıcısına göre alır.
title: 'IDiaSession:: symbolById | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::symbolById method
ms.assetid: 062e4b5a-9c4d-4703-88da-ec13102c2b66
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 979825cd3e62c97334d55676b3bf32bf874f8445
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102147606"
---
# <a name="idiasessionsymbolbyid"></a>IDiaSession::symbolById
Bir sembolü benzersiz tanımlayıcısına göre alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT symbolById (
    DWORD        id,
    IDiaSymbol** ppSymbol
);
```

#### <a name="parameters"></a>Parametreler
`id`

'ndaki Benzersiz tanımlayıcı.

`ppSymbol`

dışı Alınan simgeyi temsil eden bir [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
Belirtilen tanımlayıcı, tüm sembolleri benzersiz hale getirmek için DIA SDK tarafından dahili olarak kullanılan benzersiz bir değerdir.

Bu yöntem, örneğin, başka bir simgenin türünü temsil eden simgeyi almak için kullanılabilir (örneğe bakın).

## <a name="example"></a>Örnek
Bu örnek, başka bir simgenin türünü temsil eden bir [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) alır. Bu örnek, oturumunda yönteminin nasıl kullanılacağını gösterir `symbolById` . Daha basit bir yaklaşım, tür sembolünü doğrudan almak için [IDiaSymbol:: get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md) yöntemini çağırmalıdır.

```C++
IDiaSymbol *GetSymbolType(IDiaSymbol *pSymbol, IDiaSession *pSession)
{
    IDiaSymbol *pTypeSymbol = NULL;
    if (pSymbol != NULL && pSession != NULL)
    {
        DWORD symbolTypeId;
        pSymbol->get_typeId(&symbolTypeId);
        pSession->symbolById(symbolTypeId, &pTypeSymbol);
    }
    return(pTypeSymbol);
}
```

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)
