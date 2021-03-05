---
description: Bu sembolün bir veri üyesine yönelik bir işaretçi olup olmadığını belirtir.
title: 'IDiaSymbol:: get_isPointerToDataMember | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: ef17c737-242e-43e8-b7e1-2c3bc58cfcef
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 45dba4978f4ff06b77bb9216cc836e8eaec9f0e0
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102156092"
---
# <a name="idiasymbolget_ispointertodatamember"></a>IDiaSymbol::get_isPointerToDataMember
Bu sembolün bir veri üyesine yönelik bir işaretçi olup olmadığını belirtir.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_isPointerToDataMember(
   BOOL* pRetVal);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı `BOOL` Bu simgenin bir veri üyesine yönelik bir işaretçi olup olmadığını belirten bir işaretçisi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, `S_FALSE` bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
