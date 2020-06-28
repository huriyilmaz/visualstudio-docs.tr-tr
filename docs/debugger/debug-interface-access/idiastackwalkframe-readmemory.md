---
title: 'IDiaStackWalkFrame:: readMemory | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: f682f3fe0e300f84dc28b959497138a5019f954b
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85464830"
---
# <a name="idiastackwalkframereadmemory"></a>IDiaStackWalkFrame::readMemory
Görüntüden belleği okur.

## <a name="syntax"></a>Söz dizimi

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

dışı Döndürülen bayt sayısını döndürür. `data`İse `NULL` , `pcbData` kullanılabilir verilerin toplam bayt sayısını içerir.

 `data`

dışı Belirtilen konumdan alınan verilerle doldurulacak bir arabellek.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)