---
title: DA0012 - Önemli miktarda Yansıma | Microsoft Docs
description: InvokeMember ve GetMember gibi System.Reflection yöntemlerine veya MemberInvoke gibi Tür yöntemlerine yapılan çağrılar, profil oluşturma verilerinin önemli bir oranıdır.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.rules.DAReflection
- vs.performance.12
- vs.performance.rules.DA0012
- vs.performance.DA0012
ms.assetid: c92a1d76-21fa-426e-8b1b-a3c08e9bcbca
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 89368361b269dec80a46821395b6a0a23ce7e5ea
ms.sourcegitcommit: 965372ad0d75f015403c1af508080bf799914ce3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "135804369"
---
# <a name="da0012-significant-amount-of-reflection"></a>DA0012: Önemli miktarda Yansıma

|Öğe|Değer|
|-|-|
|Kural Kimliği|DA0012|
|Kategori|.NET Framework Kullanımı|
|Profil oluşturma yöntemleri|Örnekleme|
|İleti|Yansımayı aşırı kullanıyor olabilir. Pahalı bir işlemdir.|
|Kural türü|Uyarı|

## <a name="cause"></a>Nedeni
 InvokeMember ve GetMember gibi System.Reflection yöntemlerine veya MemberInvoke gibi Tür yöntemlerine yapılan çağrılar, profil oluşturma verilerinin önemli bir oranıdır. Mümkün olduğunda, bu yöntemleri bağımlı derlemelerin yöntemlerine erken bağlama ile değiştirmeyi göz önünde bulundurarak.

## <a name="rule-description"></a>Kural açıklaması
 Yansıma, .NET Framework bağımlı bir çalışma zamanı Derlemesi'ne geç bağlama gerçekleştirmek veya çalışma zamanında yeni türler oluşturmak ve dinamik olarak yürütmek için kullanılmaktadır. Ancak bu teknikler sık kullanılırsa veya sıkı döngülerde çağrılsa performansı düşürebilir.

 Daha fazla bilgi [](/previous-versions/msp-n-p/ff647790(v=pandp.10)#reflection-and-late-binding) için MSDN'de Microsoft Patterns and Practices kitaplığının .NET Uygulama Performansını ve Ölçeklenebilirlik hacmini geliştirme bölümündeki 5. Bölüm - Yönetilen Kod Performansını Geliştirme bölümünün Yansıma ve Geç Bağlama bölümüne bakın.

## <a name="how-to-investigate-a-warning"></a>Uyarıyı araştırma
 Profil oluşturma verilerine ilişkin İşlev Ayrıntıları Görünümüne gitmek için Hatalar [Listesi penceresindeki](../profiling/function-details-view.md) iletiye çift tıklayın. Programın .NET Yansıma API'lerini en sık kullanan bölümlerini bulmak için System.Type veya System.Reflection yönteminin çağırma işlevlerini inceleme. Meta veri dönüş yöntemleri kullanmaktan kaçının. Uygulamanın performansı kritik öneme sahip olduğunda, çalışma zamanında dinamik olarak türler oluşturmaktan ve geç bağlamayı kullanmaktan kaçınmanız gerekir.
