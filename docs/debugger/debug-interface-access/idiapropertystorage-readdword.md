---
description: Bir özellik kümesinde DWORD değerlerini okur.
title: IDiaPropertyStorage::ReadDWORD | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadDWORD
ms.assetid: 5f4c034e-a9d3-4560-94b5-ede524741439
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 58b51638b742fa8dfe874c4d46ff7bd0894f7766
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122161704"
---
# <a name="idiapropertystoragereaddword"></a>IDiaPropertyStorage::ReadDWORD
Bir `DWORD` özellik kümesinde değerleri okur.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT ReadDWORD ( 
   PROPID id,
   DWORD* pValue
);
```

#### <a name="parameters"></a>Parametreler
 `id`

[in] Okunacak özelliğin tanımlayıcısı ( `PROPID` WTypes.h içinde bir olarak `ULONG` tanımlanır).

 `pValue`

[out] Özellik değerini döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür. özelliği `E_INVALIDARG` türünde değilse `DWORD` döndürür.

## <a name="remarks"></a>Açıklamalar
 , 32 bit Windows bir tamsayı `DWORD` olarak tanımlanır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)
