---
description: Numaralama dizisinde belirtilen sayıda çerçeve verisi öğelerini alan.
title: IDiaEnumFrameData::Next | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::Next method
ms.assetid: 546e2e23-efb2-425a-96a1-808c67c519fb
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 5a4ec2e800a0c5eac80832a1b878d2f63d1251e2b6f0e576fd750f3d1e5111de
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121380512"
---
# <a name="idiaenumframedatanext"></a>IDiaEnumFrameData::Next
Numaralama dizisinde belirtilen sayıda çerçeve verisi öğelerini alan.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT Next ( 
   ULONG           celt,
   IDiaFrameData** rgelt,
   ULONG*          pceltFetched
);
```

#### <a name="parameters"></a>Parametreler
 Celt

[in] Numaralayıcıda alınan çerçeve veri öğelerinin sayısı.

 Rgelt

[out] İstenen çerçeve veri öğeleriyle doldurulan [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) nesneleri dizisi.

 pceltFetched

[out] Getirili numaralayıcıda çerçeve veri öğelerinin sayısını döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür. Başka `S_FALSE` kayıt yoksa döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
