---
title: DA0010-pahalı GetHashCode | Microsoft Docs
description: Türün GetHashCode yöntemine yapılan çağrılar, profil oluşturma verilerinin önemli bir oranıyla veya yöntemin belleği ayırır.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.rules.DAExpensiveGetHashCode
- vs.performance.DA0010
- vs.performance.rules.DA0010
- vs.performance.10
ms.assetid: 3987e21a-5b4f-45e4-8a33-6b3f0a472c08
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 1347b390c5d70478f2c7311746e6282fa344ba98
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122107868"
---
# <a name="da0010-expensive-gethashcode"></a>DA0010: Pahalı GetHashCode

|Öğe|Değer|
|-|-|
|Kural kimliği|DA0010|
|Kategori|.NET Framework Kullanımıyla|
|Profil oluşturma yöntemleri|Örnekleme<br /><br /> .NET belleği|
|İleti|GetHashCode işlevleri bir tek EAP olmalı ve herhangi bir bellek ayırmamalıdır. Mümkünse karma kod işlevinin karmaşıklığını azaltın.|
|Mesaj türü|Uyarı|

## <a name="cause"></a>Nedeni
 Türün GetHashCode yöntemine yapılan çağrılar, profil oluşturma verilerinin önemli bir oranıyla veya yöntemin belleği ayırır.

## <a name="rule-description"></a>Kural açıklaması
 Karma, büyük bir koleksiyondaki belirli bir öğeyi hızlı bir şekilde bulmanın bir tekniğidir. Karma tabloları büyük olabileceğinden ve çok yüksek erişim fiyatlarını desteklemesi gerektiğinden, karma tabloların etkili olması gerekir. bu gereksinimin bir engel, .NET Framework GetHashCode yöntemlerinin bellek ayırmamalıdır. Bellek ayırma, atık toplayıcıdaki yükü artırır ve ayırma isteğinin sonucu olarak çöp toplamayı çalıştırmak için gerekli hale gelirse, olası gecikmelerle yöntemi ortaya çıkarır.

## <a name="how-to-fix-violations"></a>İhlalleri çözme
 Metodun karmaşıklığını azaltın.
