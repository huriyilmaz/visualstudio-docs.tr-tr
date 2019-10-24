---
title: 'IDiaEnumSectionContribs:: Skip | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSectionContribs::Skip method
ms.assetid: 7471a178-5134-41b2-80a6-51ff96abe916
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cb371d841c10b64895400f66bf73159f27d68ec1
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744258"
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
 Başarılı olursa `S_OK`döndürür; Aksi takdirde, atlanacak başka bölüm katkıları yoksa `S_FALSE` döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)