---
title: 'IDiaEnumFrameData:: Skip | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::Skip method
ms.assetid: 67140b4c-7125-4895-932d-42412326da29
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 02c56c0b49844b72384d641a53eb513c2a504acb
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85468310"
---
# <a name="idiaenumframedataskip"></a>IDiaEnumFrameData::Skip
Bir numaralandırma dizisindeki belirtilen sayıda çerçeve verisi öğesini atlar.

## <a name="syntax"></a>Söz dizimi

```C++
HRESULT Skip ( 
   ULONG celt
);
```

#### <a name="parameters"></a>Parametreler
 celt

'ndaki Atlanacak numaralandırma dizisindeki çerçeve verisi öğelerinin sayısı.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, öğesini döndürür `S_OK` ; Aksi takdirde, `S_FALSE` atlanacak daha fazla kayıt yoksa döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)