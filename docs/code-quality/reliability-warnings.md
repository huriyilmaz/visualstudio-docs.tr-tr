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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cb39bb5f59373f52d77c7cc5d13d12544d4c0314
ms.sourcegitcommit: 3e94d9fb6dc56fa8b23fbacd5d11cf8d6e7e18f1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/10/2019
ms.locfileid: "72252593"
---
# <a name="reliability-warnings"></a>Güvenilirlik uyarıları

Güvenilirlik uyarıları, doğru bellek ve iş parçacığı kullanımı gibi kitaplık ve uygulama güvenilirliğini destekler. Güvenilirlik kuralları şunları içerir:

|Kural|Açıklama|
|----------|-----------------|
|[CA2000: Kapsamı kaybetmeden önce nesneleri Dispose @ no__t-0|Bir nesnenin sonlandırıcısının çalışmasını engelleyecek olağanüstü bir durum gerçekleşebileceği için, nesne ona olan tüm başvurular kapsam dışına çıkmadan açıkça atılmalıdır.|
|[CA2001: Sorunlu yöntemleri çağırmaktan kaçının @ no__t-0|Bir üye olası tehlikeli ya da sorunlu yöntemi çağırır.|
|[CA2002: Zayıf kimliğe sahip nesnelerde kilitleme @ no__t-0|Bir nesneye uygulama etki alanları arasından erişilebiliyorsa o nesnenin zayıf bir kimliğe sahip olduğu söylenir. Zayıf kimliğe sahip bir nesne üzerinde kilit almayı deneyen iş parçacığı aynı nesne üzerinde bir kilide sahip olan farklı uygulama etki alanı içindeki ikinci iş parçacığı tarafından engellenebilir.|
|[CA2003: Lifleri görmeyin iş parçacığı olarak davranmayın @ no__t-0|Yönetilen bir iş parçacığı Win32 iş parçacığı olarak kabul ediliyor.|
|[CA2004: GC çağrılarını kaldırın. KeepAlive @ no__t-0|SafeHandle kullanımına dönüştürüyorsanız, GC 'ye yapılan tüm çağrıları kaldırın. KeepAlive (nesne). Bu durumda, sınıfların GC çağrısı olması gerekmez. Canlı tutma, sonlandırıcılardan olmadığı varsayılarak ancak işletim sistemi tanıtıcısını sonuçlandırmak için SafeHandle 'ı kullanır.|
|[CA2006: Yerel kaynakları kapsüllemek için SafeHandle kullanın @ no__t-0|Yönetilen kod içinde IntPtr kullanmak olası bir güvenlik ve güvenilirlik sorunu belirtebilir. IntPtr'nin tüm kullanımları onun yerine bir SafeHandle ya da benzer bir teknolojinin kullanımının gerekip gerekmediğini belirlemek için gözden geçirilmelidir.|
|[CA2007: Doğrudan bir görevi beklemeyin @ no__t-0|Zaman uyumsuz bir yöntem <xref:System.Threading.Tasks.Task> ' i doğrudan [bekler](/dotnet/csharp/language-reference/keywords/await) .|
