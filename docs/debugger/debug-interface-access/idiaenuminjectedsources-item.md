---
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 76e89c89bca8b164645c71df6083b230850e61ca
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85468275"
---
# <a name="idiaenuminjectedsourcesitem"></a>IDiaEnumInjectedSources::Item
Eklenen kaynağı bir dizin aracılığıyla alır.

## <a name="syntax"></a>Söz dizimi

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