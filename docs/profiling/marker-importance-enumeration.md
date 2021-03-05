---
description: Bir eşzamanlılık görselleştiricisi işaretçisinin önem derecesini temsil eder.
title: marker_importance numaralandırması | Microsoft Docs
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
ms.workload:
- multiple
ms.openlocfilehash: 2c2e7560c91882afe1ee2608bb2ae2fc105738dc
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223946"
---
# <a name="marker_importance-enumeration"></a>marker_importance numaralandırması
Bir eşzamanlılık görselleştiricisi işaretçisinin önem derecesini temsil eder.

## <a name="syntax"></a>Syntax

```cpp
enum marker_importance;
```

## <a name="members"></a>Üyeler

### <a name="values"></a>Değerler

|Ad|Açıklama|
|----------|-----------------|
|`critical_importance`|İşaretin önemli öneme sahip olduğunu belirtir.|
|`high_importance`|İşaretin yüksek önem derecesine sahip olduğunu belirtir.|
|`low_importance`|İşaretin düşük önem derecesine sahip olduğunu belirtir.|
|`normal_importance`|İşaretin normal öneme sahip olduğunu belirtir.|

## <a name="requirements"></a>Gereksinimler
 **Üst bilgi:** *cvmarkersobj. h*

 **Ad alanı:** Eşzamanlılık::d ıagstik

## <a name="see-also"></a>Ayrıca bkz.
- [Tanılama ad alanı](../profiling/diagnostic-namespace.md)
