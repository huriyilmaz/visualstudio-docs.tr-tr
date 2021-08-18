---
description: Eşzamanlılık Görselleştiricisi işaretçisinin önem düzeyini temsil eder.
title: marker_importance Enumeration | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkersobj/Concurrency, diagnostic::marker_importance
helpviewer_keywords:
- Concurrency, diagnostic::marker_importance enumeration
ms.assetid: d5524ea0-0227-4d8e-9122-332291042df5
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 1e499466eebb4ef856839d1e71880011c6490aba
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122076483"
---
# <a name="marker_importance-enumeration"></a>marker_importance enumeration
Eşzamanlılık Görselleştiricisi işaretçisinin önem düzeyini temsil eder.

## <a name="syntax"></a>Syntax

```cpp
enum marker_importance;
```

## <a name="members"></a>Üyeler

### <a name="values"></a>Değerler

|Ad|Açıklama|
|----------|-----------------|
|`critical_importance`|İşaretçinin kritik öneme sahip olduğunu belirtir.|
|`high_importance`|İşaretçinin yüksek öneme sahip olduğunu belirtir.|
|`low_importance`|İşaretçinin düşük öneme sahip olduğunu belirtir.|
|`normal_importance`|İşaretçinin normal öneme sahip olduğunu belirtir.|

## <a name="requirements"></a>Gereksinimler
 **Üst bilgi:** *cvmarkersobj.h*

 **Ad alanı:** Concurrency::d iagnostic

## <a name="see-also"></a>Ayrıca bkz.
- [tanılama ad alanı](../profiling/diagnostic-namespace.md)
