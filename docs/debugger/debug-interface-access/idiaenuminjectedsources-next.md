---
description: Numaralama sırasına belirtilen sayıda kaynak eklemesini sağlar.
title: IDiaEnumInjectedSources::Next | Microsoft Docs
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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: ee8e2a2f7b595bdc3484af78542dcd7d45ce1244fee9ea588ba5c1e1cff11a61
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121455162"
---
# <a name="idiaenuminjectedsourcesnext"></a>IDiaEnumInjectedSources::Next
Numaralama sırasına belirtilen sayıda kaynak eklemesini sağlar.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT Next ( 
   ULONG                celt,
   IDiaInjectedSource** rgelt,
   ULONG*               pceltFetched
);
```

#### <a name="parameters"></a>Parametreler
 Celt

[in] Numaralayıcıya alınan kaynakların sayısı.

 Rgelt

[out] İstenen ekleme kaynaklarını [temsil eden bir IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md) nesneleri dizisi döndürür.

 pceltFetched

[out] Getirilen numaralayıcıya alınan kaynakların sayısını döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür. Daha `S_FALSE` fazla kaynak eklemezse döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)
- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)
