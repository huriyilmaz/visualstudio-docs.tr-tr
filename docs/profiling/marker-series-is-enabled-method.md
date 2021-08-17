---
description: Sağlayıcıyı herhangi bir oturumun etkinleştirmiş olup olmadığını belirler.
title: marker_series::is_enabled Metodu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkersobj/Concurrency, diagnostic::marker_series::is_enabled
helpviewer_keywords:
- Concurrency, diagnostic::marker_series::is_enabled method
ms.assetid: 8ce4dd50-ca29-4c72-98d6-582693f7d501
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: b36a76b8d404606b97672a78d8fb467fc998bbf4
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122107413"
---
# <a name="marker_seriesis_enabled-method"></a>marker_series::is_enabled yöntemi
Sağlayıcıyı herhangi bir oturumun etkinleştirmiş olup olmadığını belirler.

## <a name="syntax"></a>Sözdizimi

```cpp
bool is_enabled();
bool is_enabled(
   marker_importance _Importance,
   int _Category
);
```

#### <a name="parameters"></a>Parametreler
 `_Importance` Önem düzeyi.

 `_Category` Kategori.

## <a name="return-value"></a>Döndürülen değer

## <a name="requirements"></a>Gereksinimler
 **Üst bilgi:** *cvmarkersobj.h*

 **Ad alanı:** Concurrency::d iagnostic

## <a name="see-also"></a>Ayrıca bkz.
- [marker_series sınıfı](../profiling/marker-series-class.md)
