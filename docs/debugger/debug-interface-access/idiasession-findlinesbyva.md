---
description: Belirtilen sanal adres (VA) aralığındaki satırlar için satır numarası bilgilerini alın.
title: IDiaSession::findLinesByVA | Microsoft Docs
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
ms.openlocfilehash: fca9006f0b7a556be022eaac9682aa58b9e70228
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122081352"
---
# <a name="idiasessionfindlinesbyva"></a>IDiaSession::findLinesByVA
Belirtilen sanal adres (VA) aralığındaki satırlar için satır numarası bilgilerini alın.

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

[in] Adresi VA olarak belirtir.

`length`

[in] Bu sorguyla birlikte ele alınan adres aralığının bayt sayısını belirtir.

`ppResult`

[out] Belirtilen adres aralığını içeren tüm satır numaralarının listesini içeren bir [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) nesnesi döndürür.

## <a name="example"></a>Örnek
Bu örnek, işlevin sanal adresini ve uzunluğunu kullanarak bir işlevde yer alan tüm satır numaralarını alan bir işlevi gösterir.

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
