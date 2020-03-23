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
ms.openlocfilehash: 680d52ff04553d399b6abeb53919d8aafd4fa792
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301694"
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

## <a name="see-also"></a>Ayrıca bkz.

- [Analizcilere genel bakış](roslyn-analyzers-overview.md)
- [EditorConfig için .NET kodlama kuralı ayarları](../ide/editorconfig-code-style-settings-reference.md)
