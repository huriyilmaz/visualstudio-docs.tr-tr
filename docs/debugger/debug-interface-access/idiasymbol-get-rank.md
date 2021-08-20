---
description: ForTRAN çok boyutlu dizisinin derecesini (boyut sayısı) alır.
title: IDiaSymbol::get_rank | Microsoft Docs
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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 03c61eea4e46f1e9223ee296f8728e8f4284bf31
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122105436"
---
# <a name="idiasymbolget_rank"></a>IDiaSymbol::get_rank
ForTRAN çok boyutlu dizisinin derecesini (boyut sayısı) alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_rank ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

[out] BIR FORTRAN çok boyutlu dizisinde boyut sayısını döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde veya `S_FALSE` bir hata kodu döndürür.

> [!NOTE]
> dönüş `S_FALSE` değeri, özelliğin sembol için kullanılamaz olduğu anlamına gelir.

## <a name="remarks"></a>Açıklamalar
 Derece, dizisinin olarak bildir olduğu bir dizide boyut sayısını ifade `myarray[1,2,3]` eder. Bu örnekte 3 ve 3 boyut derecesi vardır. Sıralama, her boyut için dizi dizisi kavramını kullanan C++ için geçerli değildir (yani `myarray[1][2][3]` ).

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
