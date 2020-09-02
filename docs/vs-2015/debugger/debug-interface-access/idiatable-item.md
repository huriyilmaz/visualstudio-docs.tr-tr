---
title: 'IDiaTable:: Item | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaTable::Item method
ms.assetid: eae11b26-4807-400c-be25-e85bbc0c6b20
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6112a4580a68a98407723afab1ec3310d0f1cca9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62574807"
---
# <a name="idiatableitem"></a>IDiaTable::Item
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Tablodaki belirtilen girdiye bir başvuru alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)   
 [IDiaTable:: get_Count](../../debugger/debug-interface-access/idiatable-get-count.md)   
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)   
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)
