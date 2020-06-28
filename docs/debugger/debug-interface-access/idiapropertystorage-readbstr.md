---
title: 'IDiaPropertyStorage:: ReadBSTR | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadBSTR
ms.assetid: 7214643b-3286-48ed-90aa-0fe95b4cae5b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c6e87c2ed168a262fc1a12f06fc6a18bcf73e7bc
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85466597"
---
# <a name="idiapropertystoragereadbstr"></a>IDiaPropertyStorage::ReadBSTR
`BSTR`Bir özellik kümesindeki değerleri okur.

## <a name="syntax"></a>Söz dizimi

```C++
HRESULT ReadBSTR ( 
   PROPID id,
   BSTR*  pValue
);
```

#### <a name="parameters"></a>Parametreler
 `id`

'ndaki Okunacak özelliğin tanımlayıcısı ( `PROPID` WTypes. h olarak bir olarak tanımlanır `ULONG` ).

 `pValue`

dışı Özellik değerini döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde bir hata kodu döndürür. `E_INVALIDARG`Özelliğin tür olup olmadığını döndürür `BSTR` .

## <a name="remarks"></a>Açıklamalar
 `BSTR`, Windows tarafından sıfır ile sonlandırılmış geniş karakter dizesi olarak tanımlanır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)