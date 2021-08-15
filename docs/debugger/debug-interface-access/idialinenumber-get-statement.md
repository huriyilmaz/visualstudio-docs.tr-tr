---
description: Bu satır bilgisinin program kaynağında bir ifade yerine bir deyimin başlangıcını açık olduğunu belirten bir bayrak alınır.
title: IDiaLineNumber::get_statement | Microsoft Docs
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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: fa27b5a23f87fb68f070e4f2e5a781d6e5c345a368796c88dc3226b7b8291fd9
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121312159"
---
# <a name="idialinenumberget_statement"></a>IDiaLineNumber::get_statement
Bu satır bilgisinin program kaynağında bir ifade yerine bir deyimin başlangıcını açık olduğunu belirten bir bayrak alınır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_statement ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

[out] Bu `TRUE` satır bilgileri program kaynağında bir deyimin başlangıcını açıklarsa döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür. Bu `S_FALSE` özellik desteklenmiyorsa döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Deyimler birden çok satıra yayma. Bu yöntem, ilişkili satır numarasının böyle bir çok satırlı deyimin başlangıcını işaretleip işaretleyene sahip olduğunu gösterir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)
