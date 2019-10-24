---
title: 'IDiaEnumFrameData:: Skip | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: c49aaf1f648a52e1701088b6579eda55cde6c355
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744566"
---
# <a name="idiaenumframedataskip"></a>IDiaEnumFrameData::Skip
Bir numaralandırma dizisindeki belirtilen sayıda çerçeve verisi öğesini atlar.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT Skip ( 
   ULONG celt
);
```

#### <a name="parameters"></a>Parametreler
 celt

'ndaki Atlanacak numaralandırma dizisindeki çerçeve verisi öğelerinin sayısı.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK`döndürür; Aksi takdirde, atlanacak daha fazla kayıt yoksa `S_FALSE` döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)