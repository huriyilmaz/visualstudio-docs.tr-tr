---
title: 'IDiaSymbol:: get_InlSpec | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_InlSpec method
ms.assetid: 30af6a2f-be84-429e-a96a-d0f9ed9343fb
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5675239e35ab3bef809e3d54544d87d7a9e8bb75
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740390"
---
# <a name="idiasymbolget_inlspec"></a>IDiaSymbol::get_InlSpec
Bu işlev, işlevin satır içi olarak işaretlenip işaretlenmediğini belirten bir bayrak alır ( [satır içi, __inline, \__forceinline](/cpp/cpp/inline-functions-cpp) özniteliklerinden birini kullanarak).

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_inlSpec(
   BOOL *pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı İşlev satır içi olarak işaretlenmişse `TRUE` döndürür; Aksi takdirde, `FALSE` döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; Aksi takdirde, `S_FALSE` veya hata kodu döndürür.

> [!NOTE]
> @No__t_0 dönüş değeri, özelliğin simge için kullanılamadığı anlamına gelir.

## <a name="requirements"></a>Gereksinimler

|Gereksinim|Açıklama|
|-----------------|-----------------|
|Üst bilgi|dia2. h|
|Sürüm:|DIA SDK v 8.0|

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [satır içi, __inline, \__forceinline](/cpp/cpp/inline-functions-cpp)