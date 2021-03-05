---
description: 'IDiaFrameData:: get_allocatesBasePointer, temel işaretçinin bu adres aralığındaki kod için ayrılıp ayrılmadığını gösteren bir bayrak alır.'
title: 'IDiaFrameData:: get_allocatesBasePointer | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_allocatesBasePointer method
ms.assetid: 8a33db5d-008c-4fe5-b64f-210c9b77f686
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8fce5e5dbd12be7bae6ba1937b30c8a5d62de3ec
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102157753"
---
# <a name="idiaframedataget_allocatesbasepointer"></a>IDiaFrameData::get_allocatesBasePointer
Taban işaretçisinin bu adres aralığındaki kod için ayrılmış olup olmadığını gösteren bir bayrak alır. Bu yöntem kullanım dışıdır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_allocatesBasePointer ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı `TRUE` Bir taban işaretçisi ayrıldıysanız döndürür; Aksi takdirde, döndürür `FALSE` .

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` . `S_FALSE`Bu özellik desteklenmiyorsa döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu özellik yalnızca FPO_DATA veya [IDiaFrameData:: get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md) yöntemi tarafından döndürülen program dizesi olduğunda, yalnızca önceden erişilen kod tarafından kullanılmalıdır `NULL` . Aksi takdirde, program dizesi önceki kayıt değerlerini hesaplamak için gereken tüm bilgileri içerir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
- [IDiaFrameData::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)
