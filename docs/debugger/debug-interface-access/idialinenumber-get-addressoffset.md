---
title: 'IDiaLineNumber:: get_addressOffset | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_addressOffset method
ms.assetid: 3bcb5500-b26c-4d3c-9d81-0a389a3715c3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b99addc04a7b9dc2f2b77d1943605f8c24af6aa7
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743278"
---
# <a name="idialinenumberget_addressoffset"></a>IDiaLineNumber::get_addressOffset
Bir bloğun başladığı bellek adresinin konum kısmını alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_addressOffset ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı Bir bloğun başladığı bellek adresinin konum parçasını döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür. Bu özellik desteklenmiyorsa `S_FALSE` döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="example"></a>Örnek

```C++
CComPtr< IDiaLineNumber > pLine;
DWORD offset;
pLine->get_addressOffset( &offset);
```

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)
- [IDiaLineNumber::get_addressSection](../../debugger/debug-interface-access/idialinenumber-get-addresssection.md)