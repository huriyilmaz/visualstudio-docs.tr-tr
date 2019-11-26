---
title: 'DA0006: değer türleri için Equals () öğesini geçersiz kıl | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.rules.DAOverrideEquals
- vs.performance.6
- vs.performance.DA0006
- vs.performance.rules.DA0006
ms.assetid: 4d85bdd6-b571-47e0-afd6-ba3764e4eed5
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ae18d4cb69de5faa4289a99cbb53b273443b494a
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300986"
---
# <a name="da0006-override-equals-for-value-types"></a>DA0006: Değer türleri için Eşittir()'lerin üzerine yaz
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kural kimliği | DA0006 |  
| Kategori |. NET Framework kullanımı |  
| Profikenme yöntemleri | Örnekleme |  
| İleti | Değer türlerinde Equals ve eşitlik işlecini geçersiz kılın. |  
| Messge türü | Uyarı |  
  
## <a name="cause"></a>Nedeni  
 Eşittir yöntemine veya bir ortak değer türünün eşitlik işleçlerine yapılan çağrılar, profil oluşturma verilerinin önemli bir orandır. Daha verimli bir yöntem uygulamayı düşünün.  
  
## <a name="rule-description"></a>Kural Tanımı  
 Değer türleri için, eşittir devralınan uygulama <xref:System.Reflection> kitaplığını kullanır ve bu türdeki tüm alanların içeriğini karşılaştırır. Yansıma hesaplama açısından pahalıdır ve her alan için eşitlik karşılaştırma gereksiz olabilir. Kullanıcıların örnekleri karşılaştırmasını veya sıralamasını veya onları karma tablo anahtarları olarak kullanmasını bekleliyorsanız, değer türü eşittir değerini uygulamalıdır. Programlama diliniz işleç aşırı yüklemesini destekliyorsa eşitlik ve eşitsizlik işleçleri de bir uygulama sağlamalısınız.  
  
 Eşit ve eşitlik operatörlerinin nasıl geçersiz kılındığı hakkında daha fazla bilgi için bkz. [Equals ve eşitlik işleci (= =) uygulamak Için yönergeler](https://go.microsoft.com/fwlink/?LinkId=177818).  
  
## <a name="how-to-investigate-a-warning"></a>Uyarı araştırma  
 Eşittir ve eşitlik işleçlerini uygulamayla ilgili bir örnek için, bkz. kod analizi kuralı [CA1815: geçersiz kılma Equals ve değer türlerinde işleç eşittir](../code-quality/ca1815-override-equals-and-operator-equals-on-value-types.md)
