---
description: Sabit Listesi dizisinde belirtilen sayıda bölüm katkılarını alır.
title: 'IDiaEnumSectionContribs:: Next | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSectionContribs::Next method
ms.assetid: a6bb2adb-ee6d-4f3c-ab5b-e89361c8880e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0d6e33d1c56b1dd2501af2a84af8fbeef5a2831e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102159323"
---
# <a name="idiaenumsectioncontribsnext"></a>IDiaEnumSectionContribs::Next
Sabit Listesi dizisinde belirtilen sayıda bölüm katkılarını alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT Next( 
   ULONG                celt,
   IDiaSectionContrib** rgelt,
   ULONG*               pceltFetched
);
```

#### <a name="parameters"></a>Parametreler
 celt

'ndaki Alınacak numaralandırıcıdaki bölüm katkılarının sayısı.

 rgelt

dışı İstenen bölüm katkılarını temsil eden [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md) nesneleriyle doldurulacak bir dizi.

 Pceltfettiz

dışı Alınan Numaralandırıcı içindeki bölüm katkılarının sayısını döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` . `S_FALSE`Başka bölüm katkıları yoksa döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)
