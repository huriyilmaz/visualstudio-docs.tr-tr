---
description: Matrisin satır birincil olup olmadığını belirtir.
title: 'IDiaSymbol:: get_isMatrixRowMajor | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 36b1e881-ea76-48b0-b67f-e9eb0d19bec7
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5d96dcde53bf09d8705964e9c01e2d6ca650f744
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102156183"
---
# <a name="idiasymbolget_ismatrixrowmajor"></a>IDiaSymbol::get_isMatrixRowMajor
Matrisin satır birincil olup olmadığını belirtir.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_isMatrixRowMajor(
   BOOL* pRetVal);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı `BOOL` Matrisin satır birincil olup olmadığını belirten bir işaretçisi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, `S_FALSE` bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
