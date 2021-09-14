---
title: DA0012 - Önemli miktarda Yansıma | Microsoft Docs
description: InvokeMember ve GetMember gibi System.Reflection yöntemlerine veya MemberInvoke gibi Tür yöntemlerine yapılan çağrılar, profil oluşturma verilerinin önemli bir oranıdır.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.rules.DAReflection
- vs.performance.12
- vs.performance.rules.DA0012
- vs.performance.DA0011
ms.assetid: c92a1d76-21fa-426e-8b1b-a3c08e9bcbca
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: aecafde31cf799122b9aae60003c1de22b026c8e
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126637153"
---
# <a name="da0012-significant-amount-of-reflection"></a>DA0012: Önemli miktarda Yansıma

|Öğe|Değer|
|-|-|
|Kural Kimliği|DA0012|
|Kategori|.NET Framework Kullanım|
|Profil oluşturma yöntemleri|Örnekleme|
|İleti|Yansımayı aşırı kullanıyor olabilir. Pahalı bir işlemdir.|
|Kural türü|Uyarı|

## <a name="cause"></a>Nedeni
 InvokeMember ve GetMember gibi System.Reflection yöntemlerine veya MemberInvoke gibi Tür yöntemlerine yapılan çağrılar, profil oluşturma verilerinin önemli bir oranıdır. Mümkün olduğunda, bu yöntemleri bağımlı derlemelerin yöntemlerine erken bağlama ile değiştirmeyi göz önünde bulundurarak.

## <a name="rule-description"></a>Kural açıklaması
 Yansıma, .NET Framework bağımlı bir çalışma zamanı Derlemesi'ne geç bağlama gerçekleştirmek veya çalışma zamanında yeni türler oluşturmak ve dinamik olarak yürütmek için kullanılmaktadır. Ancak, bu teknikler sık kullanılırsa veya sıkı döngülerde çağrılırsa performansı düşürebilir.

 Daha fazla bilgi [](/previous-versions/msp-n-p/ff647790(v=pandp.10)#reflection-and-late-binding) için MSDN'de Microsoft Patterns and Practices kitaplığının .NET Uygulama Performansını ve Ölçeklenebilirlik hacmini Geliştirme bölümünde Bölüm 5 - Yönetilen Kod Performansını Geliştirme bölümünün Yansıma ve Geç Bağlama bölümüne bakın.

## <a name="how-to-investigate-a-warning"></a>Uyarıyı araştırma
 Profil oluşturma verilerine ilişkin İşlev Ayrıntıları Görünümüne gitmek için Hatalar Listesi [penceresindeki](../profiling/function-details-view.md) iletiye çift tıklayın. Programın .NET Yansıma API'lerini en sık kullanan bölümlerini bulmak için System.Type veya System.Reflection yönteminin çağırma işlevlerini inceleme. Meta veri dönüş yöntemleri kullanmaktan kaçının. Uygulamanın performansı kritik olduğunda, gecikmeli bağlamayı kullanmaktan ve çalışma zamanında dinamik olarak türler oluşturmaktan kaçınmanız gerekir.
