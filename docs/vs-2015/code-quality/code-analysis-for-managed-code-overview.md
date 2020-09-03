---
title: Yönetilen koda genel bakış için kod analizi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: overview
f1_keywords:
- vs.projectpropertypages.codeanalysis
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
ms.assetid: 12ec0dab-46a4-43d8-984a-440730ef37a9
caps.latest.revision: 37
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 33ab4a000fac75c51c32e8a6d37de62e006160b3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72610068"
---
# <a name="code-analysis-for-managed-code-overview"></a>Yönetilen Kod için Kod Analizine Genel Bakış
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Yönetilen kod için kod analizi, yönetilen derlemeleri ve derleme hakkında, Microsoft .NET Framework tasarım yönergelerinden oluşan programlama ve tasarım kuralları ihlalleri gibi rapor bilgilerini analiz eder.

 Analiz Aracı, bir analiz sırasında uyarı iletileri olarak gerçekleştirdiği denetimleri temsil eder. Uyarı iletileri ilgili programlama ve tasarım sorunlarını belirler ve mümkünse sorunun nasıl düzeltileceğini gösteren bilgileri sağlar.

## <a name="ide-integrated-development-environment-integration"></a>IDE (tümleşik geliştirme ortamı) Tümleştirmesi
 Bir geliştirici olarak projenizde kod analizini otomatik olarak çalıştırabilir veya el ile çalıştırabilirsiniz.

 Her proje oluşturduğunuzda Kod analizini çalıştırmak için, projenin özellik sayfasında **derleme üzerinde Kod analizini etkinleştir (CODE_ANALYSIS sabiti tanımlar)** seçeneğini belirleyin. Daha fazla bilgi için bkz. [nasıl yapılır: Otomatik Kod analizini etkinleştirme ve devre dışı bırakma](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).

 Kod analizini bir projede el ile çalıştırmak için, **Çözümle** menüsünde,_ProjectName_ **üzerinde Kod analizini Çalıştır**' a tıklayın. Daha fazla bilgi için bkz. [nasıl yapılır: Otomatik Kod analizini etkinleştirme ve devre dışı bırakma](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).

## <a name="rule-sets"></a>Kural Kümeleri
 Yönetilen kod için kod analizi kuralları *kural kümelerinde*gruplandırılır. Microsoft standart kural kümelerinden birini kullanabilir veya belirli bir gereksinimi karşılamak için özel bir kural kümesi oluşturabilirsiniz. Daha fazla bilgi için bkz. [kod analizi kurallarını gruplandırmak Için kural kümeleri kullanma](../code-quality/using-rule-sets-to-group-code-analysis-rules.md).

## <a name="in-source-suppression"></a>Kaynak gizleme bölümünde
 Genellikle, bir uyarının uygulanamaz olduğunu göstermek yararlıdır. Bu, geliştiriciye ve kodu daha sonra gözden geçirebilecek diğer kişilere, bir uyarının araştırılması ve sonra gizlenmiş ya da yok sayılmasına bildirir.

 Uyarıları kaynak gizleme bölümünde özel öznitelikler kullanılarak uygulanır. Bir uyarıyı gizlemek için `SuppressMessage` Aşağıdaki örnekte gösterildiği gibi, kaynak koduna özniteliği ekleyin:

 ```csharp
 [System.Diagnostics.CodeAnalysis.SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]
 Public class MyClass
 {
     // code
 }
 ```

 Daha fazla bilgi için bkz. [SuppressMessage özniteliğini kullanarak uyarıları gizleme](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md).

## <a name="run-code-analysis-as-part-of-check-in-policy"></a>İade ilkesinin bir parçası olarak kod analizini Çalıştır
 Bir kuruluş olarak, tüm iadelerinin belirli ilkeleri yerine getirmesini gerektirmek isteyebilirsiniz. Özellikle, bu ilkeleri izlediğinizden emin olmak istersiniz:

- İade edilen kodda derleme hatası yoktu.

- Kod Analizi, en son yapılandırmanın bir parçası olarak çalıştırıldı.

  Bunu, iade ilkelerini belirterek gerçekleştirebilirsiniz. Daha fazla bilgi için bkz. [Takım projesi Iade Ilkeleriyle kod kalitesini geliştirme](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md).

## <a name="team-build-integration"></a>Takım derlemesi tümleştirmesi
 Yapı işleminin bir parçası olarak çözümleme aracını çalıştırmak için yapı sisteminin tümleşik özelliklerini kullanabilirsiniz. Daha fazla bilgi için bkz. [uygulamayı oluşturma](/azure/devops/pipelines/index).

## <a name="see-also"></a>Ayrıca Bkz.
 [Kod analizi kurallarını gruplandırmak Için kural kümeleri kullanma](../code-quality/using-rule-sets-to-group-code-analysis-rules.md) [nasıl yapılır: Otomatik Kod analizini etkinleştirme ve devre dışı bırakma](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)
