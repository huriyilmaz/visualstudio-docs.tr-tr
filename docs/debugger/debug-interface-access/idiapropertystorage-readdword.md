---
title: 'IDiaPropertyStorage:: ReadDWORD | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadDWORD
ms.assetid: 5f4c034e-a9d3-4560-94b5-ede524741439
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1764ec83a69dcc5daff267767594473bf690b341
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742904"
---
# <a name="idiapropertystoragereaddword"></a>IDiaPropertyStorage::ReadDWORD
Bir özellik kümesindeki `DWORD` değerleri okur.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT ReadDWORD ( 
   PROPID id,
   DWORD* pValue
);
```

#### <a name="parameters"></a>Parametreler
 `id`

'ndaki Okunacak özelliğin tanımlayıcısı (`PROPID` `ULONG` olarak WTypes. h içinde tanımlanmıştır).

 `pValue`

dışı Özellik değerini döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; Aksi takdirde bir hata kodu döndürür. Özellik `DWORD` türünde değilse `E_INVALIDARG` döndürür.

## <a name="remarks"></a>Açıklamalar
 @No__t_0, Windows tarafından 32 bitlik işaretsiz tamsayı olarak tanımlanır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)