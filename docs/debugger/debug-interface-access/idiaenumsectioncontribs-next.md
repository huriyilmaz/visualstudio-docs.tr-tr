---
description: Numaralama dizisinde belirtilen sayıda bölüm katkısını alma.
title: IDiaEnumSectionContribs::Next | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSectionContribs::Next method
ms.assetid: a6bb2adb-ee6d-4f3c-ab5b-e89361c8880e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 66771f984a5ba0ed7e6061dc133768e7fbd959a7c273cd273bb299a424900063
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121392483"
---
# <a name="idiaenumsectioncontribsnext"></a>IDiaEnumSectionContribs::Next
Numaralama dizisinde belirtilen sayıda bölüm katkısını alma.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT Next( 
   ULONG                celt,
   IDiaSectionContrib** rgelt,
   ULONG*               pceltFetched
);
```

#### <a name="parameters"></a>Parametreler
 Celt

[in] Numaralayıcıda alınan bölüm katkılarının sayısı.

 Rgelt

[out] İstenen bölüm katkılarını temsil eden [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md) nesneleriyle doldurulması gereken bir dizi.

 pceltFetched

[out] Numaralayıcıda alınan bölüm katkılarının sayısını döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür. Başka `S_FALSE` bölüm katkısı yoksa döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)
