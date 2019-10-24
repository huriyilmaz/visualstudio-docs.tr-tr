---
title: 'IDiaSymbol:: get_intrinsic | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_intrinsic method
ms.assetid: f969f595-d9f9-48b9-adaa-63a6e4e09575
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7a300cd39e85e84ee3a008f3dc011ddcccb6ce5e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740359"
---
# <a name="idiasymbolget_intrinsic"></a>IDiaSymbol::get_intrinsic
Bir sınıfın içsel bir tür olup olmadığını belirten bir bayrak alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_intrinsic( 
   BOOL* pRetVal)
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı Sınıf içsel bir tür ise `TRUE` döndürür; Aksi takdirde, `FALSE` döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; Aksi takdirde, `S_FALSE` veya bir hata kodu döndürür.

> [!NOTE]
> @No__t_0 dönüş değeri özelliğin sembol için kullanılamadığı anlamına gelir.

## <a name="remarks"></a>Açıklamalar

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: dia2. h

 Kitaplık: diaguid. lib

 DLL: msdia100. dll

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)