---
title: Güvenilirlik Uyarıları
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.reliabilityrules
helpviewer_keywords:
- warnings, reliability
- reliability warnings
- managed code analysis warnings, reliability warnings
ms.assetid: 77886846-10a2-4585-968a-7eb60ebe07e8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3449723394f603b4b726fa8ebf2258e2c8f4c46c
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85283391"
---
# <a name="reliability-warnings"></a>Güvenilirlik uyarıları

Güvenilirlik uyarıları, doğru bellek ve iş parçacığı kullanımı gibi kitaplık ve uygulama güvenilirliğini destekler. Güvenilirlik kuralları şunları içerir:

|Kural|Description|
|----------|-----------------|
|[CA2000: Kapsamı kaybetmeden önce nesneleri bırakın](../code-quality/ca2000.md)|Bir nesnenin sonlandırıcısının çalışmasını engelleyecek olağanüstü bir durum gerçekleşebileceği için, nesne ona olan tüm başvurular kapsam dışına çıkmadan açıkça atılmalıdır.|
|[CA2001: Sorunlu metotları çağırmaktan kaçının](../code-quality/ca2001.md)|Bir üye olası tehlikeli ya da sorunlu yöntemi çağırır.|
|[CA2002: Zayıf kimliği olan nesneleri kilitlemeyin](../code-quality/ca2002.md)|Bir nesneye uygulama etki alanları arasından erişilebiliyorsa o nesnenin zayıf bir kimliğe sahip olduğu söylenir. Zayıf kimliğe sahip bir nesne üzerinde kilit almayı deneyen iş parçacığı aynı nesne üzerinde bir kilide sahip olan farklı uygulama etki alanı içindeki ikinci iş parçacığı tarafından engellenebilir.|
|[CA2003: Fiberleri iş parçacığı olarak görmeyin](../code-quality/ca2003.md)|Yönetilen bir iş parçacığı Win32 iş parçacığı olarak kabul ediliyor.|
|[CA2004: GC.KeepAlive'a çağrıları kaldırın](../code-quality/ca2004.md)|SafeHandle kullanımına dönüştürüyorsanız, GC 'ye yapılan tüm çağrıları kaldırın. KeepAlive (nesne). Bu durumda, sınıfların GC çağrısı olması gerekmez. Canlı tutma, sonlandırıcılardan olmadığı varsayılarak ancak işletim sistemi tanıtıcısını sonuçlandırmak için SafeHandle 'ı kullanır.|
|[CA2006: Yerel kaynakları kapsamak için SafeHandle kullanın](../code-quality/ca2006.md)|Yönetilen kod içinde IntPtr kullanmak olası bir güvenlik ve güvenilirlik sorunu belirtebilir. IntPtr'nin tüm kullanımları onun yerine bir SafeHandle ya da benzer bir teknolojinin kullanımının gerekip gerekmediğini belirlemek için gözden geçirilmelidir.|
|[CA2007: Doğrudan bir Görevi beklemeyin](../code-quality/ca2007.md)|Zaman uyumsuz bir [awaits](/dotnet/csharp/language-reference/keywords/await) yöntem doğrudan bekler <xref:System.Threading.Tasks.Task> .|
|[CA2009: Bir ImmutableCollection değeri üzerinde ToImmutableCollection çağırma](../code-quality/ca2009.md)|`ToImmutable`Yöntem, ad alanından sabit bir koleksiyonda gereksiz şekilde çağrıldı <xref:System.Collections.Immutable> .|
|[CA2011: Özelliği, ayarlayıcısı içinde atama](../code-quality/ca2011.md) | Bir özelliğe yanlışlıkla kendi [set erişimcisi](/dotnet/csharp/programming-guide/classes-and-structs/using-properties#the-set-accessor)içinde bir değer atandı. |
|[CA2012: ValueTasks 'ı doğru kullanın](../code-quality/ca2012.md) | Üye etkinleştirmeleri tarafından döndürülen ValueTasks, doğrudan beklenmek üzere tasarlanmıştır.  Bir ValueTask 'ı birden çok kez kullanmaya çalışır veya tamamlanması bilinmadan önce bir sonuca doğrudan erişmek için bir özel durumla veya bozulmaya neden olabilir.  Bu tür bir ValueTask, büyük olasılıkla işlevsel bir hatanın göstergesidir ve performansın düşmesine neden olabilir. |
|[CA2013: ReferenceEquals değerini değer türleriyle kullanmayın](../code-quality/ca2013.md) | Kullanılarak değerler karşılaştırılırken <xref:System.Object.ReferenceEquals%2A?displayProperty=fullName> , objA ve objB değer türlerseler, yönteme geçirilmeden önce bunlar paketlenirler <xref:System.Object.ReferenceEquals%2A> . Bu, hem objA hem de objB bir değer türünün aynı örneğini temsil ediyorsa bile, <xref:System.Object.ReferenceEquals%2A> Yöntem false değerini döndürür. |
|[CA2014: Döngülerde stackalloc kullanmayın.](../code-quality/ca2014.md) | Bir stackalloc tarafından ayrılan yığın alanı yalnızca geçerli metodun çağrısının sonunda serbest bırakılır.  Bunu bir döngüde kullanmak, sınırsız yığın büyümesi ve nihai yığın taşması koşullarına yol açabilir. |
|[CA2015: MemoryManager T 'den türetilmiş türler için sonlandırıcılar tanımlama &lt;&gt;](../code-quality/ca2015.md) | ' Dan türetilmiş bir türe Sonlandırıcı eklemek <xref:System.Buffers.MemoryManager%601> , bir tarafından kullanılmaya devam edilirken belleğin serbest olmasına izin verebilir <xref:System.Span%601> . |
