---
description: Uıav yuvasını alır.
title: 'IDiaSymbol:: get_uavSlot | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: a70648f2-3b25-439f-8099-239ac602515a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 33f3aa8e9897c1207e8b51c7f80d5a6d2bda21e9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122065991"
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

dışı `DWORD` Uıav yuvasını tutan bir işaretçisi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, `S_FALSE` bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
