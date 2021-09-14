---
description: Bir özellik kümesinde LONG değerlerini okur.
title: IDiaPropertyStorage::ReadLONG | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadLONG
ms.assetid: 32054cbc-db55-4513-a1b4-de80e77aac8a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 5112970758a037754c61064ca073c79e950bafb4
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126629547"
---
# <a name="idiapropertystoragereadlong"></a>IDiaPropertyStorage::ReadLONG
Bir `LONG` özellik kümesinde değerleri okur.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT ReadDLONG ( 
   PROPID id,
   LONG*  pValue
);
```

#### <a name="parameters"></a>Parametreler
 `id`

[in] Okunacak özelliğin tanımlayıcısı ( `PROPID` WTypes.h içinde bir olarak `ULONG` tanımlanır).

 `pValue`

[out] Özellik değerini döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür. özelliği `E_INVALIDARG` türünde yoksa `LONG` döndürür.

## <a name="remarks"></a>Açıklamalar
 A, `LONG` 32 bit Windows bir tamsayı olarak tanımlanır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)
