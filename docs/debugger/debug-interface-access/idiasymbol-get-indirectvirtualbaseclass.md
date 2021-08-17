---
description: Kullanıcı tanımlı veri türünün dolaylı bir sanal temel sınıf olup olmadığını belirten bir bayrağını alın.
title: IDiaSymbol::get_indirectVirtualBaseClass | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_indirectVirtualBaseClass method
ms.assetid: 853b5c6f-e1cb-4675-ad36-9ee16e3341c3
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 06a308af7d62672e8d130ff09bae3d561047870e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122058733"
---
# <a name="idiasymbolget_indirectvirtualbaseclass"></a>IDiaSymbol::get_indirectVirtualBaseClass
Kullanıcı tanımlı veri türünün dolaylı bir sanal temel sınıf olup olmadığını belirten bir bayrağını alın.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_indirectVirtualBaseClass ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

[out] Kullanıcı `TRUE` tanımlı veri türü dolaylı bir sanal temel sınıfsa döndürür; aksi takdirde `FALSE` döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde veya `S_FALSE` hata kodu döndürür.

> [!NOTE]
> dönüş `S_FALSE` değeri, özelliğin sembol için kullanılamaz olduğu anlamına gelir.

## <a name="requirements"></a>Gereksinimler

|Gereksinim|Açıklama|
|-----------------|-----------------|
|Üstbilgi:|dia2.h|
|Sürüm:|DIA SDK v7.0|

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
