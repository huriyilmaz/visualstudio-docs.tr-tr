---
description: Sabit Listesi dizisinde belirtilen sayıda hata ayıklama akışını atlar.
title: 'IDiaEnumDebugStreams:: Skip | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreams::Skip method
ms.assetid: 6ec7753c-d7af-4879-b107-1b3442e0b025
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8584a20a888bc0f0a33a1b53686e95422792a09f
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158108"
---
# <a name="idiaenumdebugstreamsskip"></a>IDiaEnumDebugStreams::Skip
Sabit Listesi dizisinde belirtilen sayıda hata ayıklama akışını atlar.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT Skip ( 
   ULONG celt
);
```

#### <a name="parameters"></a>Parametreler
 `celt`

'ndaki Atlanacak numaralandırma dizisindeki hata ayıklama akışlarının sayısı.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, öğesini döndürür `S_OK` ; Aksi takdirde, `S_FALSE` atlanacak daha fazla kayıt yoksa döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)
