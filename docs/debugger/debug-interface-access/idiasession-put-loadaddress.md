---
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 807346ef5a34c0b175257fe2099dc25e8de692f6
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85465386"
---
# <a name="idiasessionput_loadaddress"></a>IDiaSession::put_loadAddress
Bu sembol deposundaki simgelere karşılık gelen yürütülebilir dosyanın yükleme adresini ayarlar.

## <a name="syntax"></a>Söz dizimi

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