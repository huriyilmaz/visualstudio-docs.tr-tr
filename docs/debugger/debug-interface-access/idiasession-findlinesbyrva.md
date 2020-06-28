---
title: 'IDiaSession:: findLinesByRVA | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 671e72d9a0dc1f9d4bf539efaa75e76e2f15f23f
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85465610"
---
# <a name="idiasessionfindlinesbyrva"></a>IDiaSession::findLinesByRVA
Belirtilen bir göreli sanal adres (RVA) içeren belirtilen bir compiland içindeki satırları alır.

## <a name="syntax"></a>Söz dizimi

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
Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

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
