---
description: Bir dizini kullanarak sembolünü alan.
title: IDiaEnumSymbols::Item | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbols::Item method
ms.assetid: 2bd1ec04-e677-4e32-8e32-33334f1eed77
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: edeccffd92749ac7f00ea6f866a37e933eb499c6
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126630027"
---
# <a name="idiaenumsymbolsitem"></a>IDiaEnumSymbols::Item
Bir dizini kullanarak sembolünü alan.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT Item ( 
   DWORD        index,
   IDiaSymbol** symbol
);
```

#### <a name="parameters"></a>Parametreler
 dizin

[in] Alınacak [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) nesnesinin dizini. Dizin, 0 ile -1 aralığındadır `count` ve `count` burada [IDiaEnumSymbols::get_Count](../../debugger/debug-interface-access/idiaenumsymbols-get-count.md) yöntemi tarafından döndürülür.

  simgesi

[out] İstenen sembolü [temsil eden bir IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
