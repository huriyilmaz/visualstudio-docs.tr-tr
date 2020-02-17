---
title: 'Nasıl yapılır: CC++ projeleri Için kod analizi özelliklerini ayarlama | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
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
caps.latest.revision: 19
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: b2fb3cb81b49fd4b8cc83e0548110d2025c7488d
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/15/2020
ms.locfileid: "77277992"
---
# <a name="how-to-set-code-analysis-properties-for-cc-projects"></a>Nasıl yapılır: C/C++ Projeleri için Kod Analizi Özelliklerini Ayarlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kod Analizi aracının, projenizin her yapılandırmasındaki kodu çözümlemek için hangi kuralları kullanacağını yapılandırabilirsiniz. Ayrıca, bir üçüncü taraf aracı tarafından oluşturulan ve projenize eklenen koddan uyarıları bastırmak için kod analizini yönlendirebilirsiniz.  
  
## <a name="code-analysis-property-page"></a>Kod Analizi Özellik sayfası  
 **Kod Analizi** Özellik sayfası, bir proje için tüm kod analizi yapılandırma ayarlarını içerir. **Çözüm Gezgini**bir projenin kod analizi özellik sayfasını açmak için projeye sağ tıklayın ve ardından **Özellikler**' e tıklayın. Sonra, **yapılandırma özellikleri** ' ni genişletin ve **Kod Analizi** sekmesini seçin.  
  
## <a name="project-configuration-and-platform"></a>Proje yapılandırması ve platformu  
 **Yapılandırma** listesi ve **Platform** listesi farklı proje yapılandırmasına ve platform birleşimlerine farklı kod çözümleme ayarları uygulamanıza olanak tanır. Örneğin, hata ayıklama derlemeleri ve yayın yapıları için farklı bir küme için projenize bir kural kümesi uygulamak üzere Kod analizini yönlendirebilirsiniz.  
  
## <a name="enabling-code-analysis"></a>Kod analizini etkinleştirme  
 **Derleme Için kod analizini EtkinleştirC++ '** i seçerek projeniz için kod analizini etkinleştirmek isteyip istemediğinize karar verebilirsiniz. **Yapılandırma** listesiyle birlikte, örneğin hata ayıklama derlemeleri Için kod analizini devre dışı bırakmaya karar verebilir ve bunu yayın yapıları için etkinleştirebilirsiniz.  
  
 Projeniz yönetilen kod içeriyorsa, **derlemede Kod analizini etkinleştir**' i seçerek Kod analizini etkinleştirip etkinleştirmemeye veya devre dışı bırakılacağını belirleyebilirsiniz.  
  
 Kod Analizi, kodunuzun kalitesini iyileştirebilmeniz ve genel kullanım tehliklerini önlemenize yardımcı olmak için tasarlanmıştır. Bu nedenle, kod analizinin devre dışı bırakılıp başlatılmayacağını dikkatle düşünün. Projenize uygulanmasını istemediğiniz kural kümelerini veya tek tek kuralları devre dışı bırakmak genellikle daha iyidir.  
  
## <a name="generated-code"></a>Oluşturulan kod  
 Geliştiriciler hızlı bir şekilde uygulama geliştirmeye yardımcı olan araçları kullanır. Bu araçlar projeye eklenen kodu oluşturabilir. Kod analizinin üretilen kodda bulduğu kural ihlallerini görmek isteyebilirsiniz. Ancak, kodu sürdürmek istemiyorsanız bunları görmek istemeyebilirsiniz.  
  
 **Genel** Özellikler sayfasındaki **oluşturulan koddan sonuçları gösterme** onay kutusu, üçüncü taraf bir araç tarafından oluşturulan yönetilen koddan kod analizi uyarılarını görmek isteyip istemediğinizi seçmenizi sağlar.  
  
## <a name="rule-sets"></a>Kural Kümeleri  
 Projeniz yönetilen kod içeriyorsa, **Bu kural kümesini Çalıştır** listesinden bir kural kümesi seçerek kod analizinde uygulanacak kuralları seçebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yönetilen kod kalitesi  çözümleniyor](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)  
 [C/C++ İçin Kod Analizi Uyarıları](../code-quality/code-analysis-for-c-cpp-warnings.md)
