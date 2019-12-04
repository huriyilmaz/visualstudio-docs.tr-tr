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
ms.openlocfilehash: 5a740885d8876398bf86e279aa259e9169fcf7c2
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74779293"
---
# <a name="net-framework-usage-performance-rules"></a>.NET Framework kullanımı performans kuralları
The.NET Framework kullanım kategorisindeki performans kuralları, en iyi duruma getirilebilen ve ayrıca performans sorunları araştırılan çöp toplama ve kilit çekişmesi gibi daha genel kullanım düzenlerini tanımlayan belirli yöntemleri belirler.

|||
|-|-|
|[DA0001: Birleştirmeler için StringBuilder kullanın](../profiling/da0001-use-stringbuilder-for-concatenations.md)|<xref:System.String.Concat(System.String,System.String)?displayProperty=fullName> çağrıları, profil oluşturma verilerinin önemli bir oranlarından oluşur. Birden çok kesimden dizeler oluşturmak için <xref:System.Text.StringBuilder> sınıfını kullanmayı düşünün.|
|[DA0005: Sık kullanılan GC2 koleksiyonları](../profiling/da0005-frequent-gc2-collections.md)|2\. nesil atık toplamada, görece yüksek sayıda .NET bellek nesnesi geri kazanılır. Çok fazla sayıda kısa süreli nesne, 1. nesil toplandıktan sonra bellek yönetiminin maliyeti kolayca aşırı olabilir.|
|[DA0006: Değer türleri için Eşittir()'lerin üzerine yaz](../profiling/da0006-override-equals-parens-for-value-types.md)|`Equals` yönteme veya bir ortak değer türünün eşitlik işleçlerine yapılan çağrılar, profil oluşturma verilerinin önemli bir orandır. Daha verimli bir yöntem uygulamayı düşünün.|
|[DA0007: Denetim akışı için özel durumlar kullanmaktan kaçının](../profiling/da0007-avoid-using-exceptions-for-control-flow.md)|Profil oluşturma verilerinde yüksek oranda .NET Framework özel durum işleyicileri çağrıldı. Oluşturulan özel durumların sayısını azaltmak için diğer denetim akışı mantığını kullanmayı göz önünde bulundurun.|
|[DA0010: Pahalı GetHashCode](../profiling/da0010-expensive-gethashcode.md)|`GetHashCode` yöntemine yapılan çağrılar, profil oluşturma verilerinin önemli bir oranındaki veya `GetHashCode` yöntemi belleği ayırır. Metodun karmaşıklığını azaltın.|
|[DA0011: Pahalı CompareTo](../profiling/da0011-expensive-compareto.md)|Türün `CompareTo` yöntemi pahalıdır veya yöntem belleği ayırır. `CompareTo` yönteminin karmaşıklığını azaltın.|
|[DA0012: Önemli miktarda Yansıma](../profiling/da0012-significant-amount-of-reflection.md)|<xref:System.Reflection.IReflect.InvokeMember%2A> ve <xref:System.Reflection.IReflect.GetMember%2A> gibi <xref:System.Reflection?displayProperty=fullName> yöntemlere yapılan çağrılar veya <xref:System.Type.InvokeMember%2A> gibi yöntemleri yazmak, profil oluşturma verilerinin önemli bir oranlarından oluşur. Mümkün olduğunda, bu yöntemleri bağımlı derlemelerin yöntemlerine erken bağlama ile değiştirmeyi göz önünde bulundurun.|
|[DA0013: Yüksek oranda String.Split veya String.Substring kullanımı](../profiling/da0013-high-usage-of-string-split-or-string-substring.md)|<xref:System.String.Split%2A?displayProperty=fullName> veya <xref:System.String.Substring%2A> yöntemlerine yapılan çağrılar, profil oluşturma verilerinin önemli bir bölümüdür. Bir dizedeki alt dizenin varlığını test ediyorsanız <xref:System.String.IndexOf%2A> veya <xref:System.String.IndexOfAny%2A> kullanmayı düşünün.|
|[DA0018: 32 bitlik Uygulama işlem tarafından yönetilen bellek sınırlarında çalışıyor](../profiling/da0018-32-bit-application-running-at-process-managed-memory-limits.md)|Profil oluşturma işlemi sırasında toplanan sistem verileri, approached .NET Framework bellek yığınlarının, yönetilen yığınlardaki 32 bitlik bir işlemde ulaşabileceği maksimum boyut olduğunu gösterir. .NET bellek profili oluşturma yöntemini kullanarak profil oluşturmayı yeniden düşünün ve yönetilen kaynakların uygulama tarafından kullanımını en iyi duruma getirme işlemini yapın.|
|[DA0021: Yüksek oranda Gen 1 çöp koleksiyonları](../profiling/da0021-high-rate-of-gen-1-garbage-collections.md)|2\. nesil atık toplamada, görece yüksek sayıda .NET bellek nesnesi geri kazanılır. Çok fazla sayıda kısa süreli nesne, nesil 0 topladıktan sonra bellek yönetiminin maliyeti kolayca aşırı olabilir.|
|[DA0022: Yüksek oranda Gen 2 çöp koleksiyonları](../profiling/da0022-high-rate-of-gen-2-garbage-collections.md)|2\. nesil atık toplamada yüksek sayıda .NET bellek nesnesi geri kazanılır. Çok fazla sayıda kısa süreli nesne, 1. nesil toplandıktan sonra bellek yönetiminin maliyeti kolayca aşırı olabilir. Bu kural, kilit çekişmelerinin oranı kural DA0005 üst eşik değerini aştığında ateşlenir.|
|[DA0023: Yüksek GC CPU süresi](../profiling/da0023-high-gc-cpu-time.md)|Profil oluşturma sırasında toplanan sistem performansı verileri, atık toplamada harcanan sürenin toplam uygulama işleme süresi ile karşılaştırıldığında önemli olduğunu gösterir.|
|[DA0024: aşırı GC CPU süresi](../profiling/da0024-excessive-gc-cpu-time.md)|Profil oluşturma sırasında toplanan sistem performansı verileri, atık toplamada harcanan sürenin toplam uygulama işleme süresi ile karşılaştırıldığında çok yüksek olduğunu gösterir. Bu kural, atık toplamada harcanan sürenin miktarı DA0023 kuralının üst eşik değerini aştığında ateşlenir.|
|[DA0038: yüksek oranda kilit çekişmeleri](../profiling/da0038-high-rate-of-lock-contentions.md)|Profil oluşturma verileriyle toplanan sistem performansı verileri, uygulama yürütmesi sırasında önemli ölçüde yüksek bir kilit çekişmesinin gerçekleştiğini gösterir. Çekişmelerin nedenini bulmak için eşzamanlılık profil oluşturma yöntemini kullanarak profil oluşturmayı yeniden düşünün.|
|[DA0039: çok yüksek oranda kilit çekişmeleri](../profiling/da0039-very-high-rate-of-lock-contentions.md)|Profil oluşturma verileriyle toplanan sistem performansı verileri, uygulama yürütme sırasında aşırı yüksek bir kilit çekişmesinin gerçekleştiğini gösterir. Çekişmelerin nedenini bulmak için eşzamanlılık profil oluşturma yöntemini kullanarak profil oluşturmayı yeniden düşünün. Bu kural, kilit çekişmelerinin oranı kural DA0038 üst eşik değerini aştığında ateşlenir.|
