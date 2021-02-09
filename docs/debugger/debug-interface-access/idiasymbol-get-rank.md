---
title: 'IDiaSymbol:: get_rank | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_rank method
ms.assetid: 14cc9c4b-a5ec-414a-b01f-4a142c17b7cc
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: da00422a5a12a12f99cf706b0bf7bb2ce623d76f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99853683"
---
# <a name="idiasymbolget_rank"></a>IDiaSymbol::get_rank
Bir FORTRAN çok boyutlu dizisinin derecesini (boyut sayısı) alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_rank ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı Bir FORTRAN çok boyutlu dizisindeki boyut sayısını döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, `S_FALSE` bir hata kodu döndürür.

> [!NOTE]
> Dönüş değeri, `S_FALSE` özelliğin sembol için kullanılamadığı anlamına gelir.

## <a name="remarks"></a>Açıklamalar
 Rank, dizinin olarak bildirildiği bir dizideki boyut sayısını ifade eder `myarray[1,2,3]` . Bu örnekte 3 ve 3 boyutlu bir sıralama vardır. Sıralama, her boyut için dizi dizisi kavramını kullanan C++ için geçerlidir (yani, `myarray[1][2][3]` ).

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)