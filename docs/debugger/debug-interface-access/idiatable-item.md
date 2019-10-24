---
title: 'IDiaTable:: Item | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaTable::Item method
ms.assetid: eae11b26-4807-400c-be25-e85bbc0c6b20
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d402f5ad54d5c0f487cebb3a8c53f68d17828ed4
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738721"
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

'ndaki @No__t_0-1 aralığında, `count` [IDiaTable:: get_Count](../../debugger/debug-interface-access/idiatable-get-count.md)yöntemi tarafından döndürülen tablo girişinin dizini.

 `element`

dışı Belirtilen tablo girdisini temsil eden bir `IUnknown` nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bir tablo, nesne koleksiyonunu temsil eder. Bu nesnelere bağlı olarak, öğe parametresi uygun arabirime dönüşebilir. Örneğin, bir tablo [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) nesneleri içeriyorsa, öğe parametresi `IDiaSegment` arabirimine dönüşebilir.

 Uygun Numaralandırıcı arabirimi için [IDiaTable](../../debugger/debug-interface-access/idiatable.md) arabirimindeki `QueryInterface` yöntemini çağırmaya yönelik daha yaygın bir yaklaşımdır ve tablo içeriğine erişmek için Numaralandırıcının özel yöntemlerini kullanın. Bir örnek için bkz. [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) arabirimi.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaTable](../../debugger/debug-interface-access/idiatable.md)
- [IDiaTable::get_Count](../../debugger/debug-interface-access/idiatable-get-count.md)
- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)
- [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)