---
title: 'IDiaSymbol:: get_uavSlot | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: a70648f2-3b25-439f-8099-239ac602515a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 077a0a7895e93714bfe7b64b658c59f4d38ead4e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739044"
---
# <a name="idiasymbolget_uavslot"></a>IDiaSymbol::get_uavSlot
Uıav yuvasını alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_uavSlot(
   DWORD* pRetVal);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı Uıav yuvasını tutan `DWORD` için bir işaretçi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; Aksi takdirde, `S_FALSE` veya bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)