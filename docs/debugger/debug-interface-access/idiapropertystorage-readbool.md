---
title: 'IDiaPropertyStorage:: ReadBOOL | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadBOOL
ms.assetid: ad1822db-4572-48f7-9919-f8137f6701f2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7d94e38ade7b44d7458a0918080214d00e0000aa
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85466611"
---
# <a name="idiapropertystoragereadbool"></a>IDiaPropertyStorage::ReadBOOL
`BOOL`Bir özellik kümesindeki değerleri okur.

## <a name="syntax"></a>Söz dizimi

```C++
HRESULT ReadBOOL ( 
   PROPID id,
   BOOL*  pValue
);
```

#### <a name="parameters"></a>Parametreler
 `id`

'ndaki Okunacak özelliğin tanımlayıcısı ( `PROPID` WTypes. h olarak bir olarak tanımlanır `ULONG` ).

 `pValue`

dışı Özellik değerini döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde bir hata kodu döndürür. `E_INVALIDARG`Özelliğin tür olup olmadığını döndürür `BOOL` .

## <a name="remarks"></a>Açıklamalar
 Tutarlı sonuçlar için `BOOL` değeri sıfır olmayan değerler ve sıfır olacak şekilde yorumlayın `TRUE` `FALSE` .

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)