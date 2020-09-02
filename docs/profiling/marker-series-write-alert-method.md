---
title: 'marker_series:: write_alert yöntemi | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkersobj/Concurrency, diagnostic:marker_series::write_alert
helpviewer_keywords:
- Concurrency, diagnostic:marker_series::write_alert method
ms.assetid: 9d5465c7-f862-47a7-b249-4116605075a6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d5e79bab25885c8759ea5726b037771a4943c563
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85329634"
---
# <a name="marker_serieswrite_alert-method"></a>marker_series:: write_alert yöntemi
Eşzamanlılık görselleştiricisi izleme dosyasına bir uyarı yazar.

## <a name="syntax"></a>Söz dizimi

```cpp
void write_alert(
   _In_ LPCTSTR _Format,
   ...
);
```

#### <a name="parameters"></a>Parametreler
 `_Format` Bağımsız değişken listesindeki nesnelere karşılık gelen sıfır veya daha fazla biçim öğesiyle metin içeren bir bileşik biçim dizesi.

## <a name="requirements"></a>Gereksinimler
 **Üst bilgi:** *cvmarkersobj. h*

 **Ad alanı:** Eşzamanlılık::d ıagstik

## <a name="see-also"></a>Ayrıca bkz.
- [marker_series sınıfı](../profiling/marker-series-class.md)