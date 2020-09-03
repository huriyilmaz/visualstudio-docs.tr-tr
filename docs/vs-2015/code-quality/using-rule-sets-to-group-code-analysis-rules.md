---
title: Kod analizi kurallarını gruplandırmak için kural kümeleri kullanma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.rulesets.learnmore
helpviewer_keywords:
- code analysis, rule sets
ms.assetid: ed0f3a2a-1516-42e2-92de-b8986dc75d42
caps.latest.revision: 38
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 30bd2e53531d9abc7d27adba05c3b724c88d61c3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72603474"
---
# <a name="using-rule-sets-to-group-code-analysis-rules"></a>Kod Çözümleme Kurallarını Gruplandırmak için Kural Kümeleri Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

, Veya ' de Kod analizini yapılandırdığınızda, [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] [!INCLUDE[vsPro](../includes/vspro-md.md)] Microsoft yerleşik *kural kümeleri*listesinden seçim yapabilirsiniz. Kural kümesi, hedeflenen sorunları ve belirli koşulları belirleyen kod analizi kurallarının mantıksal bir gruplandırmasıdır. Örneğin, genel olarak kullanılabilir API 'Ler için kodu taramak üzere tasarlanan bir kural kümesi uygulayabilir veya yalnızca önerilen en düşük kuralları içeren bir kural kümesi uygulayabilirsiniz. Tüm kuralları içeren bir kural kümesi de uygulayabilirsiniz.

 Kural ekleyerek veya silerek ya da kuralları **hata listesi** penceresinde uyarı veya hata olarak görünecek şekilde değiştirerek bir kural kümesini özelleştirebilirsiniz. Özelleştirilmiş kural kümeleri, belirli bir geliştirme ortamınız gereksinimini karşılayamıyor. Bir kural kümesini özelleştirdiğinizde, kural kümesi sayfası, süreçte size yardımcı olacak arama ve filtreleme araçları sağlar.

## <a name="common-tasks"></a>Ortak Görevler

|Görev|İlgili İçerik|
|----------|---------------------|
|**Uygulamalı alıştırma:** Basit bir .NET Framework uygulamasındaki sorunları bulmak ve gidermek için özel bir kural kümesi belirtmek üzere kod çözümleme araçları 'nı kullanın.|-   [İzlenecek yol: özel bir kural kümesini yapılandırma ve kullanma](../code-quality/walkthrough-configuring-and-using-a-custom-rule-set.md)|
|**Bir proje için kod analizini yapılandırın:** Bir proje, Web sitesi veya çözüm için mevcut bir kural kümesi seçin.|-   [Nasıl yapılır: yönetilen kod projesi için kod analizini yapılandırma](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)<br />-   [Çalıştırılacak C++ kurallarını belirtmek için kural kümeleri kullanma](../code-quality/using-rule-sets-to-specify-the-cpp-rules-to-run.md)<br />-   [Nasıl yapılır: ASP.NET Web uygulaması için kod analizini yapılandırma](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md)<br />-   [Nasıl yapılır: bir çözümde birden çok proje için kural kümesi belirtme](../code-quality/how-to-specify-managed-code-rule-sets-for-multiple-projects-in-a-solution.md)|
|**Bir kural kümesini özelleştirme:** Projenize uygulanacak kuralları belirtin.|-   [Özel kural kümeleri oluşturma](../code-quality/creating-custom-code-analysis-rule-sets.md)|
|**Yerleşik kural kümelerini anlayın:** Yerleşik kural kümelerini oluşturan kod çözümleme kurallarını görüntüleyin.|-   [Kod analizi kural kümesi başvurusu](../code-quality/code-analysis-rule-set-reference.md)|
|**Kod analizini Team Foundation Server Ile tümleştirin:** [!INCLUDE[esprtfs](../includes/esprtfs-md.md)] iade ilkeleri, tüm kod iadelerinin ortak bir kod analizi standartları kümesini karşıladığından emin olmak için geliştirme ekiplerine olanak tanır.|-   [Nasıl yapılır: takım projesi Iade Ilkesiyle kod proje kural kümelerini senkronize etme](../code-quality/how-to-synchronize-code-project-rule-sets-with-team-project-check-in-policy.md)|
