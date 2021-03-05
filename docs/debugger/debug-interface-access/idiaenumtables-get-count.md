---
description: Tablo sayısını alır.
title: 'IDiaEnumTables:: get_Count | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumTables::get_Count method
ms.assetid: 30fa316b-a746-4028-acae-4efcd2066f38
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c69e1860e3a0b534e53d5431c77cdfa3753a6da1
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102157863"
---
# <a name="idiaenumtablesget_count"></a>IDiaEnumTables::get_Count
Tablo sayısını alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_Count (    LONG* pRetVal
);

```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı Tablo sayısını döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)
- [IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)
