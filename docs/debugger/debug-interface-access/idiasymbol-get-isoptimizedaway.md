---
description: Değişkenin en iyi duruma getirilip getirilmediğini belirtir.
title: 'IDiaSymbol:: get_isOptimizedAway | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: c18b1e38-b152-4a13-aba0-59faded5b2e6
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6612294caa40fd885690cce3f40f7d49ffa65c5c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102156148"
---
# <a name="idiasymbolget_isoptimizedaway"></a>IDiaSymbol::get_isOptimizedAway
Değişkenin en iyi duruma getirilip getirilmediğini belirtir.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_isOptimizedAway(
   BOOL* pRetVal);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı `BOOL` Değişkenin en iyi duruma getirilip getirilmeyeceğini belirten bir işaretçisi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, `S_FALSE` bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
