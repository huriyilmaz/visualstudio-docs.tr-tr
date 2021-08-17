---
description: Numaralandı dizisinde belirtilen sayıda kaydı alan.
title: IDiaEnumDebugStreamData::Next | Microsoft Docs
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
ms.openlocfilehash: cf76783b9a9dbe642d1a641505539ccee208e2c588210e6d1102ea32fda4b7e9
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121455250"
---
# <a name="idiaenumdebugstreamdatanext"></a>IDiaEnumDebugStreamData::Next
Numaralandı dizisinde belirtilen sayıda kaydı alan.

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
 Celt

[in] Alınarak alınan kayıt sayısı.

 Cbdata

[in] Veri arabelleğinin bayt cinsinden boyutu.

 veri verisi

[out] Döndürülen bayt sayısını döndürür. NULL `data` ise, istenen `pcbData` tüm kayıtlar için kullanılabilen toplam veri bayt sayısını içerir.

 data[]

[out] Hata ayıklama akışı kayıt verileriyle doldurulacak bir arabellek.

 pceltFetched

[in, out] içinde kayıt sayısını `data` döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür. Başka `S_FALSE` kayıt yoksa döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)
- [IDiaEnumDebugStreams::Next](../../debugger/debug-interface-access/idiaenumdebugstreams-next.md)
