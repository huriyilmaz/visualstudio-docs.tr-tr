---
description: Sembolün dizi dizin türü tanımlayıcısını döndürür.
title: IDiaSymbol::get_arrayIndexTypeId | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_arrayIndexTypeId method
ms.assetid: 124f86e2-6f66-4541-87c3-799f435b731e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: c38a0529ca0e93e0924b9afc2805b57f159d73e5
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122074511"
---
# <a name="idiasymbolget_arrayindextypeid"></a>IDiaSymbol::get_arrayIndexTypeId
Sembolün dizi dizin türü tanımlayıcısını döndürür.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_arrayIndexTypeId ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

[out] Sembolün dizi dizin türü kimliğini döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde veya `S_FALSE` bir hata kodu döndürür.

> [!NOTE]
> dönüş `S_FALSE` değeri, özelliğin sembol için kullanılamaz olduğu anlamına gelir.

## <a name="remarks"></a>Açıklamalar
 Tanımlayıcı, tüm sembolleri benzersiz olarak işaretlemek DIA SDK tarafından oluşturulan benzersiz bir değerdir.

## <a name="requirements"></a>Gereksinimler

|Gereksinim|Açıklama|
|-----------------|-----------------|
|Üstbilgi:|dia2.h|
|Sürüm:|DIA SDK v7.0|

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
