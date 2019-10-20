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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 602f372e11c4a9a8506186535958fc4f22da7806
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649109"
---
# <a name="reliability-warnings"></a>Güvenilirlik uyarıları

Güvenilirlik uyarıları, doğru bellek ve iş parçacığı kullanımı gibi kitaplık ve uygulama güvenilirliğini destekler. Güvenilirlik kuralları şunları içerir:

|Kural|Açıklama|
|----------|-----------------|
|[CA2000: Kapsamı kaybetmeden önce verileri atın](../code-quality/ca2000.md)|Bir nesnenin sonlandırıcısının çalışmasını engelleyecek olağanüstü bir durum gerçekleşebileceği için, nesne ona olan tüm başvurular kapsam dışına çıkmadan açıkça atılmalıdır.|
|[CA2001: Sorunlu yöntemleri çağırmaktan kaçının](../code-quality/ca2001.md)|Bir üye olası tehlikeli ya da sorunlu yöntemi çağırır.|
|[CA2002: Zayıf kimliği olan nesneleri kilitlemeyin](../code-quality/ca2002.md)|Bir nesneye uygulama etki alanları arasından erişilebiliyorsa o nesnenin zayıf bir kimliğe sahip olduğu söylenir. Zayıf kimliğe sahip bir nesne üzerinde kilit almayı deneyen iş parçacığı aynı nesne üzerinde bir kilide sahip olan farklı uygulama etki alanı içindeki ikinci iş parçacığı tarafından engellenebilir.|
|[CA2003: Lifleri iş parçacığı olarak görmeyin](../code-quality/ca2003.md)|Yönetilen bir iş parçacığı Win32 iş parçacığı olarak kabul ediliyor.|
|[CA2004: GC.KeepAlive'a çağrıları kaldırın](../code-quality/ca2004.md)|SafeHandle kullanımına dönüştürüyorsanız, GC 'ye yapılan tüm çağrıları kaldırın. KeepAlive (nesne). Bu durumda, sınıfların GC çağrısı olması gerekmez. Canlı tutma, sonlandırıcılardan olmadığı varsayılarak ancak işletim sistemi tanıtıcısını sonuçlandırmak için SafeHandle 'ı kullanır.|
|[CA2006: Yerel kaynakları kapsamak için SafeHandle kullanın](../code-quality/ca2006.md)|Yönetilen kod içinde IntPtr kullanmak olası bir güvenlik ve güvenilirlik sorunu belirtebilir. IntPtr'nin tüm kullanımları onun yerine bir SafeHandle ya da benzer bir teknolojinin kullanımının gerekip gerekmediğini belirlemek için gözden geçirilmelidir.|
|[CA2007: bir görevi doğrudan bekleme](../code-quality/ca2007.md)|Zaman uyumsuz bir yöntem <xref:System.Threading.Tasks.Task> ' i doğrudan [bekler](/dotnet/csharp/language-reference/keywords/await) .|
