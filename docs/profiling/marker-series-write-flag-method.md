---
title: marker_series::write_flag Yöntemi | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkersojb/Concurrency::diagnostic::marker_series::write_flag
helpviewer_keywords:
- Concurrency::diagnostic::marker_series::write_flag method
ms.assetid: ca07f388-e5d5-46fd-b991-fe6e9029a68f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f09cca9bd1e3babccb0debc369881a0efa00fa0b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62830817"
---
# <a name="marker_serieswrite_flag-method"></a>marker_series::write_flag yöntemi
Eşzamanlı Görüntüleyici izleme dosyasına bir bayrak yazar.

## <a name="syntax"></a>Sözdizimi

```cpp
void write_flag(
   _In_ LPCTSTR _Format,
   ...
);
void write_flag(
   marker_importance _Importance,
   _In_ LPCTSTR _Format,
   ...
);
void write_flag(
   int _Category,
   _In_ LPCTSTR _Format,
   ...
);
void write_flag(
   marker_importance _Importance,
   int _Category,
   _In_ LPCTSTR _Format,
   ...
);
```

#### <a name="parameters"></a>Parametreler
 `_Format`Bağımsız değişken listesindeki nesnelere karşılık gelen sıfır veya daha fazla biçim öğesiyle karışık metin içeren bileşik biçim dizesi.

 `_Importance`Önem düzeyi.

 `_Category`Kategori.

## <a name="requirements"></a>Gereksinimler
 **Başlık:** *cvmarkersobj.h*

 **Ad alanı:** Eşzamanlılık::diagnostik

## <a name="see-also"></a>Ayrıca bkz.
- [marker_series sınıfı](../profiling/marker-series-class.md)