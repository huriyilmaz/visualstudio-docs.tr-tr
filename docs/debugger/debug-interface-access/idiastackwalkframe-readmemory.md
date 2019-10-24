---
title: 'IDiaStackWalkFrame:: readMemory | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame::readMemory method
ms.assetid: 7ab0b525-a5a7-4692-acad-e8c00fa9ab9a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ae1201fca1fc25cce19b40b47d6435d02d80e1b4
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741474"
---
# <a name="idiastackwalkframereadmemory"></a>IDiaStackWalkFrame::readMemory
Görüntüden belleği okur.

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

'ndaki Erişim için bellek türünü belirten [MemoryTypeEnum sabit](../../debugger/debug-interface-access/memorytypeenum.md) listesi değerlerinden biri.

 `va`

'ndaki Okumaya başlamak için görüntüdeki sanal adres konumu.

 `cbData`

'ndaki Veri arabelleğinin bayt cinsinden boyutu.

 `pcbData`

dışı Döndürülen bayt sayısını döndürür. `data` `NULL`, `pcbData` toplam kullanılabilir veri baytı sayısını içerir.

 `data`

dışı Belirtilen konumdan alınan verilerle doldurulacak bir arabellek.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK`döndürür; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)