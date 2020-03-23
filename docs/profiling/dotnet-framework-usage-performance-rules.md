---
title: .NET Framework Kullanım Performans Kuralları | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ab573755-6370-48aa-853d-a7321c424c79
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 5a740885d8876398bf86e279aa259e9169fcf7c2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779293"
---
# <a name="net-framework-usage-performance-rules"></a>.NET Framework kullanımı performans kuralları
the.NET Framework Usage kategorisindeki performans kuralları, en iyi duruma getirilebilen belirli yöntemleri tanımlar ve performans sorunları için araştırılabilen çöp toplama ve kilit çekişmesi gibi daha genel kullanım modellerini tanımlar.

|||
|-|-|
|[DA0001: Birleştirmeler için StringBuilder kullanın](../profiling/da0001-use-stringbuilder-for-concatenations.md)|Aramalar <xref:System.String.Concat(System.String,System.String)?displayProperty=fullName> profil oluşturma verilerinin önemli bir kısmıdır. Birden çok <xref:System.Text.StringBuilder> kesimden dizeleri oluşturmak için sınıfı kullanmayı düşünün.|
|[DA0005: Sık kullanılan GC2 koleksiyonları](../profiling/da0005-frequent-gc2-collections.md)|Ne derece yüksek sayıda .NET bellek nesnesi, nesil 2 çöp toplamada geri kazanılıyor. Çok fazla kısa ömürlü nesne nesil 1 koleksiyonuhayatta, bellek yönetimi maliyeti kolayca aşırı olabilir.|
|[DA0006: Değer türleri için Eşittir()'lerin üzerine yaz](../profiling/da0006-override-equals-parens-for-value-types.md)|`Equals` Yönteme yapılan çağrılar veya ortak değer türündeki eşitlik işleçleri profil oluşturma verilerinin önemli bir kısmıdır. Daha verimli bir yöntem uygulamayı düşünün.|
|[DA0007: Denetim akışı için özel durumlar kullanmaktan kaçının](../profiling/da0007-avoid-using-exceptions-for-control-flow.md)|Profil oluşturma verilerinde yüksek oranda .NET Framework özel durum işleyicileri çağrıldı. Atılan özel durumların sayısını azaltmak için diğer denetim akışı mantığını kullanmayı düşünün.|
|[DA0010: Pahalı GetHashCode](../profiling/da0010-expensive-gethashcode.md)|Tür `GetHashCode` yöntemine yapılan çağrılar, profil oluşturma verilerinin önemli `GetHashCode` bir kısmıdır veya yöntem bellek ayırır. Yöntemin karmaşıklığını azaltın.|
|[DA0011: Pahalı CompareTo](../profiling/da0011-expensive-compareto.md)|Türünün `CompareTo` yöntemi pahalıdır veya yöntem belleği ayırır. Yöntemin karmaşıklığını `CompareTo` azaltın.|
|[DA0012: Önemli miktarda Yansıma](../profiling/da0012-significant-amount-of-reflection.md)|Profil oluşturma <xref:System.Reflection?displayProperty=fullName> verilerinin <xref:System.Reflection.IReflect.InvokeMember%2A> <xref:System.Reflection.IReflect.GetMember%2A> önemli bir kısmı <xref:System.Type.InvokeMember%2A> gibi yöntemlere ve veya Type yöntemlerine yapılan çağrılardır. Mümkün olduğunda, bağımlı derlemelerin yöntemlerine erken bağlama ile bu yöntemleri değiştirmeyi düşünün.|
|[DA0013: Yüksek oranda String.Split veya String.Substring kullanımı](../profiling/da0013-high-usage-of-string-split-or-string-substring.md)|<xref:System.String.Split%2A?displayProperty=fullName> Aramalar veya <xref:System.String.Substring%2A> yöntemler profil oluşturma verilerinin önemli bir bölümütür. Bir <xref:System.String.IndexOf%2A> dizedeki bir alt dize nin varlığını sınalıyorsanız veya <xref:System.String.IndexOfAny%2A> kullanmayı düşünün.|
|[DA0018: 32 bitlik Uygulama işlem tarafından yönetilen bellek sınırlarında çalışıyor](../profiling/da0018-32-bit-application-running-at-process-managed-memory-limits.md)|Profil oluşturma işlemi sırasında toplanan sistem verileri,.NET Framework bellek yığınlarının yönetilen yığınların 32 bit lik bir işlemde ulaşabileceği maksimum boyuta yaklaştığını gösterir. .NET bellek profil oluşturma yöntemini kullanarak yeniden profil oluşturmayı ve yönetilen kaynakların uygulama tarafından kullanımını en iyi duruma çıkarmayı düşünün.|
|[DA0021: Yüksek oranda Gen 1 çöp koleksiyonları](../profiling/da0021-high-rate-of-gen-1-garbage-collections.md)|Nesil 1 çöp toplamada nispeten yüksek sayıda .NET bellek nesnesi geri kazanılıyor. Çok fazla kısa ömürlü nesne nesil 0 koleksiyonuhayatta, bellek yönetimi maliyeti kolayca aşırı olabilir.|
|[DA0022: Yüksek oranda Gen 2 çöp koleksiyonları](../profiling/da0022-high-rate-of-gen-2-garbage-collections.md)|Nesil 2 çöp toplamada çok sayıda .NET bellek nesnesi geri kazanılıyor. Çok fazla kısa ömürlü nesne nesil 1 koleksiyonuhayatta, bellek yönetimi maliyeti kolayca aşırı olabilir. Kilit çekişmeleri oranı DA0005 kuralının üst eşik değerini aştığında bu kural çerler.|
|[DA0023: Yüksek GC CPU süresi](../profiling/da0023-high-gc-cpu-time.md)|Profil oluşturma sırasında toplanan sistem performans verileri, çöp toplamada harcanan sürenin toplam uygulama işleme süresiyle karşılaştırıldığında önemli olduğunu gösterir.|
|[DA0024: Aşırı GC CPU süresi](../profiling/da0024-excessive-gc-cpu-time.md)|Profil oluşturma sırasında toplanan sistem performans verileri, çöp toplamada harcanan sürenin toplam uygulama işleme süresiyle karşılaştırıldığında aşırı derecede yüksek olduğunu gösterir. Bu kural, çöp toplamada harcanan süre DA0023 kuralının üst eşik değerini aştığında yangınlar.|
|[DA0038: Yüksek oranda kilit çekişmeleri](../profiling/da0038-high-rate-of-lock-contentions.md)|Profil oluşturma verileriyle toplanan sistem performans verileri, uygulama yürütme sırasında önemli ölçüde yüksek oranda kilit çekişmesi oluştuğunu gösterir. Çekişmelerin nedenini bulmak için eşzamanlılık profil oluşturma yöntemini kullanarak yeniden profil oluşturmayı düşünün.|
|[DA0039: Kilit çekişmeleri çok yüksek oranda](../profiling/da0039-very-high-rate-of-lock-contentions.md)|Profil oluşturma verileriyle toplanan sistem performans verileri, uygulama yürütme sırasında aşırı yüksek oranda kilit çekişmesi oluştuğunu gösterir. Çekişmelerin nedenini bulmak için eşzamanlılık profil oluşturma yöntemini kullanarak yeniden profil oluşturmayı düşünün. Kilit çekişmeleri oranı DA0038 kuralının üst eşik değerini aştığında bu kural çerler.|
