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
ms.openlocfilehash: 57324a0ec9b82ff0b32f16ebf32f8d3ee9e19fb5
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126630326"
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
