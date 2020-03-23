---
title: 'DA0006: Değer türleri için Geçersiz Kılma Eşittir() | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DAOverrideEquals
- vs.performance.6
- vs.performance.DA0006
- vs.performance.rules.DA0006
ms.assetid: 4d85bdd6-b571-47e0-afd6-ba3764e4eed5
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 9e097d6d8c9a7b82fac53fd37951644eb7eb5e59
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779538"
---
# <a name="da0006-override-equals-for-value-types"></a>DA0006: Değer türleri için Eşittir()'lerin üzerine yaz

|||
|-|-|
|Kural Id|DA0006|
|Kategori|.NET Çerçeve Kullanımı|
|Profiiling yöntemleri|Örnekleme|
|İleti|Değer türlerinde Eşitleri ve eşitlik işlecini geçersiz kılın.|
|Messge türü|Uyarı|

## <a name="cause"></a>Nedeni
 Eşitler yöntemine yapılan çağrılar veya ortak değer türündeki eşitlik işleçleri profil oluşturma verilerinin önemli bir kısmıdır. Daha verimli bir yöntem uygulamayı düşünün.

## <a name="rule-description"></a>Kural açıklaması
 Değer türleri için, Eşitler'in devralınan uygulaması <xref:System.Reflection> kitaplığı kullanır ve türdeki tüm alanların içeriğini karşılaştırır. Yansıma hesaplama açısından pahalıdır ve her alan için eşitlik karşılaştırma gereksiz olabilir. Kullanıcıların örnekleri karşılaştırmasını veya sıralamasını veya bunları karma tablo anahtarları olarak kullanmasını bekliyorsanız, değer türünüz Eşittir'leri uygulamalıdır. Programlama diliniz operatör aşırı yüklemesini destekliyorsa, eşitlik ve eşitsizlik işleçlerinin uygulanmasını da sağlamanız gerekir.

 Eşitleri ve eşitlik işleçlerini nasıl geçersiz kılacakları hakkında daha fazla bilgi için, [Eşitleri ve Eşitlik Operatörlerini Uygulama Yönergeleri'ne (==)](/dotnet/standard/design-guidelines/equality-operators)bakın.

## <a name="how-to-investigate-a-warning"></a>Bir uyarı nasıl araştırılı
 Eşitler ve eşitlik işleçleri uygulama örneği için, kod çözümleme kuralı [CA1815 bakın: Geçersiz kılma eşittir ve işleç eşittir değer türlerinde eşittir](../code-quality/ca1815.md)
