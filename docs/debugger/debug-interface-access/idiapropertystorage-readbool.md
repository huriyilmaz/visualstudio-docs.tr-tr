---
description: Bir özellik kümesinde BOOL değerlerini okur.
title: IDiaPropertyStorage::ReadBOOL | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadBOOL
ms.assetid: ad1822db-4572-48f7-9919-f8137f6701f2
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 2b7e04906d5e809538c5cb99b9b43d66701020b5d387ff3ab824367b72a94508
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121344999"
---
# <a name="idiapropertystoragereadbool"></a>IDiaPropertyStorage::ReadBOOL
Bir `BOOL` özellik kümesinde değerleri okur.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT ReadBOOL ( 
   PROPID id,
   BOOL*  pValue
);
```

#### <a name="parameters"></a>Parametreler
 `id`

[in] Okunacak özelliğin tanımlayıcısı ( `PROPID` WTypes.h içinde bir olarak `ULONG` tanımlanır).

 `pValue`

[out] Özellik değerini döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür. özelliği `E_INVALIDARG` türünde değilse `BOOL` döndürür.

## <a name="remarks"></a>Açıklamalar
 Tutarlı sonuçlar için, sıfır `BOOL` olmayan değerlerin ve sıfır değerinin olması için `TRUE` değeri yorumlun. `FALSE`

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)
