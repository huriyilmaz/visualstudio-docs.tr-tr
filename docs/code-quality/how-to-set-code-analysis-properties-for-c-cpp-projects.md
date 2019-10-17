---
title: 'Nasıl yapılır: C/C++ Projeleri için Kod Analizi Özelliklerini Ayarlama'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.native
- VC.Project.VCCLCompilerTool.EnablePrefast
- VC.Project.VCFxCopTool.EnablePREfast
- VC.Project.VCFxCopTool.IgnoreGeneratedCode
helpviewer_keywords:
- properties, C/C++ Code Analysis
- properties, Code Analysis
- code analysis properties
- C/C++ code analysis properties
ms.assetid: 7af52097-6d44-4785-9b9f-43b7a7d447d7
author: mikeblome
ms.author: mblome
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 27f3d68d28b8d1799c52fcf83c6a00dc5f81f48a
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72448910"
---
# <a name="how-to-set-code-analysis-properties-for-cc-projects"></a>Nasıl yapılır: C/C++ Projeleri için Kod Analizi Özelliklerini Ayarlama

Kod Analizi aracının, projenizin her yapılandırmasındaki kodu çözümlemek için hangi kuralları kullanacağını yapılandırabilirsiniz. Ayrıca, bir üçüncü taraf aracı tarafından oluşturulan ve projenize eklenen koddan uyarıları bastırmak için kod analizini yönlendirebilirsiniz.

## <a name="code-analysis-property-page"></a>Kod Analizi Özellik sayfası

**Kod Analizi** Özellik sayfası, bir MSBuild projesi için tüm kod analizi yapılandırma ayarlarını içerir. **Çözüm Gezgini**bir projenin kod analizi özellik sayfasını açmak için projeye sağ tıklayın ve ardından **Özellikler**' e tıklayın. Sonra, **yapılandırma özellikleri** ' ni genişletin ve **Kod Analizi** sekmesini seçin.

## <a name="project-configuration-and-platform"></a>Proje yapılandırması ve platformu

Pencerenin üst kısmındaki **yapılandırma** listesi ve **Platform** listesi farklı proje yapılandırmasına ve platform birleşimlerine farklı kod çözümleme ayarları uygulamanıza olanak tanır. Örneğin, hata ayıklama derlemeleri ve yayın yapıları için farklı bir küme için projenize bir kural kümesi uygulamak üzere Kod analizini yönlendirebilirsiniz.

## <a name="enabling-code-analysis"></a>Kod analizini etkinleştirme

**Microsoft Kod analizini etkinleştir** ve **Clang-Tidy seçeneklerini etkinleştirerek** ve derlemede **Kod analizini etkinleştir**' i seçerek daha fazla yapılandırma yaparak projeniz için kod analizini etkinleştirebilirsiniz. **Yapılandırma** listesiyle birlikte, örneğin hata ayıklama derlemeleri Için kod analizini devre dışı bırakmaya karar verebilir ve bunu yayın yapıları için etkinleştirebilirsiniz.

Kod Analizi, kodunuzun kalitesini iyileştirebilmeniz ve genel kullanım tehliklerini önlemenize yardımcı olmak için tasarlanmıştır. Bu nedenle, kod analizinin devre dışı bırakılıp başlatılmayacağını dikkatle düşünün. Projenize uygulanmasını istemediğiniz kural kümelerini, bireysel kuralları veya bireysel denetimleri devre dışı bırakmak genellikle daha iyidir.

## <a name="cmake-configuration"></a>CMake yapılandırması

CMake projelerinde, Kod analizini etkinleştirmek veya devre dışı bırakmak için `enableMicrosoftCodeAnalysis` ve `enableClangTidyCodeAnalysis` anahtarlarının değerini `CMakeSettings.json` içinde değiştirin. Daha fazla bilgi için bkz. [Visual Studio 'Da Clang-Tidy kullanma](../code-quality/clang-tidy.md) .

## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilen Kod Kalitesini Analiz Etme](../code-quality/code-analysis-for-managed-code-overview.md)
- [C/C++ İçin Kod Analizi Uyarıları](../code-quality/code-analysis-for-c-cpp-warnings.md)
- [Kod için C++ kural kümeleri](../code-quality/using-rule-sets-to-specify-the-cpp-rules-to-run.md)
- [Clang-Tidy kullanma](../code-quality/clang-tidy.md)
