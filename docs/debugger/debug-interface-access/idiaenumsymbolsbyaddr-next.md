---
description: Sıradaki simgeleri adrese göre alır.
title: 'IDiaEnumSymbolsByAddr:: Next | Microsoft Docs'
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
ms.openlocfilehash: b509c84c9ee0fe81a7c9532bbc6f218af277df5d
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126629996"
---
# <a name="idiaenumsymbolsbyaddrnext"></a>IDiaEnumSymbolsByAddr::Next
Sıradaki simgeleri adrese göre alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT Next ( 
   ULONG        celt,
   IDiaSymbol** rgelt,
   ULONG*       pceltFetched
);
```

#### <a name="parameters"></a>Parametreler
 celt

'ndaki Numaralandırıcıda alınacak olan simgelerin sayısı.

 rgelt

dışı İstenen sembolleri temsil eden [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) nesnesiyle doldurulacak bir dizi.

 Pceltfettiz

dışı Getirilen Numaralandırıcı içindeki simgelerin sayısını döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` . `S_FALSE`Daha fazla sembol yoksa döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem, Numaralandırıcı konumunu getirilen öğe sayısına göre güncelleştirir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
