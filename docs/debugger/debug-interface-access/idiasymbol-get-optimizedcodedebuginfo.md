---
description: İşlevin iyileştirilmiş koda özgü hata ayıklama bilgileri içerdiğini belirten bir bayrak verir.
title: IDiaSymbol::get_optimizedCodeDebugInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_optimizedCodeDebugInfo method
ms.assetid: 57ef4170-37a9-46b0-8217-c1a674725113
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: b5cd438ead3b76f2c562c1e84304ba3b2819d3fa
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122081192"
---
# <a name="idiasymbolget_optimizedcodedebuginfo"></a>IDiaSymbol::get_optimizedCodeDebugInfo
İşlevin iyileştirilmiş koda özgü hata ayıklama bilgileri içerdiğini belirten bir bayrak verir.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_optimizedCodeDebugInfo(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Parametreler
 `pFlag`

[out] İyileştirilmiş `TRUE` işlev veya etiket hata ayıklama bilgileri içeriyorsa döndürür; aksi takdirde `FALSE` döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde veya `S_FALSE` bir hata kodu döndürür.

> [!NOTE]
> dönüş `S_FALSE` değeri, özelliğin sembol için kullanılamaz olduğu anlamına gelir.

## <a name="requirements"></a>Gereksinimler

|Gereksinim|Açıklama|
|-----------------|-----------------|
|Üstbilgi:|dia2.h|

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
