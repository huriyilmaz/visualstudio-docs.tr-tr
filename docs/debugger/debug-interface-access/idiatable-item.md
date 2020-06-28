---
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 18efd1113d66d36b99dd33eb3e79cb0cc7e8bb05
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85461303"
---
# <a name="idiatableitem"></a>IDiaTable::Item
Tablodaki belirtilen girdiye bir başvuru alır.

## <a name="syntax"></a>Söz dizimi

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

dışı `IUnknown`Belirtilen tablo girdisini temsil eden bir nesne döndürür.

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