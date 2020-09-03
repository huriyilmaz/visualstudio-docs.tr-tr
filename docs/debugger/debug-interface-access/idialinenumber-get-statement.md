---
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3ea4a05bfccddeedb29110ea6ee44f34f85534a8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85466849"
---
# <a name="idialinenumberget_statement"></a>IDiaLineNumber::get_statement
Bu satır bilgisinin program kaynağında bir ifade yerine bir deyimin başlangıcını açıkladığını belirten bir bayrak alır.

## <a name="syntax"></a>Söz dizimi

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