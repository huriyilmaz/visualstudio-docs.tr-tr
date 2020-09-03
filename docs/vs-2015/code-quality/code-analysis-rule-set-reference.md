---
title: Kod analizi kural kümesi başvurusu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
helpviewer_keywords:
- code analysis, rule sets
ms.assetid: 5874e854-e298-4d2e-bbe4-95e899d22587
caps.latest.revision: 45
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: e480869d5b13ecc051deaa97b0bfd2532519d18f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85535726"
---
# <a name="code-analysis-rule-set-reference"></a>Kod analizi kural kümesi başvurusu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

,, Veya içinde yönetilen kod projeleri için kod analizini [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] yapılandırdığınızda [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] , veya [!INCLUDE[vsPro](../includes/vspro-md.md)] yerleşik *kural kümelerinin*bir listesi sunulur. Standar kural kümelerinden birini kullanabilir ya da bir kural kümesini proje gereksinimlerinize uyacak şekilde özelleştirebilirsiniz.

## <a name="available-rule-sets"></a>Kullanılabilir kural kümeleri
 Aşağıdaki tabloda varsayılan kural kümeleri listelenmektedir:

|Öğe|Değer|
|-|-|
|[Tüm Kurallar kural kümesi](../code-quality/all-rules-rule-set.md)|Bu kural kümesi tüm kuralları içerir. Bu kural kümesini çalıştırmak, çok sayıda uyarı oluşmasına neden olabilir. Kodunuzdaki tüm sorunların kapsamlı bir görüntüsünü almak için bu kural kümesini kullanın. Bu, ne kadar çok odaklanmış kural kümelerinin projeleriniz için çalıştırmaya en uygun olduğuna karar vermenize yardımcı olabilir.|
|[Yönetilen kod için Temel Doğruluk Kuralları kural kümesi](../code-quality/basic-correctness-rules-rule-set-for-managed-code.md)|Bu kurallar, çerçeve API 'Leri kullanımında yapılan mantıksal hatalara ve yaygın hatalara odaklanmaktadır. Önerilen en düşük kurallara göre raporlanan uyarılar listesinde genişletmek için bu kural kümesini ekleyin.|
|[Yönetilen kod için Temel Tasarım Yönerge Kuralları kural kümesi](../code-quality/basic-design-guideline-rules-rule-set-for-managed-code.md)|Bu kurallar, kodunuzun anlaşılması ve kullanılması için en iyi uygulamaları zorlamaya odaklanmaktadır. Projeniz kitaplık kodu içeriyorsa veya kolayca sürdürülebilir kod için en iyi yöntemleri zorlamak istiyorsanız bu kural kümesini ekleyin.|
|[Yönetilen kod için Genişletilmiş Doğruluk Kuralları kural kümesi](../code-quality/extended-correctness-rules-rule-set-for-managed-code.md)|Bu kurallar, bildirilen mantık ve çerçeve kullanım hatalarının en üst düzeye çıkarmak için temel doğruluk kurallarına genişletilir. Ek vurgu, COM birlikte çalışma ve mobil uygulamalar gibi belirli senaryolara yerleştirilir. Bu senaryolardan biri projeniz için geçerliyse veya projenizde ek sorunlar bulmak için bu kural kümesini dahil etmeyi göz önünde bulundurun.|
|[Yönetilen kod için Genişletilmiş Tasarım Yönerge Kuralları kural kümesi](../code-quality/extended-design-guidelines-rules-rule-set-for-managed-code.md)|Bu kurallar, bildirilen kullanılabilirlik ve bakım sorunlarını en üst düzeye çıkarmak için temel tasarım kılavuz kuralları ' nı genişletir. Ek vurgu, adlandırma yönergelerine göre yerleştirilir. Projeniz kitaplık kodu içeriyorsa veya sürdürülebilir kod yazmak için en yüksek standartları zorlamak istiyorsanız bu kural kümesini dahil etmeyi göz önünde bulundurun.|
|[Yönetilen kod için Genelleştirme Kuralları kural kümesi](../code-quality/globalization-rules-rule-set-for-managed-code.md)|Bu kurallar, farklı dillerde, yerel ayarlarda ve kültürlerde kullanıldığında uygulamanızdaki verilerin düzgün görüntülenmesini engelleyen sorunlara odaklanmaktadır. Uygulamanız yerelleştirilmiş veya Genelleştirilmiş ise bu kural kümesini ekleyin.|
|[Yönetilen kod için Yönetilen Minimum Kurallar kural kümesi](../code-quality/managed-minimun-rules-rule-set-for-managed-code.md)|Bu kurallar, kodunuzda kod analizini en doğru olan en kritik sorunlara odaklanmaktadır.  Bu kurallar sayı olarak küçüktür ve yalnızca sınırlı Visual Studio sürümlerinde çalışmak üzere tasarlanmıştır.  Diğer Visual Studio sürümleriyle MinimumRecommendedRules. RuleSet kullanın.|
|[Yönetilen kod için Yönetilen Önerilen Kurallar kural kümesi](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md)|Bu kurallar, olası güvenlik delikleri, uygulama kilitlenmesi ve diğer önemli mantık ve tasarım hataları da dahil olmak üzere kodunuzdaki en kritik sorunlara odaklanmaktadır. Bu kural kümesini, projeleriniz için oluşturduğunuz herhangi bir özel kural kümesine dahil etmelisiniz.|
|[Karışık Minimum Kurallar kural kümesi](../code-quality/mixed-minimum-rules-rule-set.md)|Bu kurallar, olası güvenlik delikleri ve uygulama kilitlenmeleri dahil olmak üzere, ortak dil çalışma zamanını destekleyen C++ projelerinizde en kritik sorunlara odaklanmaktadır. Bu kural kümesini, ortak dil çalışma zamanını destekleyen C++ projeleriniz için oluşturduğunuz herhangi bir özel kural kümesine dahil etmeniz gerekir.|
|[Karışık Önerilen Kurallar kural kümesi](../code-quality/mixed-recommended-rules-rule-set.md)|Bu kurallar, olası güvenlik delikleri, uygulama kilitlenmesi ve diğer önemli mantık ve tasarım hataları da dahil olmak üzere, ortak dil çalışma zamanını destekleyen C++ projelerinizde en yaygın ve kritik sorunlara odaklanmaktadır. Bu kural kümesini, ortak dil çalışma zamanını destekleyen C++ projeleriniz için oluşturduğunuz herhangi bir özel kural kümesine dahil etmeniz gerekir.  Bu RuleSet, Visual Studio Professional sürümü ve üstü ile yapılandırılacak şekilde tasarlanmıştır.|
|[Yerel Minimum Kurallar kural kümesi](../code-quality/native-minimum-rules-rule-set.md)|Bu kurallar, olası güvenlik delikleri ve uygulama kilitlenmeleri dahil olmak üzere yerel kodunuzda en kritik sorunlara odaklanmaktadır. Bu kural kümesini yerel projeleriniz için oluşturduğunuz herhangi bir özel kural kümesine dahil etmelisiniz.|
|[Yerel Önerilen Kurallar kural kümesi](../code-quality/native-recommended-rules-rule-set.md)|Bu kurallar, olası güvenlik delikleri ve uygulama kilitlenmeleri dahil olmak üzere yerel kodunuzda en kritik ve yaygın sorunlara odaklanmaktadır.  Bu kural kümesini yerel projeleriniz için oluşturduğunuz herhangi bir özel kural kümesine dahil etmelisiniz.  Bu RuleSet, Visual Studio Professional Edition ve üzeri ile çalışacak şekilde tasarlanmıştır.|
|[Yönetilen kod için Güvenlik Kuralları kural kümesi](../code-quality/security-rules-rule-set-for-managed-code.md)|Bu kural kümesi tüm Microsoft güvenlik kurallarını içerir. Bildirilen olası güvenlik sorunlarının sayısını en üst düzeye çıkarmak için bu kural kümesini ekleyin.|
