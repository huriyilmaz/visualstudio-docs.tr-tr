---
description: FORTRAN dizisi boyutunun üst sınırlarını temsil eden bir simgeyi döndürür.
title: IDiaSymbol::get_upperBound | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_upperBound method
ms.assetid: a77dcafa-ea3f-45da-826d-8f9b4489a03f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: b2ccab028f5a3c152b4c5e313341fbf2ef47eb140876e5df1e45f1de0cecb84d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121379697"
---
# <a name="idiasymbolget_upperbound"></a>IDiaSymbol::get_upperBound
FORTRAN dizisi boyutunun üst sınırlarını temsil eden bir simgeyi döndürür.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_upperBound ( 
   IDiaSymbol** pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

[out] ForTRAN dizisi boyutunun üst sınırlarını temsil eden bir [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde veya `S_FALSE` bir hata kodu döndürür.

> [!NOTE]
> dönüş `S_FALSE` değeri, özelliğin sembol için kullanılamaz olduğu anlamına gelir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
