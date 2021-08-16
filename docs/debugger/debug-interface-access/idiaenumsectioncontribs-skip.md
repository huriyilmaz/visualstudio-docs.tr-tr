---
description: Bir numaralama dizisinde belirtilen sayıda bölüm katkısını atlar.
title: IDiaEnumSectionContribs::Skip | Microsoft Docs
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
ms.openlocfilehash: 9ab53955f5342dd0bce902c73ba568f3f6a00aa22b062ba5fa1394ba0bb8a2c8
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121380353"
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
