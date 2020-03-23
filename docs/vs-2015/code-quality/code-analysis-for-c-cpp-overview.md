---
title: C-C++ Genel Bakış için Kod Analizi | Microsoft Dokümanlar
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: overview
helpviewer_keywords:
- annotations, code analysis
- build integration, code analysis
- C/C++ code analysis
- IDE, code analysis
- pragma directive, code analysis
- code analysis, C/C++
- code analysis tool
- command line, code analysis
- C++, code analysis
- check-in policies, code analysis
- '#pragma directives, code analysis'
- C, code analysis
ms.assetid: 81f0c9e8-f471-4de5-aac4-99db336a8809
caps.latest.revision: 27
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: 1ce41cd1c0dabc94658b83aa5e2bcdc08d005fdb
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "77275362"
---
# <a name="code-analysis-for-cc-overview"></a>C/C++ İçin Kod Analizine Genel Bakış
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

C/C++ Kod Analizi aracı, geliştiricilere C/C++ kaynak kodlarındaki olası kusurlar hakkında bilgi sağlar. Araç tarafından bildirilen yaygın kodlama hataları arabellek taşmaları, un-initialized bellek, null işaretçi dereferences ve bellek ve kaynak sızıntıları içerir.  
  
## <a name="ide-integrated-development-environment-integration"></a>IDE (entegre geliştirme ortamı) Entegrasyonu  
 Geliştiricilerin analiz aracını kullanmasını doğal hale getirmek için, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE'ye tamamen entegre edilmiştir. Oluşturma işlemi sırasında, kaynak kodu için oluşturulan tüm uyarılar Hata Listesi'nde görünür. Uyarıya neden olan kaynak koduna gidebilir ve sorunun nedeni ve olası çözümleri hakkında ek bilgileri görüntüleyebilirsiniz.  
  
## <a name="pragma-support"></a>#pragma Desteği  
 Geliştiriciler uyarıları `#pragma` hata olarak ele almak için yönergeyi kullanabilir; uyarıları etkinleştirin veya devre dışı edin ve tek tek kod satırları için uyarıları bastırın. Daha fazla bilgi için [bkz: Belirli C/C++ Uyarıları için Kod Çözümlemesi etkinleştirme ve devre dışı.](https://msdn.microsoft.com/910b8518-71f1-4b2e-b012-70647795642a)  
  
## <a name="annotation-support"></a>Ek Açıklama Desteği  
 Ek açıklamalar kod çözümlemesi doğruluğunu artırır. Ek açıklamalar, işlev parametreleri ve iade türleri hakkında ön ve sonrası koşullar hakkında ek bilgiler sağlar. Daha fazla bilgi için [bkz: __analysis_assume kullanarak Ek Kod Bilgilerini Belirtin](../code-quality/how-to-specify-additional-code-information-by-using-analysis-assume.md)  
  
## <a name="run-analysis-tool-as-part-of-check-in-policy"></a>İade ilkesinin bir parçası olarak analiz aracını çalıştırma  
 Tüm kaynak kodu iadelerinin belirli ilkeleri karşıladığını isteyebilirsiniz. Özellikle, bu çözümlemenin en son yerel yapının bir adımı olarak çalıştırıldığınızdan emin olmak istersiniz. Kod analizi iade ilkesini etkinleştirme hakkında daha fazla bilgi için kod [analizi denetim ilkeleri oluşturma ve kullanma](../code-quality/creating-and-using-code-analysis-check-in-policies.md)  
  
## <a name="team-build-integration"></a>Takım Oluşturma Tümleştirmesi  
 Yapı işleminin bir adımı [!INCLUDE[esprtfs](../includes/esprtfs-md.md)] olarak kod çözümleme aracını çalıştırmak için yapı sisteminin tümleşik özelliklerini kullanabilirsiniz. Daha fazla bilgi için [bkz.](/azure/devops/pipelines/index)  
  
## <a name="command-line-support"></a>Komut satırı desteği  
 Geliştirme ortamındaki tam tümleştirmeye ek olarak, geliştiriciler aşağıdaki örnekte gösterildiği gibi komut satırındaki çözümleme aracını da kullanabilirler:  
  
 `C:\>cl /analyze Sample.cpp`
