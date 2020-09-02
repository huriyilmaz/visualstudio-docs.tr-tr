---
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 76f5aa24efe6ce479de2a312943613b8262d0118
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85468268"
---
# <a name="idiaenuminjectedsourcesnext"></a>IDiaEnumInjectedSources::Next
Sabit Listesi dizisinde belirtilen sayıda eklenen kaynağı alır.

## <a name="syntax"></a>Söz dizimi

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