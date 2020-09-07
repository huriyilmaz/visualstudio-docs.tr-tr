---
title: Yönetilen Kod için Kod Analizi Uyarıları
ms.date: 08/31/2020
ms.topic: reference
f1_keywords:
- vc.project.vcfxcoptool.enablefxcop
helpviewer_keywords:
- managed code analyis, warnings
- warnings, managed code analysis
- managed code analysis warnings
- code analysis,managed code
ms.assetid: 3c2741ff-0d3a-42e6-acd5-d42310bd03c4
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 8238de0760f300b6fa418a5e3eb47eac3db77272
ms.sourcegitcommit: 5caad925ca0b5d136416144a279e984836d8f28c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2020
ms.locfileid: "89509022"
---
# <a name="net-code-analysis-rules"></a>.NET kod analizi kuralları
Yönetilen Kod Analizi Aracı, yönetilen kod kitaplıklarında kural ihlallerini belirten uyarılar sağlar. Uyarılar, tasarım, yerelleştirme, performans ve güvenlik gibi kural alanlarında düzenlenir. Her uyarı, yönetilen kod analizi kuralının ihlal edildiğini belirtir. Bu bölümde, her bir yönetilen kod analizi uyarısıyla ilgili ayrıntılı tartışmalar ve örnekler sağlanmaktadır.

 Aşağıdaki tabloda her uyarı için belirtilen bilgi türü gösterilmektedir.

|Öğe|Açıklama|
|----------|-----------------|
|Tür|Kural için TypeName.|
|CheckId|Kural için benzersiz tanımlayıcı. CheckId ve Category bir uyarının kaynak üzerinde gizlemesi için kullanılır.|
|Kategori|Uyarının kategorisi.|
|Son değişiklik|Kural ihlalinin düzeltilme düzeltmesinin önemli bir değişiklik olup olmadığı. Son değişiklik, ihlale neden olan hedefe bağımlılığı olan bir derlemenin yeni sabit sürümle yeniden derlenmeyeceği veya değişiklik nedeniyle çalışma zamanında başarısız olabileceği anlamına gelir. Birden çok düzeltme kullanılabilir olduğunda ve en az bir düzeltme, Son değişiklik olduğunda ve bir düzeltme yoksa, ' kırılmamış ' ve ' kırılmamış ' seçeneklerinin her ikisi de belirtilir.|
|Nedeni|Kuralın bir uyarı oluşturmasına neden olan özel yönetilen kod.|
|Açıklama|Uyarının arkasındaki sorunları açıklar.|
|İhlaller Nasıl Düzeltilir?|Kaynak kodun kuralı karşılamak için nasıl değiştirileceğini ve bir uyarı oluşturmasını engellemesini açıklar.|
|Uyarılar Bastırıldığında|Kuraldan bir uyarı bastırmasının ne kadar güvenli olduğunu açıklar.|
|Örnek kod|Kuralı ihlal eden örnekleri ve kuralı karşılayan örnekleri düzeltildi.|
|İlgili uyarılar|İlgili uyarılar.|

## <a name="in-this-section"></a>Bu Bölümde

|Kategori|Açıklama|
|-|-|
|[KIMLIĞE göre kurallar](../code-quality/code-analysis-warnings-for-managed-code-by-checkid.md)|RuleId tarafından tüm kuralları listeler|
|[Tasarım kuralları](../code-quality/design-warnings.md)|.NET tasarım yönergeleri tarafından belirtilen şekilde doğru kitaplık tasarımını destekleyen kurallar.|
|[Belge kuralları](../code-quality/documentation-warnings.md)|XML belgelerinin açıklamalarını doğru kullanarak iyi belgelenmiş kitaplık tasarımını destekleyen kurallar.|
|[Genelleştirme Kuralları](../code-quality/globalization-warnings.md)|Uluslararası kitaplıkları ve uygulamaları destekleyen kurallar.|
|[Bakım kuralları](../code-quality/maintainability-warnings.md)|Kitaplığı ve uygulama bakımını destekleyen kurallar.|
|[Adlandırma kuralları](../code-quality/naming-warnings.md)|.NET Tasarım Yönergelerinin adlandırma kurallarına uygunluğunu destekleyen kurallar.|
|[Performans Kuralları](../code-quality/performance-warnings.md)|Yüksek performanslı kitaplıkları ve uygulamaları destekleyen kurallar.|
|[Taşınabilirlik ve birlikte çalışabilirlik kuralları](../code-quality/interoperability-warnings.md)|Farklı platformlar genelinde taşınabilirliği ve COM istemcileriyle etkileşimi destekleyen kurallar.|
|[Kuralları Yayımla](../code-quality/publish-warnings.md)|.NET uygulamaları için uygun yayımlamayı destekleyen kurallar.|
|[Güvenilirlik kuralları](../code-quality/reliability-warnings.md)|Doğru bellek ve iş parçacığı kullanımı gibi kitaplık ve uygulama güvenilirliğini destekleyen kurallar.|
|[Güvenlik Kuralları](../code-quality/security-warnings.md)|Daha güvenli kitaplıkları ve uygulamaları destekleyen kurallar.|
|[Kullanım kuralları](../code-quality/usage-warnings.md)|.NET ' in uygun kullanımını destekleyen kurallar.|
