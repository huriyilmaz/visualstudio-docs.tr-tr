---
description: Bu işlev, bu sembolün üst/kapsayıcısını temsil eden bir simgeye yönelik bir işaretçi alır.
title: 'IDiaSymbol:: get_container | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_container method
ms.assetid: 24e832eb-80b3-484c-a41b-11477ec9de99
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 724127e50708585613175b0f5773f231f1b33944
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102156386"
---
# <a name="idiasymbolget_container"></a>IDiaSymbol::get_container
Bu işlev, bu sembolün üst/kapsayıcısını temsil eden bir simgeye yönelik bir işaretçi alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_container(
   IDiaSymbol **pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı `IDiaSymbol` Bu sembolün kapsayıcısı hakkında içeren bir bilgi için bir işaretçi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa S_OK döndürür; Aksi takdirde, S_FALSE veya bir hata kodu döndürür.

> [!NOTE]
> S_FALSE dönüş değeri, özelliğin simge için kullanılamadığı anlamına gelir.

## <a name="requirements"></a>Gereksinimler

|Gereksinim|Açıklama|
|-----------------|-----------------|
|Üst bilgi|dia2. h|
|Sürüm:|DIA SDK v 8.0|

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
