---
title: 'IDiaEnumDebugStreams:: Next | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreams::Next method
ms.assetid: eb8eae5a-be27-45f4-a7bd-6e4ef0652385
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 63b66729192c9c976ecd226ab21aad73b94bf9f2
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744723"
---
# <a name="idiaenumdebugstreamsnext"></a>IDiaEnumDebugStreams::Next
Sabit Listesi dizisinde belirtilen sayıda hata ayıklama akışı alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT Next ( 
   ULONG                     celt,
   IDiaEnumDebugStreamData** rgelt,
   ULONG*                    pceltFetched
);
```

#### <a name="parameters"></a>Parametreler
 celt

'ndaki Alınacak Numaralandırıcı içindeki hata ayıklama akışlarının sayısı.

 rgelt

dışı Alınmakta olan hata ayıklama akışlarını temsil eden [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md) nesnelerinin bir dizisini döndürür.

 Pceltfettiz

dışı Döndürülen hata ayıklama akışlarının sayısını döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür. Daha fazla akış yoksa `S_FALSE` döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)