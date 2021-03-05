---
description: Başka bir simgenin bu simgenin adresine başvuruda bulunup bulunmadığını gösteren bir bayrak alır.
title: 'IDiaSymbol:: get_addressTaken | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_addressTaken method
ms.assetid: 0d366188-f5e1-4226-b392-58c09539d097
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2db653509b0afa40f3b59e1a4a6232763da6ef1f
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102156568"
---
# <a name="idiasymbolget_addresstaken"></a>IDiaSymbol::get_addressTaken
Başka bir simgenin bu simgenin adresine başvuruda bulunup bulunmadığını gösteren bir bayrak alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_addressTaken ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı `TRUE` Başka bir simgenin bu adrese başvuruyorsa döndürür; Aksi takdirde, döndürür `FALSE` .

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, `S_FALSE` bir hata kodu döndürür.

> [!NOTE]
> Dönüş değeri, `S_FALSE` özelliğin simge için kullanılamadığı anlamına gelir.

## <a name="example"></a>Örnek
 Aşağıdaki örnekte, `B` başvuruları `A` . Bu nedenle, `A` simgenin `get_addressTaken` yöntemi döndürür `TRUE` .

```C++
int A  = 0;
int* B = &A;
```

## <a name="requirements"></a>Gereksinimler

|Gereksinim|Açıklama|
|-----------------|-----------------|
|Üst bilgi|dia2. h|
|Sürüm:|DIA SDK v 7.0|

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
