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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: e49593578efb94feb9fc5f9da2152b9008a4d8ba
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122044789"
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
