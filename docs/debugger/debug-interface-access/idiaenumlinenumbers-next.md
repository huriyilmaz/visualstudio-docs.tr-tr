---
description: Sabit Listesi dizisinde belirtilen sayıda satır numarasını alır.
title: 'IDiaEnumLineNumbers:: Next | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumLineNumbers::Next method
ms.assetid: 363d5b40-1316-4ab8-836f-63637f619e0a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9301c10634919774b8253eea77dba6acdd3c324a
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102157968"
---
# <a name="idiaenumlinenumbersnext"></a>IDiaEnumLineNumbers::Next
Sabit Listesi dizisinde belirtilen sayıda satır numarasını alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT Next ( 
   ULONG            celt,
   IDiaLineNumber** rgelt,
   ULONG*           pceltFetched
);
```

#### <a name="parameters"></a>Parametreler
 celt

'ndaki Numaralandırıcıda alınacak olan satır numaralarının sayısı.

 rgelt

dışı İstenen satır numaralarını temsil eden [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md) nesnelerinin bir dizisini döndürür.

 Pceltfettiz

dışı Getirilen Numaralandırıcı içindeki satır numaralarının sayısını döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` . `S_FALSE`Daha fazla satır numarası yoksa döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)
- [IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)
