---
description: Tablodaki belirtilen girişe bir başvuru alır.
title: IDiaTable::Item | Microsoft Docs
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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 384aab56a17faa4ada1ff99fc43f13032d18db3d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122121204"
---
# <a name="idiatableitem"></a>IDiaTable::Item
Tablodaki belirtilen girişe bir başvuru alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT Item ( 
   DWORD      index,
   IUnknown** element
);
```

#### <a name="parameters"></a>Parametreler
 `index`

[in] 0 ile -1 aralığındaki tablo girişinin dizini; burada `count` `count` [IDiaTable::get_Count](../../debugger/debug-interface-access/idiatable-get-count.md)yöntemi tarafından döndürülür.

 `element`

[out] Belirtilen tablo `IUnknown` girişini temsil eden bir nesne döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Tablo, bir nesne koleksiyonunu temsil eder. Bu nesnelere bağlı olarak, öğe parametresi uygun arabirime atabilirsiniz. Örneğin, bir tablo [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) nesneleri içeriyorsa, öğe parametresi arabirime `IDiaSegment` atabilirsiniz.

 Uygun numaralayıcı arabirimi için IDiaTable arabiriminde yöntemini çağırma ve tablo içeriğine erişmek için numaralayıcının belirli yöntemlerini kullanma daha yaygın bir `QueryInterface` yaklaşımdır. [](../../debugger/debug-interface-access/idiatable.md) Örnek için [bkz. IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) arabirimi.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaTable](../../debugger/debug-interface-access/idiatable.md)
- [IDiaTable::get_Count](../../debugger/debug-interface-access/idiatable-get-count.md)
- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)
- [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)
