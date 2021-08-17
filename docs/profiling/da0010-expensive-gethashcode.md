---
title: DA0010 - Pahalı GetHashCode | Microsoft Docs
description: Türün GetHashCode yöntemine yapılan çağrılar, profil oluşturma verilerinin önemli bir oranıdır veya yöntem bellek ayırır.
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
ms.openlocfilehash: 3b32dba46e496e80c12b2fd351cc5dde0984d95b95ddd98492adb51ee9c52f1b
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121368805"
---
# <a name="da0010-expensive-gethashcode"></a>DA0010: Pahalı GetHashCode

|Öğe|Değer|
|-|-|
|Kural Kimliği|DA0010|
|Kategori|.NET Framework Kullanım|
|Profil oluşturma yöntemleri|Örnekleme<br /><br /> .NET Belleği|
|İleti|GetHashCode işlevleri ucuz olmalı ve bellek ayırmaz. Mümkünse karma kod işlevinin karmaşıklığını azaltabilirsiniz.|
|Mesaj türü|Uyarı|

## <a name="cause"></a>Nedeni
 Türün GetHashCode yöntemine yapılan çağrılar, profil oluşturma verilerinin önemli bir oranıdır veya yöntem bellek ayırır.

## <a name="rule-description"></a>Kural açıklaması
 Karma, büyük bir koleksiyonda belirli bir öğeyi hızla bulmak için kullanılan bir tekniktir. Karma tablolar büyük olduğundan ve çok yüksek erişim hızlarını desteklemesi gerektire olduğundan karma tabloların verimli olması gerekir. Bu gereksinimin bir anlamı, uygulamanın içinde GetHashCode yöntemlerinin .NET Framework ayırmamalarıdır. Bellek ayırma, atık toplayıcı üzerindeki yükü artırır ve ayırma isteğinin sonucu olarak çöp toplamayı çalıştırmak gerekli hale gelirse yöntemi olası gecikmelere maruz eder.

## <a name="how-to-fix-violations"></a>İhlalleri düzeltme
 Yönteminin karmaşıklığını azaltma.
