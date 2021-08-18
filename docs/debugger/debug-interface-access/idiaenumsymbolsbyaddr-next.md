---
description: Sonraki sembolleri adrese göre sırasıyla alın.
title: IDiaEnumSymbolsByAddr::Next | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbolsByAddr::Next method
ms.assetid: a1320587-7ce7-401f-9548-2f8bcece5cc3
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 7b962618854bc9701eb731729ebd276f1a6a96969addf6187d92b2e922b6d298
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121345151"
---
# <a name="idiaenumsymbolsbyaddrnext"></a>IDiaEnumSymbolsByAddr::Next
Sonraki sembolleri adrese göre sırasıyla alın.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT Next ( 
   ULONG        celt,
   IDiaSymbol** rgelt,
   ULONG*       pceltFetched
);
```

#### <a name="parameters"></a>Parametreler
 Celt

[in] Numaralayıcıda alınan simgelerin sayısı.

 Rgelt

[out] İstenen sembolleri temsil eden [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) nesnesiyle doldurulacak bir dizi.

 pceltFetched

[out] Getirili numaralayıcıda simgelerin sayısını döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür. Başka `S_FALSE` sembol yoksa döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem, numaralayıcı konumunu alınan öğe sayısına göre günceller.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
