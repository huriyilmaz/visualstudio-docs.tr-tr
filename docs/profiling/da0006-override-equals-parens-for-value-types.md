---
title: DA0006 - Değer türleri için Equals() işlevini geçersiz | Microsoft Docs
description: Eşittir yöntemine veya ortak değer türünün eşitlik işleçlerine yapılan çağrılar, profil oluşturma verilerinin önemli bir oranıdır.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.rules.DAOverrideEquals
- vs.performance.6
- vs.performance.DA0006
- vs.performance.rules.DA0006
ms.assetid: 4d85bdd6-b571-47e0-afd6-ba3764e4eed5
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 0abdfb412d4adada9f4e41fd98258abfa1cb88e1
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626985"
---
# <a name="da0006-override-equals-for-value-types"></a>DA0006: Değer türleri için Equals() üzerine yazın

|Öğe|Değer|
|-|-|
|Kural Kimliği|DA0006|
|Kategori|.NET Framework Kullanım|
|Küfür yöntemleri|Örnekleme|
|İleti|Değer türlerinde Eşittir ve eşitlik işlecini geçersiz kılın.|
|Dağınıklık türü|Uyarı|

## <a name="cause"></a>Nedeni
 Eşittir yöntemine veya ortak değer türünün eşitlik işleçlerine yapılan çağrılar, profil oluşturma verilerinin önemli bir oranıdır. Daha verimli bir yöntem uygulamayı göz önünde bulundurarak.

## <a name="rule-description"></a>Kural açıklaması
 Değer türleri için, Equals'ın devralınmış uygulaması kitaplığı kullanır ve tür <xref:System.Reflection> içindeki tüm alanların içeriğini karşılar. Yansıma hesaplama açısından pahalıdır ve her alan için eşitlik karşılaştırma gereksiz olabilir. Kullanıcıların örnekleri karşılaştırmasını, sıralamasını veya karma tablo anahtarları olarak kullanmasını bekliyorsanız, değer türünüz Equals uygulamalı. Programlama diliniz işleç aşırı yüklemesi destekliyorsa, eşitlik ve eşitsizlik işleçlerinin bir uygulamasını da sağlasanız gerekir.

 Eşittir ve eşitlik işleçlerini geçersiz kılma hakkında daha fazla bilgi için bkz. Eşitleri Uygulama Yönergeleri ve Eşitlik [İşleci (==)](/dotnet/standard/design-guidelines/equality-operators).

## <a name="how-to-investigate-a-warning"></a>Uyarıyı araştırma
 Eşittir ve eşitlik işleçlerini uygulama örneği için, [ca1815 kod analizi kuralına bakın:](/dotnet/fundamentals/code-analysis/quality-rules/ca1815) Değer türlerinde eşittir ve işleç eşittir'i geçersiz kılın
