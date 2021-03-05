---
description: Tablodaki belirtilen girdiye bir başvuru alır.
title: 'IDiaTable:: Item | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaTable::Item method
ms.assetid: eae11b26-4807-400c-be25-e85bbc0c6b20
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9693a1d16666dcb23f97d918807f9c2fea31c186
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102161678"
---
# <a name="idiatableitem"></a>IDiaTable::Item
Tablodaki belirtilen girdiye bir başvuru alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT Item ( 
   DWORD      index,
   IUnknown** element
);
```

#### <a name="parameters"></a>Parametreler
 `index`

'ndaki 0 ile-1 aralığındaki tablo girişinin dizini `count` , burada `count` [IDiaTable:: get_Count](../../debugger/debug-interface-access/idiatable-get-count.md)yöntemi tarafından döndürülür.

 `element`

dışı `IUnknown` Belirtilen tablo girdisini temsil eden bir nesne döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bir tablo, nesne koleksiyonunu temsil eder. Bu nesnelere bağlı olarak, öğe parametresi uygun arabirime dönüşebilir. Örneğin, bir tablo [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) nesneleri içeriyorsa, öğe parametresi `IDiaSegment` arabirime dönüşebilir.

 `QueryInterface`Uygun Numaralandırıcı arabirimi Için [IDiaTable](../../debugger/debug-interface-access/idiatable.md) arabirimindeki yöntemi çağırmak için daha yaygın bir yaklaşımdır ve tablo içeriğine erişmek için Numaralandırıcının özel yöntemlerini kullanın. Bir örnek için bkz. [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) arabirimi.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaTable](../../debugger/debug-interface-access/idiatable.md)
- [IDiaTable::get_Count](../../debugger/debug-interface-access/idiatable-get-count.md)
- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)
- [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)
