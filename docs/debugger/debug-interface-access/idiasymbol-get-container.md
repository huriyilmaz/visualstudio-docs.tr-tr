---
title: 'IDiaSymbol:: get_container | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_container method
ms.assetid: 24e832eb-80b3-484c-a41b-11477ec9de99
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0533eb2cdea1dd3e1bea3d64e2b94ce29a09353d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740775"
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

dışı Bu sembolün kapsayıcısı hakkında bilgi içeren `IDiaSymbol` bir işaretçi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, S_OK döndürür; Aksi takdirde, S_FALSE veya bir hata kodu döndürür.

> [!NOTE]
> S_FALSE dönüş değeri, özelliğin simge için kullanılamadığı anlamına gelir.

## <a name="requirements"></a>Gereksinimler

|Gereksinim|Açıklama|
|-----------------|-----------------|
|Üst bilgi|dia2. h|
|Sürüm:|DIA SDK v 8.0|

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)