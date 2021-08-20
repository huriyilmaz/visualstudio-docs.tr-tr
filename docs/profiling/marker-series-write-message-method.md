---
description: Eşzamanlılık Görselleştiricisi izleme dosyasına bir ileti yazar.
title: marker_series::write_message Metodu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkersobj/Concurrency, diagnostic::marker_series::write_message
helpviewer_keywords:
- Concurrency, diagnostic::marker_series::write_message method
ms.assetid: 546121bc-67e0-4a5a-a456-12bd78fd6de2
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 483ee104f2141888d5f4468278f7b1707fe6b7bb
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122149695"
---
# <a name="marker_serieswrite_message-method"></a>marker_series::write_message yöntemi
Eşzamanlılık Görselleştiricisi izleme dosyasına bir ileti yazar.

## <a name="syntax"></a>Sözdizimi

```cpp
void write_message(
   _In_ LPCTSTR _Format,
   ...
);
void write_message(
   marker_importance _Importance,
   _In_ LPCTSTR _Format,
   ...
);
void write_message(
   int _Category,
   _In_ LPCTSTR _Format,
   ...
);
void write_message(
   marker_importance _Importance,
   int _Category,
   _In_ LPCTSTR _Format,
   ...
);
```

#### <a name="parameters"></a>Parametreler
 `_Format` Bağımsız değişken listesinde nesnelere karşılık gelen sıfır veya daha fazla biçim öğeleriyle kesişen metin içeren bileşik biçim dizesi.

 `_Importance` Önem düzeyi.

 `_Category` Category.Importance düzeyi.

## <a name="requirements"></a>Gereksinimler
 **Üst bilgi:** *cvmarkersobj.h*

 **Ad alanı:** Concurrency::d iagnostic

## <a name="see-also"></a>Ayrıca bkz.
- [marker_series sınıfı](../profiling/marker-series-class.md)
