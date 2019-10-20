---
title: Yönetilen Kod için Kod Analizi Uyarıları
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vc.project.vcfxcoptool.enablefxcop
helpviewer_keywords:
- managed code analyis, warnings
- warnings, managed code analysis
- managed code analysis warnings
- code analysis,managed code
ms.assetid: 3c2741ff-0d3a-42e6-acd5-d42310bd03c4
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 8fbc5bbb596cc7b790ea456b22a24b582e1b609a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72622458"
---
# <a name="code-analysis-for-managed-code-warnings"></a>Yönetilen Kod için Kod Analizi Uyarıları
Yönetilen Kod Analizi Aracı, yönetilen kod kitaplıklarında kural ihlallerini belirten uyarılar sağlar. Uyarılar, tasarım, yerelleştirme, performans ve güvenlik gibi kural alanlarında düzenlenir. Her uyarı, yönetilen kod analizi kuralının ihlal edildiğini belirtir. Bu bölümde, her bir yönetilen kod analizi uyarısıyla ilgili ayrıntılı tartışmalar ve örnekler sağlanmaktadır.

 Aşağıdaki tabloda her uyarı için belirtilen bilgi türü gösterilmektedir.

|Öğe|Açıklama|
|----------|-----------------|
|Tür|Kural için TypeName.|
|CheckId|Kural için benzersiz tanımlayıcı. CheckId ve Category bir uyarının kaynak üzerinde gizlemesi için kullanılır.|
|Kategori|Uyarının kategorisi.|
|Son değişiklik|Kural ihlalinin düzeltilme düzeltmesinin önemli bir değişiklik olup olmadığı. Son değişiklik, ihlale neden olan hedefe bağımlılığı olan bir derlemenin yeni sabit sürümle yeniden derlenmeyeceği veya değişiklik nedeniyle çalışma zamanında başarısız olabileceği anlamına gelir. Birden çok düzeltme kullanılabilir olduğunda ve en az bir düzeltme, Son değişiklik olduğunda ve bir düzeltme yoksa, ' kırılmamış ' ve ' kırılmamış ' seçeneklerinin her ikisi de belirtilir.|
|Sebep|Kuralın bir uyarı oluşturmasına neden olan özel yönetilen kod.|
|Açıklama|Uyarının arkasındaki sorunları açıklar.|
|İhlaller Nasıl Düzeltilir?|Kaynak kodun kuralı karşılamak için nasıl değiştirileceğini ve bir uyarı oluşturmasını engellemesini açıklar.|
|Uyarılar Bastırıldığında|Kuraldan bir uyarı bastırmasının ne kadar güvenli olduğunu açıklar.|
|Örnek kod|Kuralı ihlal eden örnekleri ve kuralı karşılayan örnekleri düzeltildi.|
|İlgili uyarılar|İlgili uyarılar.|

## <a name="in-this-section"></a>Bu Bölümde

|||
|-|-|
|[CheckId Uyarıları](../code-quality/code-analysis-warnings-for-managed-code-by-checkid.md)|Tüm uyarıları CheckId 'ye göre listeler|
|[Şifreleme Uyarıları](../code-quality/cryptography-warnings.md)|Şifrelemeyi doğru şekilde kullanarak daha güvenli kitaplıkları ve uygulamaları destekleyen uyarılar.|
|[Tasarım Uyarıları](../code-quality/design-warnings.md)|.NET tasarım yönergeleri tarafından belirtilen şekilde doğru kitaplık tasarımını destekleyen uyarılar.|
|[Belge Uyarıları](../code-quality/documentation-warnings.md)|XML belgelerinin açıklamalarını doğru kullanarak iyi belgelenmiş kitaplık tasarımını destekleyen uyarılar.|
|[Genelleştirme Uyarıları](../code-quality/globalization-warnings.md)|Uluslararası kitaplıkları ve uygulamaları destekleyen uyarılar.|
|[Birlikte Çalışabilirlik Uyarıları](../code-quality/interoperability-warnings.md)|COM istemcileriyle etkileşimi destekleyen uyarılar.|
|[Bakım Uyarıları](../code-quality/maintainability-warnings.md)|Kitaplığı ve uygulama bakımını destekleyen uyarılar.|
|[Hareketlilik Uyarıları](../code-quality/mobility-warnings.md)|Verimli güç kullanımını destekleyen uyarılar.|
|[Adlandırma Uyarıları](../code-quality/naming-warnings.md)|.NET Tasarım Yönergelerinin adlandırma kurallarına uygunluğunu destekleyen uyarılar.|
|[Performans Uyarıları](../code-quality/performance-warnings.md)|Yüksek performanslı kitaplıkları ve uygulamaları destekleyen uyarılar.|
|[Taşınabilirlik Uyarıları](../code-quality/portability-warnings.md)|Farklı platformlarda taşınabilirliği destekleyen uyarılar.|
|[Güvenilirlik Uyarıları](../code-quality/reliability-warnings.md)|Doğru bellek ve iş parçacığı kullanımı gibi kitaplık ve uygulama güvenilirliğini destekleyen uyarılar.|
|[Güvenlik Uyarıları](../code-quality/security-warnings.md)|Daha güvenli kitaplıkları ve uygulamaları destekleyen uyarılar.|
|[Kullanım Uyarıları](../code-quality/usage-warnings.md)|.NET ' in uygun kullanımını destekleyen uyarılar.|
|[Kod Çözümleme İlkesi Hataları](../code-quality/code-analysis-policy-errors.md)|Kod Analizi ilkesi iadede karşılanmıyorsa oluşan hatalar.|
