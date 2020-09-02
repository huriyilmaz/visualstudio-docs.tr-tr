---
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d67a1806034d55147379626b6eb4f868532e4d77
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85330734"
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