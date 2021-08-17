---
description: Bu simge için derleyiciye özgü tür tanımlayıcı değerlerinin dizisini döndürür.
title: IDiaSymbol::get_typeIds | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_typeIds method
ms.assetid: 5166e647-fde5-4efe-92bf-77f8ae3fbc9b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: b3e3cd29c1cb00cfa2c01f1061487ed6a75852e4c771656efa2cf3ae94d150f7
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121391651"
---
# <a name="idiasymbolget_typeids"></a>IDiaSymbol::get_typeIds
Bu simge için derleyiciye özgü tür tanımlayıcı değerlerinin dizisini döndürür.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_typeIds ( 
   DWORD  cTypeIds,
   DWORD* pcTypeIds,
   DWORD  typeIds[]
);
```

#### <a name="parameters"></a>Parametreler
 `cTypeIds`

[in] Verileri tutmak için arabelleğin boyutu.

 `pcTypeIds`

[out] Yazılan veya ise toplam tür `typeIds` `typeIds` tanımlayıcılarının `NULL` sayısını döndürür.

 `typeIds[]`

[out] Tür tanımlayıcıları ile doldurulması gereken bir dizi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde veya `S_FALSE` bir hata kodu döndürür.

> [!NOTE]
> dönüş `S_FALSE` değeri, özelliğin sembol için kullanılamaz olduğu anlamına gelir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
