---
title: 'IDiaSession:: findLinesByRVA | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findLinesByRVA method
ms.assetid: 06f53b0b-b5b4-42cf-9252-dcee0dbe2d71
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b6dfe92a5c804c0c81bfff6fa457e1ca797a62f9
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742083"
---
# <a name="idiasessionfindlinesbyrva"></a>IDiaSession::findLinesByRVA
Belirtilen bir göreli sanal adres (RVA) içeren belirtilen bir compiland içindeki satırları alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT findLinesByRVA ( 
    DWORD                 rva,
    DWORD                 length,
    IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>Parametreler
`rva`

'ndaki Adresi RVA olarak belirtir.

`length`

'ndaki Bu sorguyla birlikte kapsamak üzere adres aralığının bayt sayısını belirtir.

`ppResult`

dışı Belirtilen adres aralığını kapsayan tüm satır numaralarının listesini içeren bir [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
Başarılı olursa `S_OK` döndürür; Aksi takdirde, bir hata kodu döndürür.

## <a name="example"></a>Örnek
Bu örnek, işlevin göreli sanal adresini ve uzunluğunu kullanarak belirtilen işlevde bulunan tüm satır numaralarını elde eden bir işlevi gösterir.

```C++
IDiaEnumLineNumbers* GetLineNumbersByRVA(IDiaSymbol *pFunc, IDiaSession *pSession)
{
    IDiaEnumLineNumbers* pEnum = NULL;
    DWORD                rva;
    ULONGLONG            length;

    if (pFunc->get_relativeVirtualAddress ( &rva ) == S_OK)
    {
        pFunc->get_length ( &length );
        pSession->findLinesByRVA( rva, static_cast<DWORD>( length ), &pEnum );
    }
    return(pEnum);
}
```

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
