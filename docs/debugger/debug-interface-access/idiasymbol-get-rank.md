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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 75e21d5af58d857f81d76bfa78af1d476f47f104
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85462520"
---
# <a name="idiasymbolget_rank"></a>IDiaSymbol::get_rank
Bir FORTRAN çok boyutlu dizisinin derecesini (boyut sayısı) alır.

## <a name="syntax"></a>Söz dizimi

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