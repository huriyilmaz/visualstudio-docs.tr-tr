---
title: Yönetilen kod için eski analiz
ms.date: 06/12/2019
description: Visual Studio 'da eski analizler hakkında bilgi edinin. Uyarıları nasıl bastırın ve analizler ve derlemeler sırasında el ile, otomatik olarak ve analizleri nasıl çalıştıracağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: c6f1f12fa7fca964c857e534c1ffae50efe70b27
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94348664"
---
# <a name="overview-of-legacy-analysis-for-managed-code-in-visual-studio"></a>Visual Studio 'da yönetilen kod için eski Analize genel bakış

Visual Studio yönetilen kodun Kod analizini iki şekilde gerçekleştirebilir: yönetilen derlemelerin FxCop statik analizini ve daha modern .NET Compiler Platform tabanlı [kod Çözümleyicileri](../code-quality/roslyn-analyzers-overview.md)olarak da bilinen [eski analizler](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md). Bu konu başlığı altında, eski analiz ele alınmaktadır. .NET Compiler Platform tabanlı kod analizi hakkında daha fazla bilgi edinmek için bkz. [.net Compiler platform tabanlı çözümleyiciler hakkında genel bakış](../code-quality/roslyn-analyzers-overview.md).

Yönetilen kod için kod analizi, yönetilen derlemeleri analiz eder ve derlemelerle ilgili bilgileri ( [.net tasarım yönergeleri](/dotnet/standard/design-guidelines/)' nde belirlenen programlama ve tasarım kuralları ihlalleri gibi) raporlar.

Analiz Aracı, bir analiz sırasında uyarı iletileri olarak gerçekleştirdiği denetimleri temsil eder. Uyarı iletileri ilgili programlama ve tasarım sorunlarını belirler ve mümkünse sorunun nasıl düzeltileceğini gösteren bilgileri sağlar.

> [!NOTE]
> Eski analiz (Statik kod analizi) Visual Studio 'daki .NET Core ve .NET Standard projelerinde desteklenmez. MSBuild 'in bir parçası olarak bir .NET Core veya .NET Standard projesi üzerinde kod analizi çalıştırırsanız, hataya benzer bir hata görürsünüz: **CA0055: Platform \<your.dll> tanımlanamıyor**. .NET Core veya .NET Standard projelerindeki kodu çözümlemek için, bunun yerine [kod Çözümleyicileri](../code-quality/roslyn-analyzers-overview.md) kullanın.

## <a name="ide-integrated-development-environment-integration"></a>IDE (tümleşik geliştirme ortamı) Tümleştirmesi

Kod analizini, projenizde el ile veya otomatik olarak çalıştırabilirsiniz.

Her proje oluşturduğunuzda Kod analizini çalıştırmak için projenin **Kod Analizi** Özellik sayfasında seçeneğini belirleyin. Daha fazla bilgi için bkz. [nasıl yapılır: Otomatik Kod analizini etkinleştirme ve devre dışı bırakma](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).

Kod analizini bir projede el ile çalıştırmak için, menü çubuğundan kodu **Çözümle**  >  **Çalıştır kod** analizini Çalıştır  >  **' \<project>** ı seçin.

## <a name="rule-sets"></a>Kural kümeleri

Yönetilen kod için kod analizi kuralları [kural kümelerinde](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)gruplandırılır. Microsoft standart kural kümelerinden birini kullanabilir veya belirli bir gereksinimi karşılamak için [özel bir kural kümesi oluşturabilirsiniz](../code-quality/how-to-create-a-custom-rule-set.md) .

## <a name="suppress-warnings"></a>Uyarıları gizleme

Genellikle, bir uyarının uygulanamaz olduğunu göstermek yararlıdır. Bu, geliştiriciye ve kodu daha sonra gözden geçirebilecek diğer kişilere, bir uyarının araştırılması ve sonra gizlenmiş ya da yok sayılmasına bildirir.

Uyarıları kaynak bölümünde gizleme özel öznitelikler aracılığıyla uygulanır. Bir uyarıyı gizlemek için `SuppressMessage` Aşağıdaki örnekte gösterildiği gibi, kaynak koduna özniteliği ekleyin:

```csharp
[System.Diagnostics.CodeAnalysis.SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]
Public class MyClass
{
   // code
}
```

Daha fazla bilgi için bkz. [uyarıları gösterme](../code-quality/in-source-suppression-overview.md).

::: moniker range="vs-2017"

> [!NOTE]
> Bir projeyi Visual Studio 2017 ' a geçirirseniz, çok sayıda kod analizi uyarısıyla aniden karşılaşabilirsiniz. Uyarıları gidermeye hazırsanız, **Analyze**  >  **çalışma kodu analizini çözümle ve etkin sorunları Gizle** ' yi seçerek bunların tümünün görüntülenmesini sağlayabilirsiniz.
>
> ![Visual Studio 'da Kod analizini çalıştırma ve sorunları gösterme](media/suppress-active-issues.png)

::: moniker-end

::: moniker range=">=vs-2019"

> [!NOTE]
> Bir projeyi Visual Studio 2019 ' a geçirirseniz, çok sayıda kod analizi uyarısıyla aniden karşılaşabilirsiniz. Uyarıları gidermeye hazırsanız, derlemeyi **Çözümle**  >  **ve etkin sorunları Gizle** ' yi seçerek bunların tümünün görüntülenmesini sağlayabilirsiniz.

::: moniker-end

## <a name="run-code-analysis-as-part-of-check-in-policy"></a>İade ilkesinin bir parçası olarak kod analizini Çalıştır

Bir kuruluş olarak, tüm iadelerinin belirli ilkeleri yerine getirmesini gerektirmek isteyebilirsiniz. Özellikle, bu ilkeleri izlediğinizden emin olmak istersiniz:

- İade edilen kodda derleme hatası yok.

- Kod Analizi, en son yapılandırmanın bir parçası olarak çalıştırılır.

Bunu, iade ilkelerini belirterek gerçekleştirebilirsiniz. Daha fazla bilgi için bkz. [Proje Iade Ilkeleriyle kod kalitesini geliştirme](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md).

## <a name="team-build-integration"></a>Takım derlemesi tümleştirmesi

Yapı işleminin bir parçası olarak çözümleme aracını çalıştırmak için yapı sisteminin tümleşik özelliklerini kullanabilirsiniz. Daha fazla bilgi için bkz. [Azure Pipelines](/azure/devops/pipelines/index?view=vsts&preserve-view=true).

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Compiler Platform tabanlı çözümleyiciler için genel bakış](../code-quality/roslyn-analyzers-overview.md)
- [Kod Çözümleme Kurallarını Gruplandırmak için Kural Kümeleri Kullanma](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
- [Nasıl yapılır: Otomatik Kod Çözümlemesini Etkinleştirme ve Devre Dışı Bırakma](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)
