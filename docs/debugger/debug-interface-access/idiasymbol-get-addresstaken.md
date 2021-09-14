---
description: Başka bir sembolün bu sembolün adresine başvurup başvura olmadığını belirten bir bayrak verir.
title: IDiaSymbol::get_addressTaken | Microsoft Docs
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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 132fa45ef2ab2adb4a79283742bf9a566aa7a59e
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725471"
---
# <a name="idiasymbolget_addresstaken"></a>IDiaSymbol::get_addressTaken
Başka bir sembolün bu sembolün adresine başvurup başvura olmadığını belirten bir bayrak verir.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_addressTaken ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

[out] Başka `TRUE` bir sembol bu adrese başvurursa döndürür; aksi takdirde `FALSE` döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde veya `S_FALSE` bir hata kodu döndürür.

> [!NOTE]
> dönüş `S_FALSE` değeri, özelliğin sembol için kullanılamaz olduğu anlamına gelir.

## <a name="example"></a>Örnek
 Aşağıdaki örnekte, `B` `A` başvurur. Bu nedenle sembol `A` metodu `get_addressTaken` `TRUE` döndürür.

```C++
int A  = 0;
int* B = &A;
```

## <a name="requirements"></a>Gereksinimler

|Gereksinim|Açıklama|
|-----------------|-----------------|
|Üstbilgi:|dia2.h|
|Sürüm:|DIA SDK v7.0|

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
