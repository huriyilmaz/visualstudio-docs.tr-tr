---
description: IDiaFrameData::get_maxStack, çerçevede yığına gönderilen en fazla bayt sayısını almaktadır.
title: IDiaFrameData::get_maxStack | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_maxStack method
ms.assetid: 2585e13c-c0f3-49fe-9a84-08adb0dbeaa4
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: f0af1f96f3f9ee468c18b89a1fd15f291ce2de0c
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126629828"
---
# <a name="idiaframedataget_maxstack"></a>IDiaFrameData::get_maxStack
Çerçevede yığına gönderilen en fazla bayt sayısını alan.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_maxStack ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

[out] Yığına gönderilen en fazla bayt sayısını döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür. Bu `S_FALSE` özellik desteklenmiyorsa döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem tarafından döndürülen değer genellikle bir program dizesinin yorumlanmasında kullanılır (program dizesinin tanımı için [IDiaFrameData::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md) yöntemine bakın).

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
- [IDiaFrameData::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)
