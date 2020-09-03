---
title: 'IDiaSymbol:: get_optimizedCodeDebugInfo | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_optimizedCodeDebugInfo method
ms.assetid: 57ef4170-37a9-46b0-8217-c1a674725113
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bf547835179aa203b9ecc4bb0c8050c34e213fdd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85462604"
---
# <a name="idiasymbolget_optimizedcodedebuginfo"></a>IDiaSymbol::get_optimizedCodeDebugInfo
İşlevin iyileştirilmiş kod için özel hata ayıklama bilgileri içerip içermediğini gösteren bir bayrak alır.

## <a name="syntax"></a>Söz dizimi

```C++
HRESULT get_optimizedCodeDebugInfo(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Parametreler
 `pFlag`

dışı `TRUE` İyileştirilmiş işlev veya etiket hata ayıklama bilgisi içeriyorsa döndürür; Aksi takdirde, döndürür `FALSE` .

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, `S_FALSE` bir hata kodu döndürür.

> [!NOTE]
> Dönüş değeri, `S_FALSE` özelliğin sembol için kullanılamadığı anlamına gelir.

## <a name="requirements"></a>Gereksinimler

|Gereksinim|Description|
|-----------------|-----------------|
|Üst bilgi|dia2. h|

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)