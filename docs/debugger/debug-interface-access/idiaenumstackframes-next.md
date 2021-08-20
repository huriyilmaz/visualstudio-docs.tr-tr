---
description: Numaralama dizisinde belirtilen sayıda yığın çerçevesi öğelerini alan.
title: IDiaEnumStackFrames::Next | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumStackFrames::Next method
ms.assetid: 09378a21-d5e3-4213-b7e2-10f04d85295f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 76248ef1feb330157895ccd24d8fa071b3e857bd
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122129482"
---
# <a name="idiaenumstackframesnext"></a>IDiaEnumStackFrames::Next
Numaralama dizisinde belirtilen sayıda yığın çerçevesi öğelerini alan.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT Next( 
   ULONG             celt,
   IDiaStackFrame**  rgelt,
   ULONG*            pceltFetched
);
```

#### <a name="parameters"></a>Parametreler
 Celt

[in] Numaralayıcıda alınan stackframe öğelerinin sayısı.

 Rgelt

[out] İstenen [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md) nesneleriyle doldurulması gereken bir dizi.

 pceltFetched

[out] Getirili numaralayıcıda yığın çerçevesi öğelerinin sayısını döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür. Başka `S_FALSE` yığın çerçevesi yoksa döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md)
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)
