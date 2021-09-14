---
description: Bir numaralama dizisinde belirtilen sayıda bölüm katkısını atlar.
title: IDiaEnumSectionContribs::| Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSectionContribs::Skip method
ms.assetid: 7471a178-5134-41b2-80a6-51ff96abe916
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: cd60e86df46a77941c3aa9b58fa93d2f7e4531c8
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126630170"
---
# <a name="idiaenumsectioncontribsskip"></a>IDiaEnumSectionContribs::Skip
Bir numaralama dizisinde belirtilen sayıda bölüm katkısını atlar.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT Skip( 
   ULONG celt
);
```

#### <a name="parameters"></a>Parametreler
 `celt`

[in] Atlama için numaralama dizisinde bölüm katkılarının sayısı.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK` döndürür; aksi takdirde, `S_FALSE` atlanabilecek başka bölüm katkısı yoksa döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)
