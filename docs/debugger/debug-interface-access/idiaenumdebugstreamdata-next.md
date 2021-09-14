---
description: Numaralandırılmış dizide belirtilen sayıda kaydı alır.
title: 'IDiaEnumDebugStreamData:: Next | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreamData::Next method
ms.assetid: 114171dd-38fd-4bd7-a702-8ff887ffc99b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 8b67d12b983ef13ad92ee8a121d8733d435f7b7c
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126630428"
---
# <a name="idiaenumdebugstreamdatanext"></a>IDiaEnumDebugStreamData::Next
Numaralandırılmış dizide belirtilen sayıda kaydı alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT Next ( 
   ULONG  celt,
   DWORD  cbData,
   DWORD* pcbData,
   BYTE   data[],
   ULONG* pceltFetched
);
```

#### <a name="parameters"></a>Parametreler
 celt

'ndaki Alınacak kayıt sayısı.

 cbData

'ndaki Veri arabelleğinin bayt cinsinden boyutu.

 pcbData

dışı Döndürülen bayt sayısını döndürür. `data`Null ise, `pcbData` Tüm istenen kayıtlar için kullanılabilir olan toplam veri baytı sayısını içerir.

 veri []

dışı Hata ayıklama akışı kayıt verileriyle doldurulacak bir arabellek.

 Pceltfettiz

[in, out] İçindeki kayıt sayısını döndürür `data` .

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` . `S_FALSE`Daha fazla kayıt yoksa döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)
- [IDiaEnumDebugStreams::Next](../../debugger/debug-interface-access/idiaenumdebugstreams-next.md)
