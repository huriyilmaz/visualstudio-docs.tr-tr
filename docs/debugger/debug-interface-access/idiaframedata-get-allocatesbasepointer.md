---
description: IDiaFrameData::get_allocatesBasePointer, temel işaretçinin bu adres aralığındaki kod için ayrılmış olup olmadığını belirten bir bayrak almaktadır.
title: IDiaFrameData::get_allocatesBasePointer | Microsoft Docs
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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: fb43d88fbe4bb607daaf6ed7e5b3c8641bbcf713
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122074871"
---
# <a name="idiaframedataget_allocatesbasepointer"></a>IDiaFrameData::get_allocatesBasePointer
Bu adres aralığındaki kod için temel işaretçinin ayrılmış olup olmadığını belirten bir bayrak alınır. Bu yöntem kullanım dışıdır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_allocatesBasePointer ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

[out] Bir `TRUE` temel işaretçi ayrılırsa döndürür; aksi takdirde `FALSE` döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür. Bu `S_FALSE` özellik desteklenmiyorsa döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu özellik yalnızca daha önce FPO_DATA erişen kod tarafından veya [IDiaFrameData::get_program yöntemi tarafından döndürülen](../../debugger/debug-interface-access/idiaframedata-get-program.md) program dizesi olduğunda `NULL` kullanılmalıdır. Aksi takdirde, program dizesi önceki yazmama değerlerini hesaplamak için gereken tüm bilgileri içerir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
- [IDiaFrameData::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)
