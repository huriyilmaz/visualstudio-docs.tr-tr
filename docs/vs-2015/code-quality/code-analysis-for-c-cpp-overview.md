---
title: C-C + + genel bakış için kod analizi | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77275362"
---
# <a name="code-analysis-for-cc-overview"></a>C/C++ İçin Kod Analizine Genel Bakış
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

C/C++ Kod Analizi Aracı, geliştiriciler için C/C++ kaynak kodundaki olası arızaların bilgilerini sağlar. Araç tarafından bildirilen yaygın kodlama hataları, arabellek taşmaları, Başlatılmamış bellek, null işaretçi başvurusu ve bellek ve kaynak sızıntılarını içerir.  
  
## <a name="ide-integrated-development-environment-integration"></a>IDE (tümleşik geliştirme ortamı) Tümleştirmesi  
 Geliştiricilerin analiz aracını kullanmasını doğal hale getirmek için, IDE içinde tamamen tümleşiktir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Yapı işlemi sırasında, kaynak kodu için oluşturulan tüm uyarılar Hata Listesi görüntülenir. Uyarıya neden olan kaynak koda gidebilir ve sorunun nedeni ve olası çözümleriyle ilgili ek bilgileri görüntüleyebilirsiniz.  
  
## <a name="pragma-support"></a>#pragma desteği  
 Geliştiriciler, `#pragma` uyarıları hata olarak değerlendirmek, uyarıları etkinleştirmek veya devre dışı bırakmak ve tek kod satırları için uyarıları bastırmak için yönergesini kullanabilir. Daha fazla bilgi için bkz. [nasıl yapılır: belirli C/C++ uyarıları Için kod analizini etkinleştirme ve devre dışı bırakma](https://msdn.microsoft.com/910b8518-71f1-4b2e-b012-70647795642a).  
  
## <a name="annotation-support"></a>Ek açıklama desteği  
 Ek açıklamalar, kod analizinin doğruluğunu geliştirir. Ek açıklamalar, işlev parametreleri ve dönüş türlerinde ön ve son koşullar hakkında ek bilgiler sağlar. Daha fazla bilgi için bkz [. nasıl yapılır: __Analysis_assume kullanarak ek kod bilgileri belirtme](../code-quality/how-to-specify-additional-code-information-by-using-analysis-assume.md)  
  
## <a name="run-analysis-tool-as-part-of-check-in-policy"></a>İade ilkesinin bir parçası olarak analiz aracını Çalıştır  
 Tüm kaynak kodu iadelerinin belirli ilkeleri karşıladıklarından emin olmak isteyebilirsiniz. Özellikle, çözümlemenin en son yerel yapıya bir adım olarak çalıştırılmış olduğundan emin olmak istersiniz. Kod Analizi iade ilkesini etkinleştirme hakkında daha fazla bilgi için bkz. [Kod Analizi Iade Ilkeleri oluşturma ve kullanma](../code-quality/creating-and-using-code-analysis-check-in-policies.md)  
  
## <a name="team-build-integration"></a>Takım derlemesi tümleştirmesi  
 Yapı işleminin bir adımı olarak kod analizi aracını çalıştırmak için derleme sisteminin tümleşik özelliklerini kullanabilirsiniz [!INCLUDE[esprtfs](../includes/esprtfs-md.md)] . Daha fazla bilgi için bkz. [uygulamayı oluşturma](/azure/devops/pipelines/index).  
  
## <a name="command-line-support"></a>Komut satırı desteği  
 Geliştiriciler geliştirme ortamında tam tümleştirmeye ek olarak, aşağıdaki örnekte gösterildiği gibi, komut satırından da çözümleme aracını da kullanabilir:  
  
 `C:\>cl /analyze Sample.cpp`
