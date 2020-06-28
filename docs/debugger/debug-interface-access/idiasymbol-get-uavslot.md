---
title: 'IDiaSymbol:: get_uavSlot | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: a70648f2-3b25-439f-8099-239ac602515a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c0d4afea1525a52453d83b804cfb06a95bce932c
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85461660"
---
# <a name="idiasymbolget_uavslot"></a>IDiaSymbol::get_uavSlot
Uıav yuvasını alır.

## <a name="syntax"></a>Söz dizimi

```C++
HRESULT get_uavSlot(
   DWORD* pRetVal);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı `DWORD`Uıav yuvasını tutan bir işaretçisi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, `S_FALSE` bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)