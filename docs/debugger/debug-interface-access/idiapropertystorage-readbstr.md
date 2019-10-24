---
title: 'IDiaPropertyStorage:: ReadBSTR | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: ef0b5bac11a1bf3da7e8081f7ae24b6a7a6f1a71
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742926"
---
# <a name="idiapropertystoragereadbstr"></a>IDiaPropertyStorage::ReadBSTR
Bir özellik kümesindeki `BSTR` değerleri okur.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT ReadBSTR ( 
   PROPID id,
   BSTR*  pValue
);
```

#### <a name="parameters"></a>Parametreler
 `id`

'ndaki Okunacak özelliğin tanımlayıcısı (`PROPID` `ULONG` olarak WTypes. h içinde tanımlanmıştır).

 `pValue`

dışı Özellik değerini döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; Aksi takdirde bir hata kodu döndürür. Özellik `BSTR` türünde değilse `E_INVALIDARG` döndürür.

## <a name="remarks"></a>Açıklamalar
 @No__t_0, Windows tarafından sıfır ile sonlandırılmış geniş karakter dizesi olarak tanımlanır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)