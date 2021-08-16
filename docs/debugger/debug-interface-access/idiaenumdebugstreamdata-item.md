---
description: Belirtilen kaydı alın.
title: IDiaEnumDebugStreamData::Item | Microsoft Docs
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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: b3bf851a1221aa2553827e015df81ea5d3b789c6fb935401a6a7e79c3a9e0f5d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121420867"
---
# <a name="idiaenumdebugstreamdataitem"></a>IDiaEnumDebugStreamData::Item
Belirtilen kaydı alın.

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

[in] Alınan kaydın dizini. Dizin 0 ile `count` -1 aralığındadır; burada `count` [IDiaEnumDebugStreamData::get_Count.](../../debugger/debug-interface-access/idiaenumdebugstreamdata-get-count.md)

 Cbdata

[in] Veri arabelleğinin bayt cinsinden boyutu.

 veri verisi

[out] Döndürülen bayt sayısını döndürür. ise, `data` `NULL` belirtilen `pcbData` kayıtta kullanılabilen toplam veri bayt sayısını içerir.

 data[]

[out] Hata ayıklama akışı kayıt verileriyle doldurulmuş bir arabellek.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür. Geçersiz `E_INVALIDARG` parametreler için ve parametresinin `index` sınırların dışında olması için döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)
- [IDiaEnumDebugStreamData::Next](../../debugger/debug-interface-access/idiaenumdebugstreamdata-next.md)
- [IDiaEnumDebugStreams::Item](../../debugger/debug-interface-access/idiaenumdebugstreams-item.md)
- [IDiaEnumDebugStreamData::get_Count](../../debugger/debug-interface-access/idiaenumdebugstreamdata-get-count.md)
- [IDiaEnumDebugStreamData::Skip](../../debugger/debug-interface-access/idiaenumdebugstreamdata-skip.md)
