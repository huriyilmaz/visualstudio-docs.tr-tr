---
title: IDE veya komut satırından kod ölçümleri oluşturma
ms.date: 11/02/2018
ms.topic: conceptual
helpviewer_keywords:
- code metrics data
- code metrics results
- code metrics [Visual Studio]
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1abae26ed8a5e5db74f7b0d04db66d9d99930d5c
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649303"
---
# <a name="how-to-generate-code-metrics-data"></a>Nasıl kullanılır: Kod ölçümleri verisi oluşturma

Kod ölçümleri verilerini üç şekilde oluşturabilirsiniz:

- [FxCop çözümleyicileri](#fxcop-analyzers-code-metrics-rules) yükleyerek ve içerdiği dört kod ölçümleri (sürdürülebilirlik) kuralları nı etkinleştirerek.

- Visual Studio içindeki [ **Kod** > Metriklerini Analiz](#calculate-code-metrics-menu-command) Et menüsü komutunu seçerek.

- C# ve Visual Basic projeleri için [komut satırından.](#command-line-code-metrics)

## <a name="fxcop-analyzers-code-metrics-rules"></a>FxCop analizörleri kod ölçümleri kuralları

[FxCopAnalyzeers NuGet paketi](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) çeşitli kod ölçümleri [analizörü](roslyn-analyzers-overview.md) kuralları içerir:

- [CA1501](ca1501-avoid-excessive-inheritance.md)
- [CA1502](ca1502.md)
- [CA1505](ca1505.md)
- [CA1506](ca1506.md)

Bu kurallar varsayılan olarak devre dışı bırakılır, ancak [**bunları Çözüm Gezgini'nden**](use-roslyn-analyzers.md#set-rule-severity-from-solution-explorer) veya [kural kümesi](using-rule-sets-to-group-code-analysis-rules.md) dosyasından etkinleştirebilirsiniz. Örneğin, CA1502 kuralını uyarı olarak etkinleştirmek için .ruleset dosyanız aşağıdaki girişi içerir:

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="Rules" Description="Rules" ToolsVersion="16.0">
  <Rules AnalyzerId="Microsoft.CodeQuality.Analyzers" RuleNamespace="Microsoft.CodeQuality.Analyzers">
    <Rule Id="CA1502" Action="Warning" />
  </Rules>
</RuleSet>
```

### <a name="configuration"></a>Yapılandırma

FxCop analizörleri paket ateşinde kod ölçümlerinin kurallarının olduğu eşikleri yapılandırabilirsiniz.

1. Bir metin dosyası oluşturun. Örnek olarak, *codeMetricsConfig.txt*adlandırabilirsiniz.

2. Metin dosyasına aşağıdaki biçimde istenen eşikleri ekleyin:

   ```txt
   CA1502: 10
   ```

   Bu örnekte, bir yöntemin siklomatik karmaşıklığı 10'dan büyük olduğunda [CA1502](ca1502.md) kuralı ateşle yapılandırılacaktır.

3. Visual Studio'nun **Özellikler** penceresinde veya proje dosyasında, yapılandırma dosyasının yapı eylemini [**Ek Dosyalar**](../ide/build-actions.md#build-action-values)olarak işaretleyin. Örneğin:

   ```xml
   <ItemGroup>
     <AdditionalFiles Include="CodeMetricsConfig.txt" />
   </ItemGroup>
   ```

## <a name="calculate-code-metrics-menu-command"></a>Kod Metriklerini Hesapla menü komutu

**Kodu Hesapla** türünize göre **analiz** > et menüsünü kullanarak IDE'deki açık projelerinizin biri veya tümü için kod ölçümleri oluşturun.

### <a name="generate-code-metrics-results-for-an-entire-solution"></a>Tüm çözüm için kod ölçümleri sonuçları oluşturma

Tüm çözüm için kod ölçümleri sonuçları aşağıdaki yollardan herhangi biri oluşturabilirsiniz:

- Menü çubuğundan Çözüm**için****Kod Ölçümlerini** >  **Hesapla'yı** > seçin.

- **Çözüm Gezgini'nde,** çözüme sağ tıklayın ve ardından **Kod Metriklerini Hesapla'yı**seçin.

- Kod **Ölçümleri Sonuçları** penceresinde, **Çözüm için Kod Metriklerini Hesapla** düğmesini seçin.

Sonuçlar oluşturulur ve **Kod Ölçümleri Sonuçları** penceresi görüntülenir. Sonuç ayrıntılarını görüntülemek için **Hiyerarşi** sütunundaki ağacı genişletin.

### <a name="generate-code-metrics-results-for-one-or-more-projects"></a>Bir veya daha fazla proje için kod ölçümleri sonuçları oluşturma

1. **Çözüm Gezgini'nde**bir veya daha fazla proje seçin.

1. Menü çubuğundan,**Seçili Proje(ler) için**Hesap kodu**ölçümlerini** >  **analiz** > et'i seçin.

Sonuçlar oluşturulur ve **Kod Ölçümleri Sonuçları** penceresi görüntülenir. Sonuç ayrıntılarını görüntülemek için **Hiyerarşi'deki**ağacı genişletin.

::: moniker range="vs-2017"

> [!NOTE]
> **Kod Ölçümleri Hesapla** komutu .NET Core ve .NET Standard projeleri için çalışmaz. Bir .NET Core veya .NET Standard projesinin kod ölçümlerini hesaplamak için şunları yapabilirsiniz:
>
> - Bunun yerine komut [satırından](#command-line-code-metrics) kod ölçümlerini hesaplama
>
> - Visual [Studio 2019'a](https://visualstudio.microsoft.com/downloads) yükseltin

::: moniker-end

## <a name="command-line-code-metrics"></a>Komut satırı kod ölçümleri

.NET Framework, .NET Core ve .NET Standard uygulamaları için C# ve Visual Basic projeleri için komut satırından kod ölçümleri verileri oluşturabilirsiniz. Komut satırından kod ölçümlerini çalıştırmak için [Microsoft.CodeAnalysis.Metrics NuGet paketini](#microsoftcodeanalysismetrics-nuget-package) yükleyin veya [Metrics.exe'yi](#metricsexe) kendiniz çalıştırabilirsiniz'ı oluşturun.

### <a name="microsoftcodeanalysismetrics-nuget-package"></a>Microsoft.CodeAnalysis.Metrics NuGet paketi

Komut satırından kod ölçümleri verileri oluşturmanın en kolay yolu [Microsoft.CodeAnalysis.Metrics](https://www.nuget.org/packages/Microsoft.CodeAnalysis.Metrics/) NuGet paketini yüklemektir. Paketi yükledikten sonra, proje `msbuild /t:Metrics` dosyanızı içeren dizinden çalıştırın. Örneğin:

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

Çıktı dosya adını belirterek `/p:MetricsOutputFile=<filename>`geçersiz kılabilirsiniz. Ayrıca, eski [stil](#previous-versions) kod ölçümleri verilerini `/p:LEGACY_CODE_METRICS_MODE=true`de belirterek alabilirsiniz. Örneğin:

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

### <a name="code-metrics-output"></a>Kod ölçümleri çıktısı

Oluşturulan XML çıkışı aşağıdaki biçimi alır:

::: moniker range=">=vs-2019"
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
          <Metric Name="SourceLines" Value="11" />
          <Metric Name="ExecutableLines" Value="1" />
        </Metrics>
        <Namespaces>
          <Namespace Name="ConsoleApp20">
            <Metrics>
              <Metric Name="MaintainabilityIndex" Value="100" />
              <Metric Name="CyclomaticComplexity" Value="1" />
              <Metric Name="ClassCoupling" Value="1" />
              <Metric Name="DepthOfInheritance" Value="1" />
              <Metric Name="SourceLines" Value="11" />
              <Metric Name="ExecutableLines" Value="1" />
            </Metrics>
            <Types>
              <NamedType Name="Program">
                <Metrics>
                  <Metric Name="MaintainabilityIndex" Value="100" />
                  <Metric Name="CyclomaticComplexity" Value="1" />
                  <Metric Name="ClassCoupling" Value="1" />
                  <Metric Name="DepthOfInheritance" Value="1" />
                  <Metric Name="SourceLines" Value="7" />
                  <Metric Name="ExecutableLines" Value="1" />
                </Metrics>
                <Members>
                  <Method Name="void Program.Main(string[] args)" File="C:\source\repos\ConsoleApp20\ConsoleApp20\Program.cs" Line="7">
                    <Metrics>
                      <Metric Name="MaintainabilityIndex" Value="100" />
                      <Metric Name="CyclomaticComplexity" Value="1" />
                      <Metric Name="ClassCoupling" Value="1" />
                      <Metric Name="SourceLines" Value="4" />
                      <Metric Name="ExecutableLines" Value="1" />
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
::: moniker-end
::: moniker range="vs-2017"
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
::: moniker-end

### <a name="metricsexe"></a>Metrics.exe

NuGet paketini yüklemek istemiyorsanız, *Metrics.exe'yi* doğrudan çalıştırılabilir olarak oluşturabilir ve kullanabilirsiniz. *Metrics.exe* çalıştırılabilir oluşturmak için:

1. [Dotnet/roslyn-analyzer](https://github.com/dotnet/roslyn-analyzers) repo'yu klonla.
2. Yönetici olarak Visual Studio için Geliştirici Komut Komut Ustem'i açın.
3. **Roslyn-çözümleyiciresinin** kökünden aşağıdaki komutu uygulayın:`Restore.cmd`
4. Dizini *src\Tools*olarak değiştirin.
5. **Metrics.csproj** projesini oluşturmak için aşağıdaki komutu uygulayın:

   ```shell
   msbuild /m /v:m /p:Configuration=Release Metrics.csproj
   ```

   Repo kökü altında *yapıls\bin* dizininde *Metrics.exe* adlı bir yürütülebilir ad oluşturulur.

#### <a name="metricsexe-usage"></a>Metrics.exe kullanımı

*Metrics.exe*çalıştırmak için, bir proje veya çözüm ve bağımsız değişken olarak bir çıkış XML dosyası kaynağı. Örneğin:

```shell
C:\>Metrics.exe /project:ConsoleApp20.csproj /out:report.xml
Loading ConsoleApp20.csproj...
Computing code metrics for ConsoleApp20.csproj...
Writing output to 'report.xml'...
Completed Successfully.
```

#### <a name="legacy-mode"></a>Eski mod

Eski *modda* *Metrics.exe* oluşturmayı seçebilirsiniz. Aracın eski mod sürümü, [aracın eski sürümlerinin oluşturduğuna](#previous-versions)daha yakın olan metrik değerler oluşturur. Ayrıca, eski *modda, Metrics.exe,* aracın önceki sürümlerinin kod ölçümleri için oluşturduğu yöntem türleri kümesi için kod ölçümleri oluşturur. Örneğin, alan ve özellik başlangıç kaydediciler için kod ölçümleri verileri oluşturmaz. Eski mod geriye dönük uyumluluk için veya kod ölçüm numaralarına dayalı kod iade kapılarınız varsa yararlıdır. *Metrics.exe'yi* eski modda oluşturma komutu:

```shell
msbuild /m /v:m /t:rebuild /p:LEGACY_CODE_METRICS_MODE=true Metrics.csproj
```

Daha fazla bilgi için [bkz.](https://github.com/dotnet/roslyn-analyzers/pull/1841)

### <a name="previous-versions"></a>Önceki sürümler

::: moniker range=">=vs-2019"
Visual Studio 2015, *Metrics.exe*olarak da adlandırılan bir komut satırı kod ölçümleri aracı nı içeriyordu. Aracın bu önceki sürümü, bir ikili çözümleme, yani bir derleme tabanlı analiz yaptı. *Metrics.exe* aracının yeni sürümü kaynak kodu çözümler yerine. Yeni *Metrics.exe* aracı kaynak kodu tabanlı olduğundan, komut satırı kod ölçümleri sonuçları Visual Studio IDE ve *Metrics.exe'nin*önceki sürümleri tarafından oluşturulanlardan farklı olabilir. Visual Studio 2019'dan itibaren Visual Studio IDE komut satırı aracı gibi kaynak kodunu analiz eder ve sonuçlar aynı olmalıdır.

::: moniker-end
::: moniker range="vs-2017"
Visual Studio 2015, *Metrics.exe*olarak da adlandırılan bir komut satırı kod ölçümleri aracı nı içeriyordu. Aracın bu önceki sürümü, bir ikili çözümleme, yani bir derleme tabanlı analiz yaptı. Yeni *Metrics.exe* aracı bunun yerine kaynak kodu analiz eder. Yeni *Metrics.exe* aracı kaynak kodu tabanlı olduğundan, komut satırı kod ölçümleri sonuçları Visual Studio IDE ve *Metrics.exe'nin*önceki sürümleri tarafından oluşturulanlardan farklıdır.
::: moniker-end

Yeni komut satırı kod ölçümleri aracı, çözüm ve proje yüklendiği sürece kaynak kodu hatalarının varlığında bile ölçümleri hesaplar.

#### <a name="metric-value-differences"></a>Metrik değer farkları

::: moniker range=">=vs-2019"
Visual Studio 2019 sürüm 16.4 ve Microsoft.CodeAnalysis.Metics (2.9.5) `SourceLines` ile başlayarak önceki `ExecutableLines` `LinesOfCode` ölçütün yerini alın. Yeni ölçümlerin açıklamaları için [Kod ölçümleri değerlerine](../code-quality/code-metrics-values.md)bakın. Metrik `LinesOfCode` eski modda kullanılabilir.
::: moniker-end
::: moniker range="vs-2017"
Metrik, `LinesOfCode` yeni komut satırı kod ölçümleri aracında daha doğru ve güvenilirdir. Herhangi bir kodgen farklarından bağımsızdır ve araç seti veya çalışma zamanı değiştiğinde değişmez. Yeni araç, boş satırlar ve açıklamalar da dahil olmak üzere gerçek kod satırlarını sayar.
::: moniker-end

Diğer ölçümler gibi `CyclomaticComplexity` `MaintainabilityIndex` ve *Metrics.exe*önceki sürümleri ile aynı formüller kullanmak, ancak `IOperations` yeni araç (mantıksal kaynak talimatları) yerine ara dil (IL) yönergeleri sayısını sayar. Sayılar Visual Studio IDE ve *Metrics.exe*önceki sürümleri tarafından oluşturulan biraz farklı olacaktır.

## <a name="see-also"></a>Ayrıca bkz.

- [Kod Ölçümleri Sonuçları penceresini kullanma](../code-quality/working-with-code-metrics-data.md)
- [Kod ölçümleri değerleri](../code-quality/code-metrics-values.md)
