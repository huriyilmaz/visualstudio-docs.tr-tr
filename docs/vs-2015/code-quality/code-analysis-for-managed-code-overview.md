---
title: Yönetilen KodA Genel Bakış için Kod Analizi | Microsoft Dokümanlar
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
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "72610068"
---
# <a name="code-analysis-for-managed-code-overview"></a>Yönetilen Kod için Kod Analizine Genel Bakış
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Yönetilen kod çözümlemesi, yönetilen derlemeleri analiz eder ve Derlemeler hakkındaki Microsoft .NET Framework Design Guidelines'da belirtilen programlama ve tasarım kurallarının ihlali gibi bilgileri raporlar.

 Çözümleme aracı, çözümleme sırasında gerçekleştirdiği denetimleri uyarı iletileri olarak temsil eder. Uyarı iletileri, ilgili programlama ve tasarım sorunlarını tanımlar ve mümkün olduğunda sorunun nasıl düzeltileceklerine ilişkin bilgi sağlar.

## <a name="ide-integrated-development-environment-integration"></a>IDE (entegre geliştirme ortamı) Entegrasyonu
 Geliştirici olarak, projenizde kod çözümlemesi çalıştırabilirsiniz veya el ile çalıştırabilirsiniz.

 Bir proje yi her oluşturduğunuzda kod çözümlemesi çalıştırmak için, projenin Özellik Sayfasında **Yapı'da Kod Çözümlemesi Etkinleştir 'i (CODE_ANALYSIS sabiti tanımlar)** seçersiniz. Daha fazla bilgi için [bkz: Otomatik Kod Çözümlemesini Etkinleştirme ve Devre Dışı](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)

 Bir projede kod çözümlemesi el ile çalıştırmak **için, Çözümle** menüsünde_ProjectName'de_ **Kod Çözümle'yi tıklatın.** Daha fazla bilgi için [bkz: Otomatik Kod Çözümlemesini Etkinleştirme ve Devre Dışı](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)

## <a name="rule-sets"></a>Kural Kümeleri
 Yönetilen kod için kod çözümleme kuralları *kural kümelerine*gruplandırılır. Microsoft standart kural kümelerinden birini kullanabilir veya belirli bir gereksinimi karşılamak için özel bir kural kümesi oluşturabilirsiniz. Daha fazla bilgi için [bkz.](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)

## <a name="in-source-suppression"></a>Kaynak Bastırma olarak
 Sık sık, bir uyarının geçerli olmadığını belirtmek yararlıdır. Bu, geliştiriciye ve kodu daha sonra gözden geçirebilecek diğer kişilere bir uyarının soruşturulduğunu ve sonra bastırıldığını veya yoksayıldığını bildirir.

 Kaynak Bastırma uyarıları özel öznitelikleri ile uygulanır. Bir uyarıyı bastırmak için `SuppressMessage` kaynak koduna aşağıdaki örnekte gösterildiği gibi özniteliği ekleyin:

 ```csharp
 [System.Diagnostics.CodeAnalysis.SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]
 Public class MyClass
 {
     // code
 }
 ```

 Daha fazla bilgi için [bkz.](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md)

## <a name="run-code-analysis-as-part-of-check-in-policy"></a>İade ilkesinin bir parçası olarak kod çözümlemesi çalıştırma
 Kuruluş olarak, tüm iadelerin belirli ilkeleri karşıladığını isteyebilirsiniz. Özellikle, şu ilkeleri izlediğinden emin olmak istersiniz:

- İade edilen kodda yapı hatası yoktu.

- Kod çözümlemesi en son yapının bir parçası olarak çalıştırıldı.

  Bunu iade ilkeleri belirterek gerçekleştirebilirsiniz. Daha fazla bilgi için, [Ekip Projesi İade İlkeleri ile Kod Kalitesini Artırma'ya](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)bakın.

## <a name="team-build-integration"></a>Takım Oluşturma Tümleştirmesi
 Çözümleme aracını yapı işleminin bir parçası olarak çalıştırmak için yapı sisteminin tümleşik özelliklerini kullanabilirsiniz. Daha fazla bilgi için [bkz.](/azure/devops/pipelines/index)

## <a name="see-also"></a>Ayrıca Bkz.
 [Kod Analizi Kurallarını Gruplandırmak için Kural Kümelerini](../code-quality/using-rule-sets-to-group-code-analysis-rules.md) [Kullanma: Otomatik Kod Analizini Etkinleştirme ve Devre Dışı](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)
