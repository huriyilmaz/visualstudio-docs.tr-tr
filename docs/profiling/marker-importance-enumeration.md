---
title: marker_importance Numaralandırma | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::marker_importance
helpviewer_keywords:
- Concurrency::diagnostic::marker_importance enumeration
ms.assetid: d5524ea0-0227-4d8e-9122-332291042df5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b3f5cfb583ec4fceb9fb7428b08c00f6ca8e26b6
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62999967"
---
# <a name="marker_importance-enumeration"></a>marker_importance numaralandırma
Eşzamanlı Görselleştirici işaretleyicisinin önem düzeyini temsil eder.

## <a name="syntax"></a>Sözdizimi

```cpp
enum marker_importance;
```

## <a name="members"></a>Üyeler

### <a name="values"></a>Değerler

|Adı|Açıklama|
|----------|-----------------|
|`critical_importance`|İşaretleyicinin kritik öneme sahip olduğunu belirtir.|
|`high_importance`|İşaretleyicinin yüksek öneme sahip olduğunu belirtir.|
|`low_importance`|İşaretleyicinin düşük öneme sahip olduğunu belirtir.|
|`normal_importance`|İşaretleyicinin normal öneme sahip olduğunu belirtir.|

## <a name="requirements"></a>Gereksinimler
 **Başlık:** *cvmarkersobj.h*

 **Ad alanı:** Eşzamanlılık::diagnostik

## <a name="see-also"></a>Ayrıca bkz.
- [tanılama ad alanı](../profiling/diagnostic-namespace.md)