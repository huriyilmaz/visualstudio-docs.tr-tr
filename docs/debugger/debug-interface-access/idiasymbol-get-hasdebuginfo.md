---
description: Compiland 'ın hata ayıklama bilgilerini içerip içerbir şekilde belirten bir bayrak alır.
title: 'IDiaSymbol:: get_hasDebugInfo | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_hasDebugInfo method
ms.assetid: 84cd2b67-0d83-4589-9ecb-a4bcbeed55f5
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8c1ca848ec33e31fbb1f6e8708fd41930931d5f6
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102156330"
---
# <a name="idiasymbolget_hasdebuginfo"></a>IDiaSymbol::get_hasDebugInfo
[Compiland](../../debugger/debug-interface-access/compiland.md) 'ın hata ayıklama bilgileri içerip içerne olduğunu belirten bir bayrak alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_hasDebugInfo(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Parametreler
 `pFlag`

dışı `TRUE` Compiland hata ayıklama bilgisi içeriyorsa döndürür; Aksi takdirde, döndürür `FALSE` .

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, `S_FALSE` bir hata kodu döndürür.

> [!NOTE]
> Dönüş değeri, `S_FALSE` özelliğin simge için kullanılamadığı anlamına gelir.

## <a name="requirements"></a>Gereksinimler

|Gereksinim|Açıklama|
|-----------------|-----------------|
|Üst bilgi|dia2. h|
|Sürüm:|DIA SDK v 8.0|

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
