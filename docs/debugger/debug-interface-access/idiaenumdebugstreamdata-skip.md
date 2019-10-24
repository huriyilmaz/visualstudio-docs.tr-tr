---
title: 'IDiaEnumDebugStreamData:: Skip | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreamData::Skip method
ms.assetid: 106ae1d3-a379-4077-babf-2665e697b0c4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f2f331d7a91e9dbc6dbf0dea2e8a5b91f08de584
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744835"
---
# <a name="idiaenumdebugstreamdataskip"></a>IDiaEnumDebugStreamData::Skip
Numaralandırılmış bir dizide belirtilen sayıda kaydı atlar.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT Skip ( 
   ULONG celt
);
```

#### <a name="parameters"></a>Parametreler
 celt

'ndaki Numaralandırılmış dizide atlanacak kayıt sayısı.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; Aksi takdirde, atlanacak daha fazla kayıt yoksa `S_FALSE` döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)