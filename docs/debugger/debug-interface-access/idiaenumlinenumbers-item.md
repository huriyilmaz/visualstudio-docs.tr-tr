---
description: Bir dizin ile bir satır numarası alınır.
title: IDiaEnumLineNumbers::Item | Microsoft Docs
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
ms.openlocfilehash: 868cd4f4e643106d5ed6f91f6dd36b711a275d7eda24f278f9e3ad8a471096d0
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121392499"
---
# <a name="idiaenumlinenumbersitem"></a>IDiaEnumLineNumbers::Item
Bir dizin ile bir satır numarası alınır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT Item ( 
   DWORD            index,
   IDiaLineNumber** lineNumber
);
```

#### <a name="parameters"></a>Parametreler
 dizin

[in] Alınan [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md) nesnesinin dizini. Dizin, 0 ile -1 aralığındadır `count` ve `count` burada [IDiaEnumLineNumbers::get_Count](../../debugger/debug-interface-access/idiaenumlinenumbers-get-count.md) yöntemi tarafından döndürülür.

 lineNumber

[out] İstenen satır numarasını temsil eden bir [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)
