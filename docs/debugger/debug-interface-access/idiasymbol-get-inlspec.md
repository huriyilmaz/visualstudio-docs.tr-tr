---
description: Bu işlev, işlevin satır içi (satır içi, _inline, __forceinline) özniteliklerinden birini kullanarak) olarak işaret __forceinline bayrağı alır.
title: IDiaSymbol::get_InlSpec | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_InlSpec method
ms.assetid: 30af6a2f-be84-429e-a96a-d0f9ed9343fb
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: f566ad0c13e64eda7ea8d6278d75261536b299423ae77ba65da996b9cdeeec65
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121404829"
---
# <a name="idiasymbolget_inlspec"></a>IDiaSymbol::get_InlSpec
Bu işlev, işlevin satır içi olarak işaretlenmiş olup olmadığını belirten bir bayrak alır (satır [içi, __inline, \_ _forceinline](/cpp/cpp/inline-functions-cpp) kullanarak).

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_inlSpec(
   BOOL *pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

[out] İşlev `TRUE` satır içi olarak işaretlenmişse döndürür; aksi takdirde `FALSE` döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde veya `S_FALSE` hata kodu döndürür.

> [!NOTE]
> dönüş `S_FALSE` değeri, özelliğin sembol için kullanılamaz olduğu anlamına gelir.

## <a name="requirements"></a>Gereksinimler

|Gereksinim|Açıklama|
|-----------------|-----------------|
|Üstbilgi:|dia2.h|
|Sürüm:|DIA SDK v8.0|

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [satır içi, __inline, \_ _forceinline](/cpp/cpp/inline-functions-cpp)
