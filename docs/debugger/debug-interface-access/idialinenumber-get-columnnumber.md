---
description: İfadenin veya deyimin başladığı sütun numarasını alır.
title: 'IDiaLineNumber:: get_columnNumber | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_columnNumber method
ms.assetid: e317f29a-6525-46a7-8421-33985392f8fd
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 1cad0c103b61c8b50e5b10f7a63c13f6bda015ade0cb11903c0e730db9ca2e5a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121392195"
---
# <a name="idialinenumberget_columnnumber"></a>IDiaLineNumber::get_columnNumber
İfadenin veya deyimin başladığı sütun numarasını alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT get_columnNumber ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı İfadenin veya deyimin başladığı sütun numarasını döndürür. Değer sıfırsa, sütun bilgisi mevcut değildir.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` . `S_FALSE`Bu özellik desteklenmiyorsa döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem tarafından döndürülen sütun değeri, satırdaki deyimin ilk karakterine satıra kadar olan bir bayt kaydırmadır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)
