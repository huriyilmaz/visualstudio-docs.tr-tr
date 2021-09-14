---
description: Benzersiz tanımlayıcısıyla bir sembolünü verir.
title: IDiaSession::symbolById | Microsoft Docs
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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 8f6f03339758ac3496f961313593c0b663fab30f
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126629061"
---
# <a name="idiasessionsymbolbyid"></a>IDiaSession::symbolById
Benzersiz tanımlayıcısıyla bir sembolünü verir.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT symbolById (
    DWORD        id,
    IDiaSymbol** ppSymbol
);
```

#### <a name="parameters"></a>Parametreler
`id`

[in] Benzersiz tanımlayıcı.

`ppSymbol`

[out] Alınan sembolü [temsil eden bir IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
Belirtilen tanımlayıcı, tüm sembolleri benzersiz hale DIA SDK tarafından dahili olarak kullanılan benzersiz bir değerdir.

Bu yöntem, örneğin, başka bir sembolün türünü temsil eden sembolü almak için kullanılabilir (örneğine bakın).

## <a name="example"></a>Örnek
Bu örnek, başka bir sembolün türünü temsil eden [bir IDiaSymbol'ı](../../debugger/debug-interface-access/idiasymbol.md) almaktadır. Bu örnek, oturumda `symbolById` yönteminin nasıl kullanılageldi. Daha basit bir yaklaşım [IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md) yöntemini çağırarak tür sembolünü doğrudan almaktır.

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
