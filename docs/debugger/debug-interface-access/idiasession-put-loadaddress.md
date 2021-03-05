---
description: Bu sembol deposundaki simgelere karşılık gelen yürütülebilir dosyanın yükleme adresini ayarlar.
title: IDiaSession::p ut_loadAddress | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::put_loadAddress method
ms.assetid: b157b245-1ea0-4b80-8962-d8b278dbc742
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 05dc21a67a88270c4d3bce46387e46ed5a8e8497
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102157002"
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
