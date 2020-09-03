---
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fed5b7f6cf3b18e854a9607b163b5e538f734915
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85467570"
---
# <a name="idiaenumtablesget_count"></a>IDiaEnumTables::get_Count
Tablo sayısını alır.

## <a name="syntax"></a>Söz dizimi

```C++
HRESULT get_Count (    LONG* pRetVal
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