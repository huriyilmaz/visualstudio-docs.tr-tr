---
title: Kod analizi kural kümesi başvurusu
ms.date: 04/04/2018
description: Eski kod analizinde yerleşik kural kümeleri Visual Studio öğrenin. Kural kümelerini kaynaklara bakın. Özelleştirilmiş kural kümelerini kullanarak bu kümeleri nasıl kullanabileceğinizi bulun.
ms.custom: SEO-VS-2020
ms.topic: reference
helpviewer_keywords:
- code analysis, rule sets reference
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-code-analysis
ms.workload:
- multiple
ms.openlocfilehash: c6f23dcc5646d4516f9e00e50f8bf742b94502a2
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631827"
---
# <a name="code-analysis-rule-set-reference"></a>Kod analizi kural kümesi başvurusu

Visual Studio'da yönetilen kod projeleri için eski analizi yapılandırarak yerleşik kural kümeleri listesinden *birini seçebilirsiniz.* Bazı kurallar yerleşik kural kümelerinden birden fazlasine dahil edilir; örneğin, Temel Doğruluk Kuralları kural kümesi Yönetilen Önerilen Kurallar kural kümesinde yer alan kuralları içerir.

> [!NOTE]
> Bu bölümdeki kural kümeleri eski analizle ilgili. Kod çözümleyicisi paketleri için kullanılabilen kural kümeleri hakkında bilgi için [bkz. Kod çözümleyicileri ile kural kümeleri kullanma.](/dotnet/fundamentals/code-analysis/code-quality-rule-options)

Bu yerleşik kural kümelerinden birini kullanabilir veya bir kural setini proje [gereksinimlerinize](../code-quality/how-to-create-a-custom-rule-set.md) uyacak şekilde özelleştirebilirsiniz. Özel kural kümesine aynı kuralı içeren birden çok kural kümesi dahil ettiysanız, bu kural özel kural kümesinde yalnızca bir kez görünür.

Bu bölümdeki konular yerleşik kural kümelerini ve içerecekleri kuralları (veya uyarıları) açıklar.

| Kural kümesi | Dahil edilen kurallar |
| - | - |
| [Tüm Kurallar](all-rules-rule-set.md) | Kullanılabilir tüm yönetilen ve C++ kurallarını içerir |
| [Temel Doğruluk Kuralları](basic-correctness-rules-rule-set-for-managed-code.md) | Mantıksal hatalar ve çerçeve kullanımı için Yönetilen Önerilen Kurallara ek kurallar içerir |
| [Genişletilmiş Doğruluk Kuralları](extended-correctness-rules-rule-set-for-managed-code.md) | Temel Doğruluk Kurallarını (Yönetilen Önerilen Kuralları içerir) ve mantık hataları ve çerçeve kullanımı için daha fazla kural içerir |
| [Temel Tasarım Kılavuzu Kuralları](basic-design-guideline-rules-rule-set-for-managed-code.md) | Kodun okunma, anlama ve bakımının kolay olmasını sağlamak için Yönetilen Önerilen Kurallara ek kurallar içerir |
| [Genişletilmiş Tasarım Kılavuzu Kuralları](extended-design-guidelines-rules-rule-set-for-managed-code.md) | Temel Tasarım Kılavuz Kuralları (Yönetilen Önerilen Kuralları içerir) ve adlandırmaya odaklanan daha fazla bakım kuralı içerir |
| [Genelleştirme Kuralları](globalization-rules-rule-set-for-managed-code.md) | Genelleştirme sorunları için kurallar içerir |
| [Yönetilen Minimum Kurallar](managed-minimum-rules-rule-set-for-managed-code.md) | Kritik yönetilen kod sorunları için dört kural içerir |
| [Yönetilen Önerilen Kurallar](managed-recommended-rules-rule-set-for-managed-code.md) | Yönetilen Minimum Kuralları ve kritik yönetilen kod sorunları için daha fazla kural içerir |
| [Karışık Minimum Kurallar](mixed-minimum-rules-rule-set.md) | CLR için C++ kodundaki kritik sorunlara ait kuralları içerir |
| [Karışık Önerilen Kurallar](mixed-recommended-rules-rule-set.md) | CLR için C++ kodunda karışık minimum kurallara ek olarak kritik sorunlar için daha fazla kural içerir |
| [Yerel Minimum Kurallar](native-minimum-rules-rule-set.md) | Yerel kodda kritik sorunlar için kurallar içerir |
| [Yerel Önerilen Kurallar](native-recommended-rules-rule-set.md) | Yerel Minimum Kuralların yanı sıra yerel kodda kritik sorunlar için daha fazla kural içerir |
| [Güvenlik Kuralları](security-rules-rule-set-for-managed-code.md) | Güvenlik açıklarını bulmaya yönelik kurallar içerir |