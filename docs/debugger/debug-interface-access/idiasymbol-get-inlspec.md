---
description: Bu işlev, işlevin satır içi olarak işaretlenip işaretlenmediğini belirten bir bayrak alır (satır içi, _inline, __forceinline) özniteliklerinden birini kullanarak).
title: 'IDiaSymbol:: get_InlSpec | Microsoft Docs'
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
ms.openlocfilehash: 6e3f82d716c4699cff05340716c9fca7383576e6
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122128658"
---
# <a name="idiasymbolget_inlspec"></a>IDiaSymbol::get_InlSpec
Bu işlev, işlevin satır içi olarak işaretlenip işaretlenmediğini belirten bir bayrak alır ( [satır içi, __inline \_ _forceinline](/cpp/cpp/inline-functions-cpp) özniteliklerinden birini kullanarak).

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_inlSpec(
   BOOL *pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı `TRUE` İşlevin satır içi olarak işaretlenip işaretlenmediğini döndürür; Aksi takdirde, döndürür `FALSE` .

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, döndürür `S_FALSE` veya hata kodu döndürür.

> [!NOTE]
> Dönüş değeri, `S_FALSE` özelliğin simge için kullanılamadığı anlamına gelir.

## <a name="requirements"></a>Gereksinimler

|Gereksinim|Açıklama|
|-----------------|-----------------|
|Üst bilgi|dia2. h|
|Sürüm:|DIA SDK v 8.0|

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [satır içi, __inline, \_ _forceinline](/cpp/cpp/inline-functions-cpp)
