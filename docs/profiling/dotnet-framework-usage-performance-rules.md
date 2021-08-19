---
title: .NET Framework Kullanım Performansı Kuralları | Microsoft Docs
description: .NET Framework Usage kategorisindeki performans kurallarını anlama. İyileştirilmiş ve daha genel kullanım desenlerini belirleyen belirli yöntemleri belirleme.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ab573755-6370-48aa-853d-a7321c424c79
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 6fd7ae10e576cf9c5645fb56be5e242ea926d207
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122033843"
---
# <a name="net-framework-usage-performance-rules"></a>.NET Framework kullanımı performans kuralları
the.NET Framework Kullanımı kategorisindeki performans kuralları, iyileştirilmiş olan belirli yöntemleri ve ayrıca atık toplama ve kilitleme gibi performans sorunları için araştırılacak daha genel kullanım desenlerini de tanımlamayı sağlar.

|Kural|Açıklama|
|-|-|
|[DA0001: Birleştirmeler için StringBuilder kullanma](../profiling/da0001-use-stringbuilder-for-concatenations.md)|çağrıları, <xref:System.String.Concat(System.String,System.String)?displayProperty=fullName> profil oluşturma verilerinin önemli bir oranıdır. Birden çok <xref:System.Text.StringBuilder> segmentten dizeler oluşturmak için sınıfını kullanmayı göz önünde bulundurabilirsiniz.|
|[DA0005: Sık kullanılan GC2 koleksiyonları](../profiling/da0005-frequent-gc2-collections.md)|Nesil 2 çöp toplamada görece yüksek sayıda .NET bellek nesnesi geri istenıyor. Çok fazla kısa süreli nesne nesil 1 toplamaya devam ederse, bellek yönetiminin maliyeti kolayca aşırıya inebilir.|
|[DA0006: Değer türleri için Equals() üzerine yazın](../profiling/da0006-override-equals-parens-for-value-types.md)|Yönteme yapılan çağrılar veya ortak değer türünün eşitlik işleçleri, profil `Equals` oluşturma verilerinin önemli bir oranıdır. Daha verimli bir yöntem uygulamayı göz önünde bulundurarak.|
|[DA0007: Denetim akışı için özel durumlar kullanmaktan kaçının](../profiling/da0007-avoid-using-exceptions-for-control-flow.md)|Profil oluşturma veri .NET Framework yüksek oranda özel durum işleyicileri çağrıldı. Diğer denetim akışı mantığını kullanarak, atılan özel durumların sayısını azaltmayı göz önünde bulundurarak.|
|[DA0010: Pahalı GetHashCode](../profiling/da0010-expensive-gethashcode.md)|Türün `GetHashCode` yöntemine yapılan çağrılar, profil oluşturma verilerinin önemli bir oranıdır veya `GetHashCode` yöntem bellek ayırır. Yönteminin karmaşıklığını azaltma.|
|[DA0011: Pahalı CompareTo](../profiling/da0011-expensive-compareto.md)|`CompareTo`türünün yöntemi pahalıdır veya yöntem bellek ayırır. Yönteminin karmaşıklığını `CompareTo` azaltma.|
|[DA0012: Önemli miktarda Yansıma](../profiling/da0012-significant-amount-of-reflection.md)|ve veya gibi Tür yöntemlerine yapılan <xref:System.Reflection?displayProperty=fullName> çağrılar, profil oluşturma <xref:System.Reflection.IReflect.InvokeMember%2A> <xref:System.Reflection.IReflect.GetMember%2A> <xref:System.Type.InvokeMember%2A> verilerinin önemli bir oranıdır. Mümkün olduğunda, bu yöntemleri bağımlı derlemelerin yöntemlerine erken bağlama ile değiştirmeyi göz önünde bulundurarak.|
|[DA0013: Yüksek oranda String.Split veya String.Substring kullanımı](../profiling/da0013-high-usage-of-string-split-or-string-substring.md)|veya <xref:System.String.Split%2A?displayProperty=fullName> yöntemlerine <xref:System.String.Substring%2A> yapılan çağrılar, profil oluşturma verilerinin önemli bir kısmıdır. bir <xref:System.String.IndexOf%2A> dizede <xref:System.String.IndexOfAny%2A> bir alt dizenin varlığını test ediyorsanız veya kullanmayı düşünün.|
|[DA0018: Yönetilen bellek limitlerinde çalışan 32 bit Uygulama](../profiling/da0018-32-bit-application-running-at-process-managed-memory-limits.md)|Profil oluşturma çalıştırması sırasında toplanan sistem verileri, .NET Framework yığınların 32 bitlik bir işlemde ulaşacak en büyük boyuta yaklaştığını gösterir. .NET bellek profili oluşturma yöntemini kullanarak ve uygulama tarafından yönetilen kaynakların kullanımını en iyi duruma getirerek profil oluşturmayı yeniden göz önünde bulundurabilirsiniz.|
|[DA0021: Yüksek oranda 1. nesil atık toplama](../profiling/da0021-high-rate-of-gen-1-garbage-collections.md)|Nesil 1 çöp toplamada görece yüksek sayıda .NET bellek nesnesi geri istenıyor. Çok fazla kısa süreli nesne nesil 0 toplamaya devam ederse, bellek yönetiminin maliyeti kolayca aşırıya inebilir.|
|[DA0022: Yüksek oranda 2. nesil atık toplama](../profiling/da0022-high-rate-of-gen-2-garbage-collections.md)|Nesil 2 çöp toplamada çok sayıda .NET bellek nesnesi geri istenıyor. Çok fazla kısa süreli nesne nesil 1 toplamaya devam ederse, bellek yönetiminin maliyeti kolayca aşırıya inebilir. Bu kural, kilit içeriklerinin oranı DA0005 kuralının üst eşik değerini aştı mı?|
|[DA0023: Yüksek GC CPU süresi](../profiling/da0023-high-gc-cpu-time.md)|Profil oluşturma sırasında toplanan sistem performansı verileri, çöp toplamada harcanan sürenin toplam uygulama işleme süresine kıyasla önemli olduğunu gösterir.|
|[DA0024: Aşırı GC CPU süresi](../profiling/da0024-excessive-gc-cpu-time.md)|Profil oluşturma sırasında toplanan sistem performansı verileri, çöp toplamada harcanan sürenin toplam uygulama işleme süresine kıyasla aşırı yüksek olduğunu gösterir. Bu kural, atık toplamada harcanan süre DA0023 kuralının üst eşik değerini aştıklarında sılaya neden olur.|
|[DA0038: Yüksek oranda kilit içeriği](../profiling/da0038-high-rate-of-lock-contentions.md)|Profil oluşturma verileriyle toplanan sistem performansı verileri, uygulama yürütme sırasında önemli ölçüde yüksek oranda kilit tartışmaları meydana geldiğine işaret ediyor. İçeriklerin nedenini bulmak için eşzamanlılık profil oluşturma yöntemini kullanarak profil oluşturmayı yeniden düşünün.|
|[DA0039: Çok yüksek oranda kilit içeriği](../profiling/da0039-very-high-rate-of-lock-contentions.md)|Profil oluşturma verileriyle toplanan sistem performansı verileri, uygulama yürütme sırasında aşırı yüksek oranda kilit tartışmaları meydana geldiğine işaret ediyor. İçeriklerin nedenini bulmak için eşzamanlılık profil oluşturma yöntemini kullanarak profil oluşturmayı yeniden düşünün. Bu kural, kilit içeriklerinin oranı DA0038 kuralının üst eşik değerini aştı mı?|
