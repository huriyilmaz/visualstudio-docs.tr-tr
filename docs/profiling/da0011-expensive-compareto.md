---
title: DA0011-pahalı CompareTo | Microsoft Docs
description: Türün CompareTo yöntemi pahalıdır veya bellek ayırır.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.DA0011
- vs.performance.rules.DAExpensiveCompareTo
- vs.performance.11
- vs.performance.rules.DA0011
ms.assetid: 239a381d-0d97-4367-8668-746c93f5af2c
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 91219bed2ca0e8b4bbc28825e1505b9d5f78bbc8
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2021
ms.locfileid: "102466160"
---
# <a name="da0011-expensive-compareto"></a>DA0011: Pahalı CompareTo

|Öğe|Değer|
|-|-|
|Kural kimliği|DA0011|
|Kategori|.NET Framework kullanımı|
|Profil oluşturma yöntemleri|Örnekleme<br /><br /> .NET belleği|
|İleti|CompareTo işlevleri, ucuz olmalı ve herhangi bir bellek ayırmamalıdır. Mümkünse, CompareTo işlevi karmaşıklığını azaltın.|
|Kural türü|Uyarı|

## <a name="cause"></a>Nedeni
 Türün CompareTo yöntemi pahalıdır veya bellek ayırır.

## <a name="rule-description"></a>Kural açıklaması
 CompareTo metotları etkili olmalıdır ve bellek ayırmamalıdır.

## <a name="how-to-fix-violations"></a>İhlalleri çözme
 CompareTo yönteminin karmaşıklığını azaltın.
