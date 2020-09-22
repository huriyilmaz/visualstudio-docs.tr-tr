---
title: Güvenilirlik kuralları
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.reliabilityrules
helpviewer_keywords:
- rules, reliability
- reliability rules
- managed code analysis rules, reliability rules
ms.assetid: 77886846-10a2-4585-968a-7eb60ebe07e8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e0a35b9c49f2eb5655eeb67721b0fafdbbe1e087
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808278"
---
# <a name="reliability-rules"></a>Güvenilirlik kuralları

Güvenilirlik kuralları, doğru bellek ve iş parçacığı kullanımı gibi kitaplık ve uygulama güvenilirliğini destekler.

|Kural|Açıklama|
|----------|-----------------|
|[CA2000: Kapsamı kaybetmeden önce nesneleri bırakın](../code-quality/ca2000.md)|Bir nesnenin sonlandırıcısının çalışmasını engelleyecek olağanüstü bir durum gerçekleşebileceği için, nesne ona olan tüm başvurular kapsam dışına çıkmadan açıkça atılmalıdır.|
|[CA2002: Zayıf kimliği olan nesneleri kilitlemeyin](../code-quality/ca2002.md)|Bir nesneye uygulama etki alanları arasından erişilebiliyorsa o nesnenin zayıf bir kimliğe sahip olduğu söylenir. Zayıf kimliğe sahip bir nesne üzerinde kilit almayı deneyen iş parçacığı aynı nesne üzerinde bir kilide sahip olan farklı uygulama etki alanı içindeki ikinci iş parçacığı tarafından engellenebilir.|
|[CA2007: Doğrudan bir Görevi beklemeyin](../code-quality/ca2007.md)|Zaman uyumsuz bir [awaits](/dotnet/csharp/language-reference/keywords/await) yöntem doğrudan bekler <xref:System.Threading.Tasks.Task> .|
|[CA2008: TaskScheduler geçirmeden görev oluşturmayın](../code-quality/ca2008.md)|Bir görev oluşturma veya devamlılık işlemi, bir parametre belirtmeyen bir yöntem aşırı yüklemesi kullanır <xref:System.Threading.Tasks.TaskScheduler> .|
|[CA2009: Bir ImmutableCollection değeri üzerinde ToImmutableCollection çağırma](../code-quality/ca2009.md)|`ToImmutable` Yöntem, ad alanından sabit bir koleksiyonda gereksiz şekilde çağrıldı <xref:System.Collections.Immutable> .|
|[CA2011: Özelliği, ayarlayıcısı içinde atama](../code-quality/ca2011.md) | Bir özelliğe yanlışlıkla kendi [set erişimcisi](/dotnet/csharp/programming-guide/classes-and-structs/using-properties#the-set-accessor)içinde bir değer atandı. |
|[CA2012: ValueTask’leri doğru kullanın](../code-quality/ca2012.md) | Üye etkinleştirmeleri tarafından döndürülen ValueTasks, doğrudan beklenmek üzere tasarlanmıştır.  Bir ValueTask 'ı birden çok kez kullanmaya çalışır veya tamamlanması bilinmadan önce bir sonuca doğrudan erişmek için bir özel durumla veya bozulmaya neden olabilir.  Bu tür bir ValueTask, büyük olasılıkla işlevsel bir hatanın göstergesidir ve performansın düşmesine neden olabilir. |
|[CA2013: ReferenceEquals metodunu değer türleriyle birlikte kullanmayın](../code-quality/ca2013.md) | Kullanılarak değerler karşılaştırılırken <xref:System.Object.ReferenceEquals%2A?displayProperty=fullName> , objA ve objB değer türlerseler, yönteme geçirilmeden önce bunlar paketlenirler <xref:System.Object.ReferenceEquals%2A> . Bu, hem objA hem de objB bir değer türünün aynı örneğini temsil ediyorsa bile, <xref:System.Object.ReferenceEquals%2A> Yöntem false değerini döndürür. |
|[CA2014: Döngülerde stackalloc kullanmayın.](../code-quality/ca2014.md) | Bir stackalloc tarafından ayrılan yığın alanı yalnızca geçerli metodun çağrısının sonunda serbest bırakılır.  Bunu bir döngüde kullanmak, sınırsız yığın büyümesi ve nihai yığın taşması koşullarına yol açabilir. |
|[CA2015: MemoryManager T 'den türetilmiş türler için sonlandırıcılar tanımlama &lt;&gt;](../code-quality/ca2015.md) | ' Dan türetilmiş bir türe Sonlandırıcı eklemek <xref:System.Buffers.MemoryManager%601> , bir tarafından kullanılmaya devam edilirken belleğin serbest olmasına izin verebilir <xref:System.Span%601> . |
|[CA2016: CancellationToken parametresini, parametre alan metotlara iletin](ca2016.md) | `CancellationToken`İşlem iptal bildirimlerinin düzgün şekilde yayıldığından emin olmak için parametreyi bir tane alan yöntemlere iletin veya `CancellationToken.None` açıkça belirteci yaymadığınızı belirtmek için açıkça geçiş yapın. |
