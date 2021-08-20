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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 0c114955909619ffba09b44c3f8bf2380530dc79
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122134443"
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
