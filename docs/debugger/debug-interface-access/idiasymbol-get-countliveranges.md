---
description: Yerel simgeyle ilişkili geçerli adres aralıklarının sayısını alın.
title: IDiaSymbol::get_countLiveRanges | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_countLiveRanges
ms.assetid: 55f79e1a-d4c2-42cd-ab37-d8253b20e34c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 2f1e8effd336ff578e7991a3a600167a20d6c3a3
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122036194"
---
# <a name="idiasymbolget_countliveranges"></a>IDiaSymbol::get_countLiveRanges
Yerel simgeyle ilişkili geçerli adres aralıklarının sayısını alın.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_countLiveRanges ( 
   DWORD* count
);
```

#### <a name="parameters"></a>Parametreler
 `count`

[out] Adres aralıklarının sayısını döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: Dia2.h

 Kitaplık: diaguids.lib

 DLL: msdia100.dll

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
