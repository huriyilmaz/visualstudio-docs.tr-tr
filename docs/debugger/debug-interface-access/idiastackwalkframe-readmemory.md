---
description: Görüntüden bellek okur.
title: IDiaStackWalkFrame::readMemory | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame::readMemory method
ms.assetid: 7ab0b525-a5a7-4692-acad-e8c00fa9ab9a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: de206ac94a03d6f50d301fed84067e56dbc88a30
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122074655"
---
# <a name="idiastackwalkframereadmemory"></a>IDiaStackWalkFrame::readMemory
Görüntüden bellek okur.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT readMemory ( 
   MemoryTypeEnum type,
   ULONGLONG va,
   DWORD     cbData,
   DWORD*    pcbData,
   BYTE      data[]
);
```

#### <a name="parameters"></a>Parametreler
 `type`

[in] Erişilen [bellek türü belirten MemoryTypeEnum](../../debugger/debug-interface-access/memorytypeenum.md) Enum Numaralama değerlerinden biri.

 `va`

[in] Okumaya başlamak için görüntüde sanal adres konumu.

 `cbData`

[in] Veri arabelleğinin bayt cinsinden boyutu.

 `pcbData`

[out] Döndürülen bayt sayısını döndürür. ise, `data` kullanılabilir toplam veri bayt sayısını `NULL` `pcbData` içerir.

 `data`

[out] Belirtilen konumdaki verilerle doldurulacak bir arabellek.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)
