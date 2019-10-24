---
title: IDiaSession::p ut_loadAddress | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::put_loadAddress method
ms.assetid: b157b245-1ea0-4b80-8962-d8b278dbc742
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 39db3bc0e0107e734f5de3f6902a2ca0fcc55bb0
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741897"
---
# <a name="idiasessionput_loadaddress"></a>IDiaSession::put_loadAddress
Bu sembol deposundaki simgelere karşılık gelen yürütülebilir dosyanın yükleme adresini ayarlar.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT put_loadAddress ( 
   ULONGLONG NewVal
);
```

#### <a name="parameters"></a>Parametreler
 `NewVal`

'ndaki Yürütülebilir dosya için yükleme adresi.

## <a name="remarks"></a>Açıklamalar
 Sembol sanal adresi (VA) özellikleri bu yöntemin değeri kullanılarak hesaplanır. Bu özellik sıfır dışında bir değer olarak ayarlanmadığı takdirde sanal adresler hesaplanmaz.

> [!NOTE]
> Bu yöntemi, [IDiaSession](../../debugger/debug-interface-access/idiasession.md) nesnesini alırken ve semboller üzerinde herhangi bir sanal özelliği kullanmanız gerekiyorsa nesneyi kullanmaya başlamadan önce çağırmanız gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)