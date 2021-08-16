---
description: Eşzamanlılık Görselleştiricisi izleme dosyasına bir bayrak yazar.
title: marker_series::write_flag Metodu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkersojb/Concurrency, diagnostic::marker_series::write_flag
helpviewer_keywords:
- Concurrency, diagnostic::marker_series::write_flag method
ms.assetid: ca07f388-e5d5-46fd-b991-fe6e9029a68f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 1e31fdbb3b0c1f1520b11f08d065c690fa7763372e31c0cedd8ffca729598ca2
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121426410"
---
# <a name="marker_serieswrite_flag-method"></a>marker_series::write_flag yöntemi
Eşzamanlılık Görselleştiricisi izleme dosyasına bir bayrak yazar.

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
 `_Format` Bağımsız değişken listesinde nesnelere karşılık gelen sıfır veya daha fazla biçim öğeleriyle kesişen metin içeren bileşik biçim dizesi.

 `_Importance` Önem düzeyi.

 `_Category` Kategori.

## <a name="requirements"></a>Gereksinimler
 **Üst bilgi:** *cvmarkersobj.h*

 **Ad alanı:** Concurrency::d iagnostic

## <a name="see-also"></a>Ayrıca bkz.
- [marker_series sınıfı](../profiling/marker-series-class.md)
