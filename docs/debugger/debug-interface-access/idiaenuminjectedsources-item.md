---
description: Eklenen kaynağı bir dizin aracılığıyla alır.
title: 'IDiaEnumInjectedSources:: Item | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumInjectedSources::Item method
ms.assetid: 14846955-7270-451d-91d2-9cb34bb65187
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: d28eb5cc69d3cdeb8ca5da95b91d79ed9c5f46ec042d53fb0704f3b77f3ea5dc
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121455202"
---
# <a name="idiaenuminjectedsourcesitem"></a>IDiaEnumInjectedSources::Item
Eklenen kaynağı bir dizin aracılığıyla alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT Item ( 
   DWORD                index,
   IDiaInjectedSource** injectedSource
);
```

#### <a name="parameters"></a>Parametreler
 dizin

'ndaki Alınacak [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md) nesnesinin dizini. Dizin, `count` `count` [IDiaEnumInjectedSources:: get_Count](../../debugger/debug-interface-access/idiaenuminjectedsources-get-count.md) yöntemi tarafından döndürülen 0 ile-1 aralığıdır.

 ınjectedsource

dışı Eklenen kaynağı temsil eden bir [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)
- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)
