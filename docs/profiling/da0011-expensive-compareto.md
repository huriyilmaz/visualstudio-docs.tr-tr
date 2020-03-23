---
title: 'DA0011: Pahalı CompareTo | Microsoft Dokümanlar'
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779434"
---
# <a name="da0011-expensive-compareto"></a>DA0011: Pahalı CompareTo

|||
|-|-|
|Kural Id|DA0011|
|Kategori|.NET Çerçeve Kullanımı|
|Profil oluşturma yöntemleri|Örnekleme<br /><br /> .NET Bellek|
|İleti|CompareTo işlevleri ucuz olmalı ve herhangi bir bellek ayırmamalıdır. Mümkünse CompareTo işlevinin karmaşıklığını azaltın.|
|Kural türü|Uyarı|

## <a name="cause"></a>Nedeni
 CompareTo türündeki yöntem pahalıdır veya belleği ayırır.

## <a name="rule-description"></a>Kural açıklaması
 CompareTo yöntemleri verimli olmalı ve bellek ayırmamalıdır.

## <a name="how-to-fix-violations"></a>İhlalleri düzeltme
 CompareTo yönteminin karmaşıklığını azaltın.
