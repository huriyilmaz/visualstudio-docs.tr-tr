---
description: Belirtilen sanal adres (VA) aralığında yer alan satırlar için satır numarası bilgilerini alır.
title: 'IDiaSession:: findLinesByVA | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findLinesByVA method
ms.assetid: f647eee9-a73c-483b-9fe9-21f42e560a7b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: cd4d27c96a6a08c6fc63d38d9845d30366be760c7db9e5fd34dfac55fc9ae497
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121380145"
---
# <a name="idiasessionfindlinesbyva"></a>IDiaSession::findLinesByVA
Belirtilen sanal adres (VA) aralığında yer alan satırlar için satır numarası bilgilerini alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT findLinesByVA (
    ULONGLONG             va,
    DWORD                 length,
    IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>Parametreler
`va`

'ndaki Adresi bir VA olarak belirtir.

`length`

'ndaki Bu sorguyla birlikte kapsamak üzere adres aralığının bayt sayısını belirtir.

`ppResult`

dışı Belirtilen adres aralığını kapsayan tüm satır numaralarının listesini içeren bir [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) nesnesi döndürür.

## <a name="example"></a>Örnek
Bu örnek, işlevin sanal adresini ve uzunluğunu kullanarak bir işlevde bulunan tüm satır numaralarını elde eden bir işlevi gösterir.

```C++
IDiaEnumLineNumbers *GetLineNumbersByVA(IDiaSymbol *pFunc, IDiaSession *pSession)
{
    IDiaEnumLineNumbers* pEnum = NULL;
    ULONGLONG            va;
    ULONGLONG            length;

    if (pFunc->get_virtualAddress ( &va ) == S_OK)
    {
        pFunc->get_length( &length );
        pSession->findLinesByVA( va, static_cast<DWORD>( length ), &pEnum );
    }
    return(pEnum);
}
```

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
