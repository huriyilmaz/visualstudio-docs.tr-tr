---
title: 'IDiaEnumInjectedSources:: Next | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumInjectedSources::Next method
ms.assetid: 38af80fc-748f-4b15-bff1-823db21dd4d0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 84dd3e1d107b8e55d5e94979627d1c1586534127
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744491"
---
# <a name="idiaenuminjectedsourcesnext"></a>IDiaEnumInjectedSources::Next
Sabit Listesi dizisinde belirtilen sayıda eklenen kaynağı alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT Next ( 
   ULONG                celt,
   IDiaInjectedSource** rgelt,
   ULONG*               pceltFetched
);
```

#### <a name="parameters"></a>Parametreler
 celt

'ndaki Alınacak Numaralandırıcı içindeki eklenen kaynak sayısı.

 rgelt

dışı İstenen eklenmiş kaynakları temsil eden [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md) nesnelerinin bir dizisini döndürür.

 Pceltfettiz

dışı Getirilen Numaralandırıcı içindeki eklenen kaynak sayısını döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür. Daha fazla eklenen kaynak yoksa `S_FALSE` döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)
- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)