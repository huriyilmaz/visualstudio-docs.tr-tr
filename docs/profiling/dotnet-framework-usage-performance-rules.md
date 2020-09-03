---
title: Kullanım performans kuralları .NET Framework | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ab573755-6370-48aa-853d-a7321c424c79
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: ac78ffb3455940cf2379af44ff5c2bc5870dc684
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85532008"
---
# <a name="net-framework-usage-performance-rules"></a>.NET Framework kullanımı performans kuralları
The.NET Framework kullanım kategorisindeki performans kuralları, en iyi duruma getirilebilen ve ayrıca performans sorunları araştırılan çöp toplama ve kilit çekişmesi gibi daha genel kullanım düzenlerini tanımlayan belirli yöntemleri belirler.

|Kural|Description|
|-|-|
|[DA0001: Birleştirmeler için StringBuilder kullanma](../profiling/da0001-use-stringbuilder-for-concatenations.md)|İçin yapılan çağrılar <xref:System.String.Concat(System.String,System.String)?displayProperty=fullName> , profil oluşturma verilerinin önemli bir orandır. <xref:System.Text.StringBuilder>Birden çok kesimden dizeler oluşturmak için sınıfını kullanmayı düşünün.|
|[DA0005: Sık kullanılan GC2 koleksiyonları](../profiling/da0005-frequent-gc2-collections.md)|2. nesil atık toplamada, görece yüksek sayıda .NET bellek nesnesi geri kazanılır. Çok fazla sayıda kısa süreli nesne, 1. nesil toplandıktan sonra bellek yönetiminin maliyeti kolayca aşırı olabilir.|
|[DA0006: Değer türleri için Equals() üzerine yazın](../profiling/da0006-override-equals-parens-for-value-types.md)|`Equals`Bir ortak değer türünün yöntemine veya eşitlik işleçlerine yapılan çağrılar, profil oluşturma verilerinin önemli bir orandır. Daha verimli bir yöntem uygulamayı düşünün.|
|[DA0007: Denetim akışı için özel durumlar kullanmaktan kaçının](../profiling/da0007-avoid-using-exceptions-for-control-flow.md)|Profil oluşturma verilerinde yüksek oranda .NET Framework özel durum işleyicileri çağrıldı. Oluşturulan özel durumların sayısını azaltmak için diğer denetim akışı mantığını kullanmayı göz önünde bulundurun.|
|[DA0010: Pahalı GetHashCode](../profiling/da0010-expensive-gethashcode.md)|Türü yöntemine yapılan çağrılar, `GetHashCode` profil oluşturma verilerinin önemli bir oranıyla veya `GetHashCode` yöntemin belleği ayırır. Metodun karmaşıklığını azaltın.|
|[DA0011: Pahalı CompareTo](../profiling/da0011-expensive-compareto.md)|`CompareTo`Türünün yöntemi pahalıdır veya yöntem belleği ayırır. Metodun karmaşıklığını azaltın `CompareTo` .|
|[DA0012: Önemli miktarda Yansıma](../profiling/da0012-significant-amount-of-reflection.md)|Ve gibi yöntemleri yazmak gibi yöntemlere yapılan çağrılar, <xref:System.Reflection?displayProperty=fullName> <xref:System.Reflection.IReflect.InvokeMember%2A> <xref:System.Reflection.IReflect.GetMember%2A> <xref:System.Type.InvokeMember%2A> profil oluşturma verilerinin önemli bir orandır. Mümkün olduğunda, bu yöntemleri bağımlı derlemelerin yöntemlerine erken bağlama ile değiştirmeyi göz önünde bulundurun.|
|[DA0013: Yüksek oranda String.Split veya String.Substring kullanımı](../profiling/da0013-high-usage-of-string-split-or-string-substring.md)|Veya yöntemlerine yapılan çağrılar, <xref:System.String.Split%2A?displayProperty=fullName> <xref:System.String.Substring%2A> profil oluşturma verilerinin önemli bir bölümüdür. <xref:System.String.IndexOf%2A> <xref:System.String.IndexOfAny%2A> Bir dizedeki alt dizenin varlığını test ediyorsanız veya kullanmayı düşünün.|
|[DA0018: Yönetilen bellek limitlerinde çalışan 32 bit Uygulama](../profiling/da0018-32-bit-application-running-at-process-managed-memory-limits.md)|Profil oluşturma işlemi sırasında toplanan sistem verileri, approached .NET Framework bellek yığınlarının, yönetilen yığınlardaki 32 bitlik bir işlemde ulaşabileceği maksimum boyut olduğunu gösterir. .NET bellek profili oluşturma yöntemini kullanarak profil oluşturmayı yeniden düşünün ve yönetilen kaynakların uygulama tarafından kullanımını en iyi duruma getirme işlemini yapın.|
|[DA0021: Yüksek oranda 1. nesil atık toplama](../profiling/da0021-high-rate-of-gen-1-garbage-collections.md)|2. nesil atık toplamada, görece yüksek sayıda .NET bellek nesnesi geri kazanılır. Çok fazla sayıda kısa süreli nesne, nesil 0 topladıktan sonra bellek yönetiminin maliyeti kolayca aşırı olabilir.|
|[DA0022: Yüksek oranda 2. nesil atık toplama](../profiling/da0022-high-rate-of-gen-2-garbage-collections.md)|2. nesil atık toplamada yüksek sayıda .NET bellek nesnesi geri kazanılır. Çok fazla sayıda kısa süreli nesne, 1. nesil toplandıktan sonra bellek yönetiminin maliyeti kolayca aşırı olabilir. Bu kural, kilit çekişmelerinin oranı kural DA0005 üst eşik değerini aştığında ateşlenir.|
|[DA0023: Yüksek GC CPU süresi](../profiling/da0023-high-gc-cpu-time.md)|Profil oluşturma sırasında toplanan sistem performansı verileri, atık toplamada harcanan sürenin toplam uygulama işleme süresi ile karşılaştırıldığında önemli olduğunu gösterir.|
|[DA0024: aşırı GC CPU süresi](../profiling/da0024-excessive-gc-cpu-time.md)|Profil oluşturma sırasında toplanan sistem performansı verileri, atık toplamada harcanan sürenin toplam uygulama işleme süresi ile karşılaştırıldığında çok yüksek olduğunu gösterir. Bu kural, atık toplamada harcanan sürenin miktarı DA0023 kuralının üst eşik değerini aştığında ateşlenir.|
|[DA0038: yüksek oranda kilit çekişmeleri](../profiling/da0038-high-rate-of-lock-contentions.md)|Profil oluşturma verileriyle toplanan sistem performansı verileri, uygulama yürütmesi sırasında önemli ölçüde yüksek bir kilit çekişmesinin gerçekleştiğini gösterir. Çekişmelerin nedenini bulmak için eşzamanlılık profil oluşturma yöntemini kullanarak profil oluşturmayı yeniden düşünün.|
|[DA0039: çok yüksek oranda kilit çekişmeleri](../profiling/da0039-very-high-rate-of-lock-contentions.md)|Profil oluşturma verileriyle toplanan sistem performansı verileri, uygulama yürütme sırasında aşırı yüksek bir kilit çekişmesinin gerçekleştiğini gösterir. Çekişmelerin nedenini bulmak için eşzamanlılık profil oluşturma yöntemini kullanarak profil oluşturmayı yeniden düşünün. Bu kural, kilit çekişmelerinin oranı kural DA0038 üst eşik değerini aştığında ateşlenir.|
