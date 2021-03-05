---
description: Sabit Listesi dizisinde belirtilen sayıda bölüm katkılarını atlar.
title: 'IDiaEnumSectionContribs:: Skip | Microsoft Docs'
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
ms.workload:
- multiple
ms.openlocfilehash: 345aa9219071a64fdd497a9e5409ee7dab3068ad
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102159302"
---
# <a name="idiaenumsectioncontribsskip"></a>IDiaEnumSectionContribs::Skip
Sabit Listesi dizisinde belirtilen sayıda bölüm katkılarını atlar.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT Skip( 
   ULONG celt
);
```

#### <a name="parameters"></a>Parametreler
 `celt`

'ndaki Atlanacak numaralandırma dizisindeki bölüm katkılarının sayısı.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, `S_FALSE` atlanacak başka bölüm katkılarının yoksa döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)
