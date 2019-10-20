---
title: Kod Analizi Iade Ilkeleri oluşturma ve kullanma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, check-in policies
ms.assetid: 3fa5a849-e05f-4e31-8ba3-b014c889d94d
caps.latest.revision: 41
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 8e31ff799edc93d250eeeab57b349873a63ecf14
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667709"
---
# <a name="creating-and-using-code-analysis-check-in-policies"></a>Kod Analizi İade İlkeleri Oluşturma ve Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Team Foundation Sürüm Denetimi (TFVC) kullandığınızda, bir takım projesindeki .NET Framework ve yerel (C/C++) kod projeleri için bir kod analizi iade ilkesi oluşturabilirsiniz. Kod tabanında işaretlenen kodun kalitesini denetlemek ve geliştirmek için kod analizi iade etme ilkesini kullanabilirsiniz.

 İlke, yerel derleme güncel olduğunda geçirilir ve en son kaynak dosyalarında kod analizi çalıştırılır. En azından, kod projesinde etkinleştirilen kod analizi kurallarının, takım projesi iade ilkesinde tanımlananlarla aynı kuralları içermesi gerekir. Takım projesi ayarlarında hata olarak belirtilen kuralların de kod projesinde hata olarak belirtilmesi gerekir

> [!IMPORTANT]
> Kod Analizi iade ilkeleri Web sitesi projelerine uygulanamaz. Web uygulaması projelerine uygulanabilirler.

 @No__t_0 takım projesi ayarlarını kullanarak kod analizi iade ilkeleri oluşturursunuz. İade ilkeleri bir takım projesi için belirlenir ve zorlanır, ancak kod analizi çalıştırmaları yerel geliştirme bilgisayarlarındaki bireysel kod projeleri için yapılandırılır ve çalıştırılır. Bu bölümde, bir takım projesi için kod analizi iade ilkelerinin nasıl belirtileceğini ve yönetilen kod için özel kod çözümleme ilkelerinin nasıl uygulanacağı açıklanmaktadır.

## <a name="in-this-section"></a>Bu Bölümde
 [Nasıl yapılır: standart kod analizi Iade Ilkeleri oluşturma veya güncelleştirme](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md) Bir takım projesi için kod analizi ilkesini ayarlamak ve değiştirmek için kullandığınız adımları açıklar.

 [Yönetilen kod Için özel Iade Ilkelerini uygulama](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md) Bir ekip projesinin iade ilkesi için özel bir kural kümesi oluşturmak ve takım projesinin kod projelerini iade ilkesiyle senkronize etmek için kullandığınız adımları açıklar.

 [Kod çözümleme Iade ilkeleri Için sürüm uyumluluğu](../code-quality/version-compatibility-for-code-analysis-check-in-policies.md) @No__t_1 sürümleri arasındaki kod analizi iade etme uyumluluk sorunlarını açıklar.

 [Nasıl yapılır: kod analizi sözlüğünü özelleştirme](../code-quality/how-to-customize-the-code-analysis-dictionary.md) Kod Analizi adlandırma kurallarında başvurulan sözlüğe sözcüklerin ve belirteçlerin nasıl ekleneceğini açıklar.

## <a name="related-sections"></a>İlgili Bölümler
 [Kalite kapıları ayarlama ve zorlama](https://msdn.microsoft.com/library/bdc5666e-6cf0-45b2-a0a1-133c3f61e852)

 [Takım Projesi İade İlkeleriyle Kod Kalitesini Arttırma](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)
