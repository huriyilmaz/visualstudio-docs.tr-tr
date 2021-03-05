---
description: Bu satır bilgisinin program kaynağında bir ifade yerine bir deyimin başlangıcını açıkladığını belirten bir bayrak alır.
title: 'IDiaLineNumber:: get_statement | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_statement method
ms.assetid: 22b8ee29-79ef-427f-bd05-00d255ab836b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e6c36852f5aa48bcd5146419415dd06ec9d0a847
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102157449"
---
# <a name="idialinenumberget_statement"></a>IDiaLineNumber::get_statement
Bu satır bilgisinin program kaynağında bir ifade yerine bir deyimin başlangıcını açıkladığını belirten bir bayrak alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_statement ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı `TRUE` Bu satır bilgisinin program kaynağındaki bir deyimin başlangıcını açıkladıysanız döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` . `S_FALSE`Bu özellik desteklenmiyorsa döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Deyimler birden çok satıra yayılabilir. Bu yöntem, ilişkili satır numarasının böyle bir çok satırlı deyimin başlangıcını işaretlemeyeceğini gösterir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)
