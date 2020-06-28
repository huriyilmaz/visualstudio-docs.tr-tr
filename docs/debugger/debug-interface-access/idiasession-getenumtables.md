---
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4b9b229de3818b00379d95a5c19e35c7e83c845e
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85465428"
---
# <a name="idiasessiongetenumtables"></a>IDiaSession::getEnumTables
Sembol deposunda bulunan tüm tablolar için bir Numaralandırıcı alır.

## <a name="syntax"></a>Söz dizimi

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
