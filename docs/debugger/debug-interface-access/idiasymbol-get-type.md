---
description: Bu sembolün türünü temsil eden simgeyi alır.
title: 'IDiaSymbol:: get_type | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_type method
ms.assetid: 1c6a4176-dd4e-4c22-8b8f-0e559fc078ba
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 6d9025a51e06158448cf273a60f95ac40b8f99a9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122105428"
---
# <a name="idiasymbolget_type"></a>IDiaSymbol::get_type
Bu sembolün türünü temsil eden simgeyi alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_type (
    IDiaSymbol** pRetVal
);
```

#### <a name="parameters"></a>Parametreler
`pRetVal`

dışı Bu sembolün türünü temsil eden bir [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, `S_FALSE` bir hata kodu döndürür.

> [!NOTE]
> Dönüş değeri, `S_FALSE` özelliğin sembol için kullanılamadığı anlamına gelir.

## <a name="remarks"></a>Açıklamalar
Bir sembolün türünü öğrenmek için, bu yöntemi çağırmanız ve elde edilen [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) nesnesini incelemeniz gerekir. Bir simgenin bir türe sahip olmadığı için mümkün olduğunu unutmayın. Örneğin, bir yapının adında hiçbir tür yoktur, ancak alt sembolleri olabilir (Bu alt öğeleri incelemek için [IDiaSymbol:: findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md) metodunu kullanın).

## <a name="example"></a>Örnek

```C++
IDiaSymbol*         pType;
CComPtr<IDiaSymbol> pBaseType;
if (SUCCEEDED(pType->get_type( &pBaseType ))) {
    BasicType btBaseType;
    if (SUCCEEDED(pBaseType->get_baseType((DWORD *)&btBaseType))) {
        // Do something with basic type.
    }
}
```

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)
- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)
