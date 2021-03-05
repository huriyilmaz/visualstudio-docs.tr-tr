---
description: Kayıt türünü alır.
title: 'IDiaSymbol:: get_registerType | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: f1c98ab0-8aef-4a07-a686-28b8a54418ef
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1ec297ea8de8ef5fb12c70a33dcb4213d39d7d9f
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102155798"
---
# <a name="idiasymbolget_registertype"></a>IDiaSymbol::get_registerType
Kayıt türünü alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_registerType(
   DWORD* pRetVal);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı `DWORD` Kayıt türünü tutan bir işaretçisi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, `S_FALSE` bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
