---
description: Yürütülebilir dosyanın görüntüsünden bellekte bir veri bloğu okur.
title: IDiaStackWalkHelper::readMemory | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::readMemory method
ms.assetid: e1eb90aa-49b7-476c-9e70-7e8f08994cbe
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 22507fb6fdc072c643675a8e99b6a578c9380118
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122036346"
---
# <a name="idiastackwalkhelperreadmemory"></a>IDiaStackWalkHelper::readMemory
Yürütülebilir dosyanın görüntüsünden bellekte bir veri bloğu okur.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT readMemory( 
   enum MemoryTypeEnum type,
   ULONGLONG           va,
   DWORD               cbData,
   DWORD*              pcbData,
   BYTE*               pbData
);
```

#### <a name="parameters"></a>Parametreler
 `type`

[in] Okunan bellek [türünü belirten MemoryTypeEnum](../../debugger/debug-interface-access/memorytypeenum.md) Enum Numaralama enumerasyonundan bir değer.

 Va

[in] Görüntüde okumaya başlanacak sanal adres.

 `cbData`

[in] Veri arabelleğinin bayt cinsinden boyutu.

 `pcbData`

[out] Gerçekte okunan bayt sayısını döndürür. ise, `pbData` kullanılabilir verilerin toplam bayt `NULL` sayısıdır.

 `pbData`

[in, out] Okunan bellekle doldurulmuş bir arabellek.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [MemoryTypeEnum Numaralandırması](../../debugger/debug-interface-access/memorytypeenum.md)
