---
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f1eae34788cfed9f509e979df8efae6657f330d5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85468219"
---
# <a name="idiaenumlinenumbersitem"></a>IDiaEnumLineNumbers::Item
Bir dizin aracılığıyla bir satır numarası alır.

## <a name="syntax"></a>Söz dizimi

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