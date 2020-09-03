---
title: 'IDiaSymbol:: get_isOptimizedAway | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: c18b1e38-b152-4a13-aba0-59faded5b2e6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a78d1d11fcc03901a3c2ac6607b5ba50fc2a9c72
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85463304"
---
# <a name="idiasymbolget_isoptimizedaway"></a>IDiaSymbol::get_isOptimizedAway
Değişkenin en iyi duruma getirilip getirilmediğini belirtir.

## <a name="syntax"></a>Söz dizimi

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