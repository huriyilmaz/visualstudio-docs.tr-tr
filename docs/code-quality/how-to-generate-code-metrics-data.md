---
title: IDE veya komut satırından kod ölçümleri oluşturma
ms.date: 11/02/2018
ms.topic: conceptual
helpviewer_keywords:
- code metrics data
- code metrics results
- code metrics [Visual Studio]
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 55f9904c95be45c7f293355340c814faafb5de2b
ms.sourcegitcommit: 97623fd6190c43fed0d2ee7af92b01c375282622
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/04/2019
ms.locfileid: "73568848"
---
# <a name="how-to-generate-code-metrics-data"></a>Nasıl yapılır: kod ölçümleri verileri oluşturma

Kod ölçümleri verilerini üç şekilde oluşturabilirsiniz:

- [FxCop çözümleyicileri](#fxcop-analyzers-code-metrics-rules) yükleyerek ve içerdiği dört kod ölçümü (bakım) kurallarını etkinleştirerek.

- Visual Studio içindeki [ **kod ölçümlerini > hesapla** ](#calculate-code-metrics-menu-command) menü komutunu seçerek.

- Ve Visual Basic projeler için C# [komut satırından](#command-line-code-metrics) .

## <a name="fxcop-analyzers-code-metrics-rules"></a>FxCop çözümleyicileri kod ölçümleri kuralları

[Fxcopçözümleyiciler NuGet paketi](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) çeşitli kod ölçümleri [Çözümleyicisi](roslyn-analyzers-overview.md) kuralları içerir:

- [CA1501](ca1501-avoid-excessive-inheritance.md)
- [CA1502](ca1502.md)
- [CA1505](ca1505-avoid-unmaintainable-code.md)
- [CA1506](ca1506.md)

Bu kurallar varsayılan olarak devre dışıdır, ancak bunları [**Çözüm Gezgini**](use-roslyn-analyzers.md#set-rule-severity-from-solution-explorer) veya bir [kural kümesi](using-rule-sets-to-group-code-analysis-rules.md) dosyasında etkinleştirebilirsiniz. Örneğin, kural CA1502 bir uyarı olarak etkinleştirmek için,. RuleSet dosyanız aşağıdaki girişi içerir:

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="Rules" Description="Rules" ToolsVersion="16.0">
  <Rules AnalyzerId="Microsoft.CodeQuality.Analyzers" RuleNamespace="Microsoft.CodeQuality.Analyzers">
    <Rule Id="CA1502" Action="Warning" />
  </Rules>
</RuleSet>
```

### <a name="configuration"></a>Yapılandırma

FxCop çözümleyicileri paketindeki kod ölçümü kurallarının tetikleneceği eşikleri yapılandırabilirsiniz.

1. Bir metin dosyası oluşturun. Örnek olarak, *Codemetricsconfig. txt*adlı bir ad verebilirsiniz.

2. İstenen eşikleri metin dosyasına aşağıdaki biçimde ekleyin:

   ```txt
   CA1502: 10
   ```

   Bu örnekte, [CA1502](ca1502.md) kuralı, yöntemin döngüsel karmaşıklığı 10 ' dan büyük olduğunda tetikleneceği şekilde yapılandırılmıştır.

3. Visual Studio 'nun **Özellikler** penceresinde veya proje dosyasında, yapılandırma dosyasının yapı eylemini [**AdditionalFiles**](../ide/build-actions.md#build-action-values)olarak işaretleyin. Örneğin:

   ```xml
   <ItemGroup>
     <AdditionalFiles Include="CodeMetricsConfig.txt" />
   </ItemGroup>
   ```

## <a name="calculate-code-metrics-menu-command"></a>Kod ölçümlerini hesapla menü komutu

**Kod ölçümlerini hesapla** menüsünü **Çözümle** > , IDE 'deki açık projelerinizden biri veya tümü için kod ölçümleri oluşturun.

### <a name="generate-code-metrics-results-for-an-entire-solution"></a>Tüm çözüm için kod ölçümleri sonuçları oluşturma

Tüm çözüm için aşağıdaki yollarla kod ölçümleri sonuçları oluşturabilirsiniz:

- Menü çubuğundan **çözümle** > **kod ölçümlerini > hesapla** ' yı seçin.

- **Çözüm Gezgini**, çözüme sağ tıklayın ve ardından **kod ölçümlerini hesapla**' yı seçin.

- **Kod ölçümleri sonuçları** penceresinde, **çözüm Için kod ölçümlerini hesapla** düğmesini seçin.

Sonuçlar oluşturulur ve **Kod ölçümleri sonuçları** penceresi görüntülenir. Sonuçlar ayrıntılarını görüntülemek için **hiyerarşi** sütunundaki ağacı genişletin.

### <a name="generate-code-metrics-results-for-one-or-more-projects"></a>Bir veya daha fazla proje için kod ölçümleri sonuçları oluşturma

1. **Çözüm Gezgini**, bir veya daha fazla proje seçin.

1. **Seçili proje (ler) için**, menü çubuğundan **analiz** > **kod ölçümlerini hesapla > hesapla** ' yı seçin.

Sonuçlar oluşturulur ve **Kod ölçümleri sonuçları** penceresi görüntülenir. Sonuç ayrıntılarını görüntülemek için **hiyerarşideki**ağacı genişletin.

::: moniker range="vs-2017"

> [!NOTE]
> **Kod ölçümlerini hesapla** komutu .NET Core ve .NET Standard projeleri için çalışmaz. Bir .NET Core veya .NET Standard projesi için kod ölçümlerini hesaplamak üzere şunları yapabilirsiniz:
>
> - Bunun yerine [komut satırından](#command-line-code-metrics) kod ölçümlerini hesaplayın
>
> - [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) ' e yükseltme

::: moniker-end

## <a name="command-line-code-metrics"></a>Komut satırı kod ölçümleri

.NET Framework, .NET Core ve .NET Standard uygulamaları için komut satırından ve C# Visual Basic projeler için kod ölçümleri verileri oluşturabilirsiniz. Komut satırından kod ölçümleri çalıştırmak için, [Microsoft. CodeAnalysis. ölçümler NuGet paketini](#microsoftcodeanalysismetrics-nuget-package) veya [ölçümler. exe](#metricsexe) yürütülebilir dosyasını kendiniz oluşturun.

### <a name="microsoftcodeanalysismetrics-nuget-package"></a>Microsoft. CodeAnalysis. ölçümler NuGet paketi

Komut satırından kod ölçüm verileri oluşturmanın en kolay yolu, [Microsoft. CodeAnalysis. ölçümler](https://www.nuget.org/packages/Microsoft.CodeAnalysis.Metrics/) NuGet paketini yüklemesidir. Paketi yükledikten sonra, proje dosyanızı içeren dizinden `msbuild /t:Metrics` çalıştırın. Örneğin:

```shell
C:\source\repos\ClassLibrary3\ClassLibrary3>msbuild /t:Metrics
Microsoft (R) Build Engine version 16.0.360-preview+g9781d96883 for .NET Framework
Copyright (C) Microsoft Corporation. All rights reserved.

Build started 1/22/2019 4:29:57 PM.
Project "C:\source\repos\ClassLibrary3\ClassLibrary3\ClassLibrary3.csproj" on node 1 (Metrics target(s))
.
Metrics:
  C:\source\repos\ClassLibrary3\packages\Microsoft.CodeMetrics.2.6.4-ci\build\\..\Metrics\Metrics.exe /project:C:\source\repos\ClassLibrary3\ClassLibrary3\ClassLibrary3.csproj /out:ClassLibrary3.Metrics.xml
  Loading ClassLibrary3.csproj...
  Computing code metrics for ClassLibrary3.csproj...
  Writing output to 'ClassLibrary3.Metrics.xml'...
  Completed Successfully.
Done Building Project "C:\source\repos\ClassLibrary3\ClassLibrary3\ClassLibrary3.csproj" (Metrics target(s)).

Build succeeded.
    0 Warning(s)
    0 Error(s)
```

`/p:MetricsOutputFile=<filename>`belirterek çıkış dosyası adını geçersiz kılabilirsiniz. Ayrıca, `/p:LEGACY_CODE_METRICS_MODE=true`belirterek [eski stil](#previous-versions) kod ölçümleri verilerini de alabilirsiniz. Örneğin:

```shell
C:\source\repos\ClassLibrary3\ClassLibrary3>msbuild /t:Metrics /p:LEGACY_CODE_METRICS_MODE=true /p:MetricsOutputFile="Legacy.xml"
Microsoft (R) Build Engine version 16.0.360-preview+g9781d96883 for .NET Framework
Copyright (C) Microsoft Corporation. All rights reserved.

Build started 1/22/2019 4:31:00 PM.
The "MetricsOutputFile" property is a global property, and cannot be modified.
Project "C:\source\repos\ClassLibrary3\ClassLibrary3\ClassLibrary3.csproj" on node 1 (Metrics target(s))
.
Metrics:
  C:\source\repos\ClassLibrary3\packages\Microsoft.CodeMetrics.2.6.4-ci\build\\..\Metrics.Legacy\Metrics.Legacy.exe /project:C:\source\repos\ClassLibrary3\ClassLibrary3\ClassLibrary3.csproj /out:Legacy.xml
  Loading ClassLibrary3.csproj...
  Computing code metrics for ClassLibrary3.csproj...
  Writing output to 'Legacy.xml'...
  Completed Successfully.
Done Building Project "C:\source\repos\ClassLibrary3\ClassLibrary3\ClassLibrary3.csproj" (Metrics target(s)).

Build succeeded.
    0 Warning(s)
    0 Error(s)
```

### <a name="code-metrics-output"></a>Kod ölçümleri çıkışı

Oluşturulan XML çıktısı aşağıdaki biçimi alır:

```xml
<?xml version="1.0" encoding="utf-8"?>
<CodeMetricsReport Version="1.0">
  <Targets>
    <Target Name="ConsoleApp20.csproj">
      <Assembly Name="ConsoleApp20, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null">
        <Metrics>
          <Metric Name="MaintainabilityIndex" Value="100" />
          <Metric Name="CyclomaticComplexity" Value="1" />
          <Metric Name="ClassCoupling" Value="1" />
          <Metric Name="DepthOfInheritance" Value="1" />
          <Metric Name="LinesOfCode" Value="11" />
        </Metrics>
        <Namespaces>
          <Namespace Name="ConsoleApp20">
            <Metrics>
              <Metric Name="MaintainabilityIndex" Value="100" />
              <Metric Name="CyclomaticComplexity" Value="1" />
              <Metric Name="ClassCoupling" Value="1" />
              <Metric Name="DepthOfInheritance" Value="1" />
              <Metric Name="LinesOfCode" Value="11" />
            </Metrics>
            <Types>
              <NamedType Name="Program">
                <Metrics>
                  <Metric Name="MaintainabilityIndex" Value="100" />
                  <Metric Name="CyclomaticComplexity" Value="1" />
                  <Metric Name="ClassCoupling" Value="1" />
                  <Metric Name="DepthOfInheritance" Value="1" />
                  <Metric Name="LinesOfCode" Value="7" />
                </Metrics>
                <Members>
                  <Method Name="void Program.Main(string[] args)" File="C:\source\repos\ConsoleApp20\ConsoleApp20\Program.cs" Line="7">
                    <Metrics>
                      <Metric Name="MaintainabilityIndex" Value="100" />
                      <Metric Name="CyclomaticComplexity" Value="1" />
                      <Metric Name="ClassCoupling" Value="1" />
                      <Metric Name="LinesOfCode" Value="4" />
                    </Metrics>
                  </Method>
                </Members>
              </NamedType>
            </Types>
          </Namespace>
        </Namespaces>
      </Assembly>
    </Target>
  </Targets>
</CodeMetricsReport>
```

### <a name="metricsexe"></a>Ölçümler. exe

NuGet paketini yüklemek istemiyorsanız, *ölçümler. exe* yürütülebilir dosyasını doğrudan oluşturabilir ve kullanabilirsiniz. *Ölçümler. exe* yürütülebilir dosyasını oluşturmak için:

1. [DotNet/Roslyn-çözümleyiciler](https://github.com/dotnet/roslyn-analyzers) deposunu kopyalayın.
2. Visual Studio için Geliştirici Komut İstemi yönetici olarak açın.
3. **Roslyn-çözümleyiciler** deposunun kökünden şu komutu yürütün: `Restore.cmd`
4. Dizini *Src\tools*olarak değiştirin.
5. **Ölçümler. csproj** projesi oluşturmak için aşağıdaki komutu yürütün:

   ```shell
   msbuild /m /v:m /p:Configuration=Release Metrics.csproj
   ```

   *Ölçüm. exe* adlı bir yürütülebilir dosya depo kökünün altındaki *artifacts\bin* dizininde oluşturulur.

#### <a name="metricsexe-usage"></a>Ölçümler. exe kullanımı

*Ölçümler. exe*' yi çalıştırmak için bağımsız değişkenler olarak bir proje veya çözüm ve bır çıktı xml dosyası sağlayın. Örneğin:

```shell
C:\>Metrics.exe /project:ConsoleApp20.csproj /out:report.xml
Loading ConsoleApp20.csproj...
Computing code metrics for ConsoleApp20.csproj...
Writing output to 'report.xml'...
Completed Successfully.
```

#### <a name="legacy-mode"></a>Eski mod

*Ölçüm. exe* ' yi *eski modda*derlemeyi seçebilirsiniz. Aracın eski mod sürümü, [aracın daha eski sürümlerinin üretilmesinden](#previous-versions)daha yakın ölçüm değerleri üretir. Ayrıca, eski modda *ölçümler. exe* , aracının önceki sürümlerinin kod ölçümlerini oluşturduğu aynı yöntem türleri kümesi için kod ölçümleri üretir. Örneğin, alan ve özellik başlatıcıları için kod ölçümleri verisi oluşturmaz. Eski mod, geriye dönük uyumluluk için veya kod ölçüm numaralarına göre kod iade kapıları varsa yararlıdır. Eski modda *ölçüm. exe* ' yi oluşturma komutu şu şekilde yapılır:

```shell
msbuild /m /v:m /t:rebuild /p:LEGACY_CODE_METRICS_MODE=true Metrics.csproj
```

Daha fazla bilgi için bkz. [eski modda kod ölçümleri oluşturmayı etkinleştirme](https://github.com/dotnet/roslyn-analyzers/pull/1841).

### <a name="previous-versions"></a>Önceki sürümler

Visual Studio 2015, *ölçüm. exe*olarak da adlandırılan bir komut satırı kod ölçümleri aracına dahil edilmiştir. Aracın bu önceki sürümü bir ikili analiz, yani derleme tabanlı bir analiz işlemi gerçekleştirmiş. Yeni *ölçümler. exe* aracı bunun yerine kaynak kodu analiz eder. Yeni *ölçümler. exe* aracı kaynak kodu tabanlı olduğundan, komut satırı kod ölçümleri sonuçları, VISUAL Studio IDE tarafından oluşturulan ve *ölçüm. exe*' nin önceki sürümleriyle farklıdır.

Yeni komut satırı kod ölçümleri Aracı, çözüm ve proje yüklenebilse de, kaynak kodu hatalarının varlığına bile ölçümleri hesaplar.

#### <a name="metric-value-differences"></a>Ölçüm değeri farkları

`LinesOfCode` ölçümü yeni komut satırı kod ölçümleri aracında daha doğru ve güvenilir. Bu, herhangi bir codegen farkından bağımsızdır ve araç takımı veya çalışma zamanı değiştiğinde değişmez. Yeni araç, boş satırlar ve açıklamalar dahil olmak üzere gerçek kod satırlarını sayar.

`CyclomaticComplexity` ve `MaintainabilityIndex` gibi diğer ölçümler, *ölçüm. exe*' nin önceki sürümleriyle aynı formülleri kullanır, ancak yeni araç ara DIL (IL) yönergeleri yerine `IOperations` (mantıksal kaynak yönergeleri) sayısını sayar. Sayılar, Visual Studio IDE tarafından oluşturulan ve *ölçüm. exe*' nin önceki sürümleri tarafından oluşturulanlar için biraz farklı olacaktır.

## <a name="see-also"></a>Ayrıca bkz.

- [Kod ölçümleri sonuçları penceresini kullanın](../code-quality/working-with-code-metrics-data.md)
- [Kod ölçüm değerleri](../code-quality/code-metrics-values.md)
