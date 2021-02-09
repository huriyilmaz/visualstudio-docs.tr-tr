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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ffd85fd1a6878fd378931901098d90f2a24c8ccc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99854803"
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

dışı Döndürülen bayt sayısını döndürür. `data`İse `NULL` , `pcbData` kullanılabilir verilerin toplam bayt sayısını içerir.

 `data`

dışı Belirtilen konumdan alınan verilerle doldurulacak bir arabellek.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)