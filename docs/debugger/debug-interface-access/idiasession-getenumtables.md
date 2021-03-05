---
description: Sembol deposunda bulunan tüm tablolar için bir Numaralandırıcı alır.
title: 'IDiaSession:: getEnumTables | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::getEnumTables method
ms.assetid: 66e0fba2-ca63-4e24-a46a-c99c7fb61dd1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d75ac2a4bca7051c6fe80f80b7a8063ef7ec6c86
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102157023"
---
# <a name="idiasessiongetenumtables"></a>IDiaSession::getEnumTables
Sembol deposunda bulunan tüm tablolar için bir Numaralandırıcı alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT getEnumTables (
    IDiaEnumTables** ppEnumTables
);
```

#### <a name="parameters"></a>Parametreler
`ppEnumTables`

dışı Bir [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md) nesnesi döndürür. Sembol deposundaki tabloları numaralandırmak için bu arabirimi kullanın.

## <a name="return-value"></a>Dönüş Değeri
Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="example"></a>Örnek
Bu örnek, `getEnumTables` belirli bir Numaralandırıcı nesnesi elde etmek için yöntemini kullanan genel bir işlev gösterir. Numaralandırıcı bulunursa, işlev istenen arabirime çileolabilecek bir işaretçi döndürür; Aksi takdirde, işlev döndürür `NULL` .

```C++
IUnknown *GetTable(IDiaSession *pSession, REFIID iid)
{
    IUnknown *pUnknown = NULL;
    if (pSession != NULL)
    {
        CComPtr<IDiaEnumTables> pEnumTables;
        if (pSession->getEnumTables(&pEnumTables) == S_OK)
        {
            CComPtr<IDiaTable> pTable;
            DWORD celt = 0;
            while(pEnumTables->Next(1,&pTable,&celt) == S_OK &&
                  celt == 1)
            {
                if (pTable->QueryInterface(iid, (void **)pUnknown) == S_OK)
                {
                    break;
                }
                pTable = NULL;
            }
        }
    }
    return(pUnknown);
}
```

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
