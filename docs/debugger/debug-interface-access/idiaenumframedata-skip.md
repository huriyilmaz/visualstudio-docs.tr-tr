---
description: Bir numaralama dizisinde belirtilen sayıda çerçeve verisi öğelerini atlar.
title: IDiaEnumFrameData::Skip | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::Skip method
ms.assetid: 67140b4c-7125-4895-932d-42412326da29
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 50c7069e47533e65273ffd988eed676a59376a1e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122134588"
---
# <a name="idiaenumframedataskip"></a>IDiaEnumFrameData::Skip
Bir numaralama dizisinde belirtilen sayıda çerçeve verisi öğelerini atlar.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT Skip ( 
   ULONG celt
);
```

#### <a name="parameters"></a>Parametreler
 Celt

[in] Atlama için numaralama dizisinde çerçeve veri öğelerinin sayısı.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa; `S_OK` aksi takdirde, `S_FALSE` atlanabilecek başka kayıt yoksa döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)
