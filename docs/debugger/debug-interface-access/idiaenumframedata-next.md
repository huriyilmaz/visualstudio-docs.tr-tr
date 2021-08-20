---
description: Sabit Listesi dizisinde belirtilen sayıda çerçeve verisi öğesini alır.
title: 'IDiaEnumFrameData:: Next | Microsoft Docs'
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122134612"
---
# <a name="idiaenumframedatanext"></a>IDiaEnumFrameData::Next
Sabit Listesi dizisinde belirtilen sayıda çerçeve verisi öğesini alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT Next ( 
   ULONG           celt,
   IDiaFrameData** rgelt,
   ULONG*          pceltFetched
);
```

#### <a name="parameters"></a>Parametreler
 celt

'ndaki Alınacak Numaralandırıcı içindeki çerçeve verisi öğelerinin sayısı.

 rgelt

dışı İstenen çerçeve verisi öğeleriyle doldurulacak bir [ıaframedata](../../debugger/debug-interface-access/idiaframedata.md) nesneleri dizisi.

 Pceltfettiz

dışı Getirilen Numaralandırıcı içindeki çerçeve verisi öğelerinin sayısını döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` . `S_FALSE`Daha fazla kayıt yoksa döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
