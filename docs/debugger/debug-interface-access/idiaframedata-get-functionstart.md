---
description: 'IDiaFrameData:: get_functionStart, bloğun bir işlevin giriş noktasını içerip içermediğini gösteren bir bayrak alır.'
title: 'IDiaFrameData:: get_functionStart | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_functionStart method
ms.assetid: 49fd24fb-65c2-4812-8303-56a968353e1b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: b33b08a00d62c89228346e5171219a801b0ad2a9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122161757"
---
# <a name="idiaframedataget_functionstart"></a>IDiaFrameData::get_functionStart
Bloğun bir işlevin giriş noktasını içerip içermediğini gösteren bir bayrak alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_functionStart ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı `TRUE` Blok giriş noktasını içeriyorsa döndürür; Aksi takdirde döndürür `FALSE` .

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` . `S_FALSE`Bu özellik desteklenmiyorsa döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Çerçeve çerçevesinin bir işlevin başında olmaması mümkündür çünkü çerçeve bir işleve yerleştirilen bir satır içi yöntemi veya işlevi temsil eder.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
