---
description: Sembol sayısını alın.
title: IDiaEnumSymbols::get_Count | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbols::get_Count method
ms.assetid: fdaae6d7-e67b-4262-84c9-fbae381e8297
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 0e3b99a4319bd1ade01d8fbc340cd82cb26bb20abc4ed2b6a4cff7c8fa397e3a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121312199"
---
# <a name="idiaenumsymbolsget_count"></a>IDiaEnumSymbols::get_Count
Sembol sayısını alın.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_Count ( 
   LONG* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 pRetVal

[out] Sembol sayısını döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaEnumSymbols::Item](../../debugger/debug-interface-access/idiaenumsymbols-item.md)
