---
description: Örnekleyici yuvasını alır.
title: 'IDiaSymbol:: get_samplerSlot | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 41c751ba-81be-4bd3-838f-8373fc146157
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f0b6ef05dd1d89328e079380381d8e5d06ed67dc
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102155791"
---
# <a name="idiasymbolget_samplerslot"></a>IDiaSymbol::get_samplerSlot
Örnekleyici yuvasını alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_samplerSlot(
   DWORD* pRetVal);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı `DWORD` Örnekleyici yuvasını tutan bir işaretçisi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, `S_FALSE` bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
