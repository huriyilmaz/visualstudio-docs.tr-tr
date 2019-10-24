---
title: 'IDiaEnumStackFrames:: Next | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumStackFrames::Next method
ms.assetid: 09378a21-d5e3-4213-b7e2-10f04d85295f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ffde40e221823d9656c4b6414b14067ac9d0537a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744034"
---
# <a name="idiaenumstackframesnext"></a>IDiaEnumStackFrames::Next
Sabit Listesi dizisinden belirtilen sayıda yığın çerçevesi öğesi alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT Next( 
   ULONG             celt,
   IDiaStackFrame**  rgelt,
   ULONG*            pceltFetched
);
```

#### <a name="parameters"></a>Parametreler
 celt

'ndaki Alınacak numaralandırıcıdaki StackFrame öğelerinin sayısı.

 rgelt

dışı İstenen [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md) nesneleriyle doldurulacak bir dizi.

 Pceltfettiz

dışı Getirilen Numaralandırıcı içindeki yığın çerçevesi öğelerinin sayısını döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK`döndürür. Daha fazla yığın çerçevesi yoksa `S_FALSE` döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md)
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)