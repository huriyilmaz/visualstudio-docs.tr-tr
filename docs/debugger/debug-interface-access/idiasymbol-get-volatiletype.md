---
description: Kullanıcı tanımlı veri türünün (UDT) geçici olup olmadığını belirten bir bayrak alınır.
title: IDiaSymbol::get_volatileType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_volatileType method
ms.assetid: 19782a4d-40a8-467b-ab7d-58bc4d812309
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 3bfde9541f787d3c573880c94f7d4b62ea09e8f7babb6c7aa7eed3a2dcb9f404
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121240451"
---
# <a name="idiasymbolget_volatiletype"></a>IDiaSymbol::get_volatileType
Kullanıcı tanımlı veri türünün (UDT) geçici olup olmadığını belirten bir bayrak alınır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_volatileType ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

[out] `TRUE` UDT geçici ise döndürür; aksi takdirde `FALSE` döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde veya `S_FALSE` bir hata kodu döndürür.

> [!NOTE]
> dönüş `S_FALSE` değeri, özelliğin sembol için kullanılamaz olduğu anlamına gelir.

## <a name="remarks"></a>Açıklamalar
 C++ içinde bir UDT anahtar sözcüğüyle işaretlenir ve içeriğinin bir erişimden sonrakine var `volatile` olduğu varsayılamaz.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
