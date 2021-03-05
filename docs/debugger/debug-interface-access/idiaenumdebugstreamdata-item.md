---
description: Belirtilen kaydı alır.
title: 'IDiaEnumDebugStreamData:: Item | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreamData::Item method
ms.assetid: 761e61a5-44a6-4d5d-a98e-c2e9b89d2343
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 22c03beccb60d4ef5848dbc973f3a67c2b0fade9
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102159462"
---
# <a name="idiaenumdebugstreamdataitem"></a>IDiaEnumDebugStreamData::Item
Belirtilen kaydı alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT Item ( 
   DWORD  index,
   DWORD  cbData,
   DWORD* pcbData,
   BYTE   data[]
);
```

#### <a name="parameters"></a>Parametreler
 dizin

'ndaki Alınacak kaydın dizini. Dizin 0 `count` -1 aralığında, burada `count` [IDiaEnumDebugStreamData:: get_Count](../../debugger/debug-interface-access/idiaenumdebugstreamdata-get-count.md)tarafından döndürülür.

 cbData

'ndaki Veri arabelleğinin bayt cinsinden boyutu.

 pcbData

dışı Döndürülen bayt sayısını döndürür. `data`İse `NULL` , `pcbData` Belirtilen kayıttaki toplam veri bayt sayısını içerir.

 veri []

dışı Hata ayıklama akışı kayıt verileriyle doldurulmuş bir arabellek.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür. `E_INVALIDARG`Geçersiz parametreler için döndürür ve `index` parametre sınırların dışında olur.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)
- [IDiaEnumDebugStreamData::Next](../../debugger/debug-interface-access/idiaenumdebugstreamdata-next.md)
- [IDiaEnumDebugStreams::Item](../../debugger/debug-interface-access/idiaenumdebugstreams-item.md)
- [IDiaEnumDebugStreamData::get_Count](../../debugger/debug-interface-access/idiaenumdebugstreamdata-get-count.md)
- [IDiaEnumDebugStreamData::Skip](../../debugger/debug-interface-access/idiaenumdebugstreamdata-skip.md)
