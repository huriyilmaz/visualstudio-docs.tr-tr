---
description: Bir dizin aracılığıyla bir satır numarası alır.
title: 'IDiaEnumLineNumbers:: Item | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumLineNumbers::Item method
ms.assetid: 08efbeaf-22f7-49e9-96a8-bb906dfe4fd8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6eeea52f2152d1674710d7c5ee2b5970a8cd91cd
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102157982"
---
# <a name="idiaenumlinenumbersitem"></a>IDiaEnumLineNumbers::Item
Bir dizin aracılığıyla bir satır numarası alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT Item ( 
   DWORD            index,
   IDiaLineNumber** lineNumber
);
```

#### <a name="parameters"></a>Parametreler
 dizin

'ndaki Alınacak [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md) nesnesinin dizini. Dizin 0 `count` -1 aralığında, burada `count` [IDiaEnumLineNumbers:: get_Count](../../debugger/debug-interface-access/idiaenumlinenumbers-get-count.md) yöntemi tarafından döndürülür.

 Onayın

dışı İstenen satır numarasını temsil eden bir [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)
