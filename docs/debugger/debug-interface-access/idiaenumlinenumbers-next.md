---
description: Numaralama dizisinde belirtilen sayıda satır numarası verir.
title: IDiaEnumLineNumbers::Next | Microsoft Docs
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
ms.openlocfilehash: ea14a255458aa0f43cc5236bff7d26ea5f14917c0b17434fa9b1755ce6b48e52
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121380473"
---
# <a name="idiaenumlinenumbersnext"></a>IDiaEnumLineNumbers::Next
Numaralama dizisinde belirtilen sayıda satır numarası verir.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT Next ( 
   ULONG            celt,
   IDiaLineNumber** rgelt,
   ULONG*           pceltFetched
);
```

#### <a name="parameters"></a>Parametreler
 Celt

[in] Alınan numaralayıcıda satır numaralarının sayısı.

 Rgelt

[out] İstenen satır numaralarını [temsil eden bir IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md) nesneleri dizisi döndürür.

 pceltFetched

[out] Getirili numaralayıcıda satır numaralarının sayısını döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür. Başka `S_FALSE` satır numarası yoksa döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)
- [IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)
