---
description: Sabit Listesi dizisinde belirtilen sayıda eklenen kaynağı alır.
title: 'IDiaEnumInjectedSources:: Next | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumInjectedSources::Next method
ms.assetid: 38af80fc-748f-4b15-bff1-823db21dd4d0
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: bdc57bd1b15150b93e8c42537e5a4abed8dfae57
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158003"
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
 Başarılı olursa, döndürür `S_OK` . `S_FALSE`Daha fazla eklenen kaynak yoksa döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)
- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)
