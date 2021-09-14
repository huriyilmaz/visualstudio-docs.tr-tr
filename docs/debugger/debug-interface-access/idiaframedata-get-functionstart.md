---
description: IDiaFrameData::get_functionStart bloğun bir işlevin giriş noktasını içerdiğini belirten bir bayrak verir.
title: IDiaFrameData::get_functionStart | Microsoft Docs
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126629871"
---
# <a name="idiaframedataget_functionstart"></a>IDiaFrameData::get_functionStart
Bloğun bir işlevin giriş noktasını içerdiğini belirten bir bayrak verir.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_functionStart ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

[out] Blok `TRUE` giriş noktasını içeriyorsa döndürür; aksi takdirde `FALSE` döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür. Bu `S_FALSE` özellik desteklenmiyorsa döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Çerçeve bir işleve eklenen satır içi bir yöntemi veya işlevi temsil ettiği için yığın çerçevesinin bir işlevin başlangıcı olması mümkün değildir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
