---
title: 'DA0011: pahalı CompareTo | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.DA0011
- vs.performance.rules.DAExpensiveCompareTo
- vs.performance.11
- vs.performance.rules.DA0011
ms.assetid: 239a381d-0d97-4367-8668-746c93f5af2c
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: d0eb4566fd4c8a513b1492cecffc16cb94a1fd83
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74779434"
---
# <a name="da0011-expensive-compareto"></a>DA0011: Pahalı CompareTo

|||
|-|-|
|Kural Kimliği|DA0011|
|Kategori|.NET Framework kullanımı|
|Profil oluşturma yöntemleri|Aşağıdakine<br /><br /> .NET belleği|
|İleti|CompareTo işlevleri, ucuz olmalı ve herhangi bir bellek ayırmamalıdır. Mümkünse, CompareTo işlevi karmaşıklığını azaltın.|
|Kural türü|Uyarı|

## <a name="cause"></a>Sebep
 Türün CompareTo yöntemi pahalıdır veya bellek ayırır.

## <a name="rule-description"></a>Kural açıklaması
 CompareTo metotları etkili olmalıdır ve bellek ayırmamalıdır.

## <a name="how-to-fix-violations"></a>İhlalleri çözme
 CompareTo yönteminin karmaşıklığını azaltın.
