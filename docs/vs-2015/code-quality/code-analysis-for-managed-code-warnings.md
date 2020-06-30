---
title: Yönetilen kod uyarıları için kod analizi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vc.project.vcfxcoptool.enablefxcop
helpviewer_keywords:
- managed code analyis, warnings
- warnings, managed code analysis
- managed code analysis warnings
- code analysis,managed code
ms.assetid: 3c2741ff-0d3a-42e6-acd5-d42310bd03c4
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 5294840e4669f28f4e8a04978274ad130d1397ee
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85535739"
---
# <a name="code-analysis-for-managed-code-warnings"></a>Yönetilen Kod için Kod Analizi Uyarıları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Yönetilen Kod Analizi Aracı, yönetilen kod kitaplıklarında kural ihlallerini belirten uyarılar sağlar. Uyarılar, tasarım, yerelleştirme, performans ve güvenlik gibi kural alanlarında düzenlenir. Her uyarı, yönetilen kod analizi kuralının ihlal edildiğini belirtir. Bu bölümde, her bir yönetilen kod analizi uyarısıyla ilgili ayrıntılı tartışmalar ve örnekler sağlanmaktadır.

 Aşağıdaki tabloda her uyarı için belirtilen bilgi türü gösterilmektedir.

|Öğe|Description|
|----------|-----------------|
|Tür|Kural için TypeName.|
|CheckId|Kural için benzersiz tanımlayıcı. CheckId ve Category bir uyarının kaynak üzerinde gizlemesi için kullanılır.|
|Kategori|Uyarının kategorisi.|
|Yeni Değişiklik|Kural ihlalinin düzeltilme düzeltmesinin önemli bir değişiklik olup olmadığı. Son değişiklik, ihlale neden olan hedefe bağımlılığı olan bir derlemenin yeni sabit sürümle yeniden derlenmeyeceği veya değişiklik nedeniyle çalışma zamanında başarısız olabileceği anlamına gelir. Birden çok düzeltme kullanılabilir olduğunda ve en az bir düzeltme, Son değişiklik olduğunda ve bir düzeltme yoksa, ' kırılmamış ' ve ' kırılmamış ' seçeneklerinin her ikisi de belirtilir.|
|Nedeni|Kuralın bir uyarı oluşturmasına neden olan özel yönetilen kod.|
|Description|Uyarının arkasındaki sorunları açıklar.|
|İhlaller Nasıl Düzeltilir?|Kaynak kodun kuralı karşılamak için nasıl değiştirileceğini ve bir uyarı oluşturmasını engellemesini açıklar.|
|Uyarılar Bastırıldığında|Kuraldan bir uyarı bastırmasının ne kadar güvenli olduğunu açıklar.|
|Örnek kod|Kuralı ihlal eden örnekleri ve kuralı karşılayan örnekleri düzeltildi.|
|İlgili uyarılar|İlgili uyarılar.|

## <a name="in-this-section"></a>Bu Bölümde

|Öğe|Değer|
|-|-|
|[CheckId 'ye göre uyarılar](../code-quality/code-analysis-warnings-for-managed-code-by-checkid.md)|Tüm uyarıları CheckId 'ye göre listeler|
|[Şifreleme uyarıları](../code-quality/cryptography-warnings.md)|Şifrelemeyi doğru şekilde kullanarak daha güvenli kitaplıkları ve uygulamaları destekleyen uyarılar.|
|[Tasarım uyarıları](../code-quality/design-warnings.md)|Tasarım yönergeleriyle belirtilen şekilde doğru kitaplık tasarımını destekleyen uyarılar [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] .|
|[Genelleştirme Uyarıları](../code-quality/globalization-warnings.md)|Uluslararası kitaplıkları ve uygulamaları destekleyen uyarılar.|
|[Birlikte çalışabilirlik uyarıları](../code-quality/interoperability-warnings.md)|COM istemcileriyle etkileşimi destekleyen uyarılar.|
|[Bakımsız uyarılar](../code-quality/maintainability-warnings.md)|Kitaplığı ve uygulama bakımını destekleyen uyarılar.|
|[Mobility uyarıları](../code-quality/mobility-warnings.md)|Verimli güç kullanımını destekleyen uyarılar.|
|[Adlandırma uyarıları](../code-quality/naming-warnings.md)|Tasarım Yönergelerinin adlandırma kurallarına uygunluğunu destekleyen uyarılar [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] .|
|[Performans uyarıları](../code-quality/performance-warnings.md)|Yüksek performanslı kitaplıkları ve uygulamaları destekleyen uyarılar.|
|[Taşınabilirlik uyarıları](../code-quality/portability-warnings.md)|Farklı platformlarda taşınabilirliği destekleyen uyarılar.|
|[Güvenilirlik uyarıları](../code-quality/reliability-warnings.md)|Doğru bellek ve iş parçacığı kullanımı gibi kitaplık ve uygulama güvenilirliğini destekleyen uyarılar.|
|[Güvenlik uyarıları](../code-quality/security-warnings.md)|Daha güvenli kitaplıkları ve uygulamaları destekleyen uyarılar.|
|[Kullanım uyarıları](../code-quality/usage-warnings.md)|Uygulamasının uygun kullanımını destekleyen uyarılar [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] .|
|[Kod Analiz İlkesi Hataları](../code-quality/code-analysis-policy-errors.md)|Kod Analizi ilkesi iadede karşılanmıyorsa oluşan hatalar.|
