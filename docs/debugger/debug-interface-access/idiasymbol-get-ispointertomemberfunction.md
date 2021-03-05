---
description: Bu sembolün bir üye işlevine yönelik bir işaretçi olup olmadığını belirtir.
title: 'IDiaSymbol:: get_isPointerToMemberFunction | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: aa9b5599-9602-41be-ab50-d84b90bee72f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 92bcde9b53cc03326aac1c122e1d2b2e20f08e67
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102156078"
---
# <a name="idiasymbolget_ispointertomemberfunction"></a>IDiaSymbol::get_isPointerToMemberFunction
Bu sembolün bir üye işlevine yönelik bir işaretçi olup olmadığını belirtir.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_isPointerToMemberFunction(
   BOOL* pRetVal);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı `BOOL` Bu simgenin bir üye işlevine yönelik bir işaretçi olup olmadığını belirten bir işaretçisi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, `S_FALSE` bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
