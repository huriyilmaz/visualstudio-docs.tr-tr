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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 68b4cf880b2b296751ec0a364d88207c35754c4a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122036138"
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
