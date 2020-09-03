---
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a8c51b335e0d13752ee2f3c6c68c17b5f2b76a9d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85467430"
---
# <a name="idiaframedataget_allocatesbasepointer"></a>IDiaFrameData::get_allocatesBasePointer
Taban işaretçisinin bu adres aralığındaki kod için ayrılmış olup olmadığını gösteren bir bayrak alır. Bu yöntem kullanım dışıdır.

## <a name="syntax"></a>Söz dizimi

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