---
description: Belirtilen bir göreli sanal adresi (RVA) içeren belirtilen bir derlemede satırları alır.
title: IDiaSession::findLinesByRVA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findLinesByRVA method
ms.assetid: 06f53b0b-b5b4-42cf-9252-dcee0dbe2d71
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 9eeaed28e4e7cc6bc27bac5c7840586e80e547ed2f2d9a3adc1f9f013a36beb1
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121380193"
---
# <a name="idiasessionfindlinesbyrva"></a>IDiaSession::findLinesByRVA
Belirtilen bir göreli sanal adresi (RVA) içeren belirtilen bir derlemede satırları alır.

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

[in] Adresi RVA olarak belirtir.

`length`

[in] Bu sorguyla birlikte ele alınan adres aralığının bayt sayısını belirtir.

`ppResult`

[out] Belirtilen adres aralığını içeren tüm satır numaralarının listesini içeren bir [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="example"></a>Örnek
Bu örnek, işlevin göreli sanal adresini ve uzunluğunu kullanarak belirtilen işlevde yer alan tüm satır numaralarını alan bir işlevi gösterir.

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
