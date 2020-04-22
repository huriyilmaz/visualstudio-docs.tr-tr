---
title: EditorConfig karşı analizörler
ms.date: 03/11/2019
ms.topic: conceptual
helpviewer_keywords:
- analyzers, faq
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 56b0c0defe5593c9dc0e2111ef5984a5c51eaf55
ms.sourcegitcommit: a7f781d5a089e6aab6b073a07f3d4d2967af8aa6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81760140"
---
# <a name="code-analysis-faq"></a>Kod analizi SSS

Bu sayfa Visual Studio'da .NET Derleyici Platformu tabanlı kod analizi hakkında sık sorulan bazı soruların yanıtlarını içermektedir.

## <a name="code-analysis-versus-editorconfig"></a>Code analysis versus EditorConfig

**S**: Kod stilini denetlemek için kod analizi ni veya EditorConfig'i kullanmalı mıyım?

**A**: Kod analizi ve EditorConfig dosyaları el ele çalışır. [EditorConfig dosyasında](../ide/editorconfig-code-style-settings-reference.md) veya [metin düzenleyicisi Seçenekleri](../ide/code-styles-and-code-cleanup.md) sayfasında kod stilleri tanımladığınızda, Visual Studio'da yerleşik kod çözümleyicilerini gerçekte yapılandırMış oluyorsunuz. EditorConfig dosyaları çözümleyici kurallarını etkinleştirmek veya devre dışı etmek ve [fxCop çözümleyicileri](configure-fxcop-analyzers.md)gibi bazı NuGet çözümleyici paketlerini yapılandırmak için de kullanılabilir.

## <a name="editorconfig-versus-rule-sets"></a>EditorConfig karşı kural kümeleri

**S**: Çözümleyicilerimi bir kural kümesi veya EditorConfig dosyası kullanarak yapılandırmalı mıyım?

**C**: Kural kümeleri ve EditorConfig dosyaları bir arada bulunabilir ve her ikisi de çözümleyicileri yapılandırmak için kullanılabilir. Hem EditorConfig dosyaları hem de kural kümeleri, kuralları etkinleştirmenizi ve devre dışı bırakmanızı ve önem derecelerini belirlemenize olanak tanır.

Ancak, EditorConfig dosyaları da kuralları yapılandırmak için ek yollar sunuyoruz:

- FxCop çözümleyicileri için, EditorConfig dosyaları [analiz etmek için kod türleri tanımlamak](fxcop-analyzer-options.md)sağlar.
- Visual Studio'da yerleşik kod stili çözümleyiciler için EditorConfig dosyaları, bir kod tabanı için [tercih edilen kod stillerini tanımlamanıza](../ide/editorconfig-code-style-settings-reference.md) izin sağlar.

Kural kümelerine ve EditorConfig dosyalarına ek olarak, bazı çözümleyiciler C# ve VB derleyicileri için [ek dosya](../ide/build-actions.md#build-action-values) olarak işaretlenmiş metin dosyaları nın kullanımı yla yapılandırılır.

> [!NOTE]
> - EditorConfig dosyaları yalnızca Visual Studio 2019 sürüm 16.3 ve sonraki sürümlerinde kuralları etkinleştirmek ve önemlerini ayarlamak için kullanılabilir.
> - EditorConfig dosyaları eski çözümlemesi yapılandırmak için kullanılamaz, kural kümeleri ise olabilir.

## <a name="code-analysis-in-ci-builds"></a>CI oluştururkod analizi

**S**: .NET Derleyici Platformu tabanlı kod analizi sürekli entegrasyon (CI) oluşturur çalışır mı?

**A**: Evet. NuGet paketinden yüklenen çözümleyiciler için, bu kurallar, CI oluşturma sırasında da dahil olmak [üzere, yapı zamanında uygulanır.](roslyn-analyzers-overview.md#build-errors) CI'de kullanılan çözümleyiciler, hem kural kümelerinden hem de EditorConfig dosyalarından saygı kuralı yapılandırması oluşturur. Şu anda, Visual Studio'da yerleşik kod çözümleyicileri NuGet paketi olarak kullanılamaz ve bu nedenle bu kurallar CI yapısında uygulanamaz.

## <a name="ide-analyzers-versus-stylecop"></a>IDE analizörleri karşı StyleCop

**S**: Visual Studio IDE kod analizörleri ile StyleCop analizörleri arasındaki fark nedir?

**C**: Visual Studio IDE, hem kod stili hem de kalite sorunlarını arayan yerleşik çözümleyiciler içerir. Bu kurallar, yeni dil özelliklerini tanıtıldıklarında kullanmanıza ve kodunuzu koruyabilirliği geliştirmenize yardımcı olur. IDE çözümleyicileri sürekli her Visual Studio sürümü ile güncellenir.

[StyleCop çözümleyicileri,](https://github.com/DotNetAnalyzers/StyleCopAnalyzers) kodunuzda stil tutarlılığını kontrol eden bir NuGet paketi olarak yüklenmiş üçüncü taraf çözümleyicilerdir. Genel olarak, StyleCop kuralları, bir stili diğerine önermeden bir kod tabanı için kişisel tercihleri ayarlamanızı sağlar.

## <a name="code-analyzers-versus-legacy-analysis"></a>Kod çözümleyicileri ve eski analiz

**S**: Eski çözümleme ile .NET Derleyici Platformu tabanlı kod analizi arasındaki fark nedir?

**C**: .NET Derleyici Platformu tabanlı kod analizi kaynak kodunu gerçek zamanlı olarak ve derleme sırasında analiz ederken, eski çözümleme, yapı tamamlandıktan sonra ikili dosyaları analiz eder. Daha fazla bilgi için [bkz.](roslyn-analyzers-overview.md#source-code-analysis-versus-legacy-analysis) [FxCop analyzers FAQ](fxcop-analyzers-faq.md)

## <a name="treat-warnings-as-errors"></a>Uyarıları hata olarak ele

**S**: Projem uyarıları hata olarak ele almak için yapı seçeneğini kullanır. Eski çözümlemeden kaynak kod çözümlemesi için geçiş yaptıktan sonra, tüm kod çözümleme uyarıları artık hata olarak görünür. Bunu nasıl önleyebilirim?

**C**: Kod çözümleme uyarılarının hata olarak değerlendirilmesini önlemek için aşağıdaki adımları izleyin:

  1. Aşağıdaki içeriğe sahip bir .props dosyası oluşturun:

     ```xml
     <Project>
        <PropertyGroup>
           <CodeAnalysisTreatWarningsAsErrors>false</CodeAnalysisTreatWarningsAsErrors>
        </PropertyGroup>
     </Project>
     ```

  2. Önceki adımda oluşturduğunuz .props dosyasını almak için .csproj veya .vbproj proje dosyanıza bir satır ekleyin. Bu satır, FxCop çözümleyicisi .props dosyalarını alan herhangi bir satırdan önce yerleştirilmelidir. Örneğin, .props dosyanız codeanalysis.props olarak adlandırılmışsa:

     ```xml
     ...
     <Import Project="..\..\codeanalysis.props" Condition="Exists('..\..\codeanalysis.props')" />
     <Import Project="..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.5\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props" Condition="Exists('..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.5\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props')" />
     ...
     ```

## <a name="code-analysis-solution-property-page"></a>Kod analizi çözüm özelliği sayfası

**S**: Çözüm için Kod Analizi özellik sayfası nerededir?

**C**: Çözüm düzeyindeki Kod Analizi özelliği sayfası daha güvenilir paylaşılan özellik grubu lehine kaldırıldı. Kod Çözümlemesi'ni proje düzeyinde yönetmek için Kod Analizi özellik sayfası hala kullanılabilir. (Yönetilen projeler için kural kümelerinden kural yapılandırması için EditorConfig'e geçiş yapmanızı da öneririz.)  Bir çözüm veya repodaki birden çok/tüm projedeki kural kümelerini paylaşmak için, paylaşılan bir sahne/hedef dosyasında veya Directory.props/Directory.targets dosyasında CodeAnalysisRuleSet özelliğine sahip bir özellik grubu tanımlamanızı öneririz. Tüm projelerinizin içe aktardığı bu tür ortak sahne veya hedefleriniz yoksa, [dizinveya alt dizinlerinde tanımlanan tüm proje dosyalarında otomatik olarak içe aktarılan bir üst düzey çözüm dizininde böyle bir özellik grubunu dizin.sahne veya Dizin hedeflerine eklemeyi](https://docs.microsoft.com/visualstudio/msbuild/customize-your-build?directorybuildprops-and-directorybuildtargets)düşünmelisiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Analizcilere genel bakış](roslyn-analyzers-overview.md)
- [EditorConfig için .NET kodlama kuralı ayarları](../ide/editorconfig-code-style-settings-reference.md)
