---
description: İşlevin Naked) özniteliğine sahip olup olmadığını belirten bir bayrak alır (yani, işlevin derleyici tarafından eklenen giriş veya bitiş kodu yok).
title: 'IDiaSymbol:: get_isNaked | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isNaked method
ms.assetid: b16629dc-8e17-476b-9c7b-58e7277c61ed
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6ec1d273ce826a87ae658f7ed22fe7680edad25d
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102156162"
---
# <a name="idiasymbolget_isnaked"></a>IDiaSymbol::get_isNaked
İşlevin [çıplak](/cpp/cpp/naked-cpp) özniteliğe sahip olup olmadığını belirten bir bayrak alır (yani, işlevin derleyici tarafından eklenen giriş veya bitiş kodu yok).

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_isNaked(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Parametreler
 `pFlag`

dışı `TRUE` İşlevin özniteliğe sahip olup olmadığını döndürür `naked` ; Aksi takdirde, döndürür `FALSE` .

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, `S_FALSE` bir hata kodu döndürür.

> [!NOTE]
> Dönüş değeri, `S_FALSE` özelliğin sembol için kullanılamadığı anlamına gelir.

## <a name="requirements"></a>Gereksinimler

|Gereksinim|Açıklama|
|-----------------|-----------------|
|Üst bilgi|dia2. h|
|Sürüm:|DIA SDK v 8.0|

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Naked Işlev çağrıları](/cpp/cpp/naked-function-calls)
