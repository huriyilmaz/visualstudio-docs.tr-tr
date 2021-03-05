---
description: Benzersiz sembol tanımlayıcısını alır.
title: 'IDiaSymbol:: get_symIndexId | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_symIndexId method
ms.assetid: dd1fb3ba-31bf-497d-a6bf-79f1206e6642
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 89edbd90e8577849f00bfe2661f6ad4f6abb181a
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102155742"
---
# <a name="idiasymbolget_symindexid"></a>IDiaSymbol::get_symIndexId
Benzersiz sembol tanımlayıcısını alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_symIndexId ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı Simgenin sembol KIMLIĞINI döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, döndürür `S_FALSE` veya hata kodu döndürür.

> [!NOTE]
> Dönüş değeri, `S_FALSE` özelliğin sembol için kullanılamadığı anlamına gelir.

## <a name="remarks"></a>Açıklamalar
 Tanımlayıcı, tüm sembolleri benzersiz olarak işaretlemek için DIA SDK tarafından oluşturulan benzersiz bir değerdir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
