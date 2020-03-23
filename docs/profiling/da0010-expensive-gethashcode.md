---
title: 'DA0010: Pahalı GetHashCode | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DAExpensiveGetHashCode
- vs.performance.DA0010
- vs.performance.rules.DA0010
- vs.performance.10
ms.assetid: 3987e21a-5b4f-45e4-8a33-6b3f0a472c08
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 9ce982c7a98fd12749c66c89e47bd895d2fb6a5d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777692"
---
# <a name="da0010-expensive-gethashcode"></a>DA0010: Pahalı GetHashCode

|||
|-|-|
|Kural Id|DA0010|
|Kategori|.NET Çerçeve Kullanımı|
|Profil oluşturma yöntemleri|Örnekleme<br /><br /> .NET Bellek|
|İleti|GetHashCode işlevleri ucuz olmalı ve herhangi bir bellek ayırmamalıdır. Mümkünse karma kod işlevinin karmaşıklığını azaltın.|
|Mesaj türü|Uyarı|

## <a name="cause"></a>Nedeni
 Türünün GetHashCode yöntemine yapılan aramalar, profil oluşturma verilerinin önemli bir kısmıdır veya yöntem bellek ayırır.

## <a name="rule-description"></a>Kural açıklaması
 Karma, büyük bir koleksiyondaki belirli bir öğeyi hızla bulmak için bir tekniktir. Karma tablolar büyük olabileceğinden ve çok yüksek erişim oranlarını desteklemesi gerektiğinden, karma tablolar verimli olmalıdır. Bu gereksinimin bir sonucu da.NET Framework'deki GetHashCode yöntemlerinin bellek ayırmamasıdır. Bellek ayırma, çöp toplayıcıüzerindeki yükü artırır ve ayırma isteği sonucunda çöp toplamanın çalıştırılaması gerekli hale gelirse yöntemi olası gecikmelere maruz bırakır.

## <a name="how-to-fix-violations"></a>İhlalleri düzeltme
 Yöntemin karmaşıklığını azaltın.
