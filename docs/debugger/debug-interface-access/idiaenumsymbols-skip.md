---
description: Bir numaralama dizisinde belirtilen sayıda simgeyi atlar.
title: IDiaEnumSymbols::Skip | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbols::Skip method
ms.assetid: e601fbc9-b10b-41c7-8180-959e57efabe8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: a0a9a4be6943f34379bc2217673eaceb6b904f19837154166b7eddfe7b8ce928
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121312191"
---
# <a name="idiaenumsymbolsskip"></a>IDiaEnumSymbols::Skip
Bir numaralama dizisinde belirtilen sayıda simgeyi atlar.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT Skip ( 
   ULONG celt
);
```

#### <a name="parameters"></a>Parametreler
 Celt

[in] Atlama sırasına göre numaralama dizisinde yer alan sembollerin sayısı.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK` ; aksi takdirde, `S_FALSE` atlanabilecek başka sembol yoksa döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
