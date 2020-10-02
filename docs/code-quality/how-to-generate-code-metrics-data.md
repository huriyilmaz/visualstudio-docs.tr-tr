---
title: IDE veya komut satırından kod ölçümleri oluşturma
ms.date: 11/02/2018
ms.topic: how-to
helpviewer_keywords:
- code metrics data
- code metrics results
- code metrics [Visual Studio]
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 25fc255d0e04dd45400fa5da2b81c2e050a2150f
ms.sourcegitcommit: c025a5e2013c4955ca685092b13e887ce64aaf64
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/02/2020
ms.locfileid: "91658535"
---
# <a name="how-to-generate-code-metrics-data"></a>Nasıl yapılır: kod ölçümleri verileri oluşturma

Kod ölçümleri verilerini üç şekilde oluşturabilirsiniz:

- [.NET kod kalitesi Çözümleyicileri](#net-code-quality-analyzers-code-metrics-rules) etkinleştirerek ve içerdiği dört kod ölçümü (bakım) kurallarını etkinleştirerek.

- Visual Studio içindeki [ **Analyze**  >  **kod ölçümlerini hesapla** ](#calculate-code-metrics-menu-command) menü komutunu seçerek.

- C# ve Visual Basic projeleri için [komut satırından](#command-line-code-metrics) .

## <a name="net-code-quality-analyzers-code-metrics-rules"></a>.NET kod kalitesi Çözümleyicileri kod ölçümleri kuralları

.NET kod kalitesi Çözümleyicileri, çeşitli kod ölçümleri [Çözümleyicisi](roslyn-analyzers-overview.md) kuralları içerir:

- [CA1501](/dotnet/fundamentals/code-analysis/quality-rules/ca1501)
- [CA1502](/dotnet/fundamentals/code-analysis/quality-rules/ca1502)
- [CA1505](/dotnet/fundamentals/code-analysis/quality-rules/ca1505)
- [CA1506](/dotnet/fundamentals/code-analysis/quality-rules/ca1506)

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

Kod ölçümü kurallarının tetikleneceği eşikleri yapılandırabilirsiniz.

1. Bir metin dosyası oluşturun. Örnek olarak, *CodeMetricsConfig.txt*adını verebilirsiniz.

2. İstenen eşikleri metin dosyasına aşağıdaki biçimde ekleyin:

   ```txt
   CA1502: 10
   ```

   Bu örnekte, [CA1502](/dotnet/fundamentals/code-analysis/quality-rules/ca1502) kuralı, yöntemin döngüsel karmaşıklığı 10 ' dan büyük olduğunda tetikleneceği şekilde yapılandırılmıştır.

3. Visual Studio 'nun **Özellikler** penceresinde veya proje dosyasında, yapılandırma dosyasının yapı eylemini [**AdditionalFiles**](../ide/build-actions.md#build-action-values)olarak işaretleyin. Örnek:

   ```xml
   <ItemGroup>
     <AdditionalFiles Include="CodeMetricsConfig.txt" />
   </ItemGroup>
   ```

## <a name="calculate-code-metrics-menu-command"></a>Kod ölçümlerini hesapla menü komutu

**Analyze**  >  **Kod ölçümlerini hesapla** menüsünü analiz ederek IDE 'deki açık projelerinizden biri veya tümü için kod ölçümleri oluşturun.

### <a name="generate-code-metrics-results-for-an-entire-solution"></a>Tüm çözüm için kod ölçümleri sonuçları oluşturma

Tüm çözüm için aşağıdaki yollarla kod ölçümleri sonuçları oluşturabilirsiniz:

- Menü çubuğundan **Analyze**  >  çözüm için**kod ölçümlerini hesapla**Çözümle ' yi seçin  >  **For Solution**.

- **Çözüm Gezgini**, çözüme sağ tıklayın ve ardından **kod ölçümlerini hesapla**' yı seçin.

- **Kod ölçümleri sonuçları** penceresinde, **çözüm Için kod ölçümlerini hesapla** düğmesini seçin.

Sonuçlar oluşturulur ve **Kod ölçümleri sonuçları** penceresi görüntülenir. Sonuçlar ayrıntılarını görüntülemek için **hiyerarşi** sütunundaki ağacı genişletin.

### <a name="generate-code-metrics-results-for-one-or-more-projects"></a>Bir veya daha fazla proje için kod ölçümleri sonuçları oluşturma

1. **Çözüm Gezgini**, bir veya daha fazla proje seçin.

1. Menü çubuğundan, **Analyze**  >  Seçili proje (ler) için**kod ölçümlerini hesapla**analiz ' i seçin  >  **For Selected Project(s)**.

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

C# ve .NET Framework, .NET Core ve .NET Standard uygulamaları için Visual Basic projeler için komut satırından kod ölçümleri verileri oluşturabilirsiniz. Komut satırından kod ölçümleri çalıştırmak için [Microsoft. CodeAnalysis. ölçümler NuGet paketini](#microsoftcodeanalysismetrics-nuget-package) veya [Metrics.exe](#metricsexe) çalıştırılabilir dosyasını kendiniz oluşturun.

### <a name="microsoftcodeanalysismetrics-nuget-package"></a>Microsoft. CodeAnalysis. ölçümler NuGet paketi

Komut satırından kod ölçüm verileri oluşturmanın en kolay yolu, [Microsoft. CodeAnalysis. ölçümler](https://www.nuget.org/packages/Microsoft.CodeAnalysis.Metrics/) NuGet paketini yüklemesidir. Paketini yükledikten sonra, `msbuild /t:Metrics` proje dosyanızı içeren dizininden çalıştırın. Örnek:

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

Öğesini belirterek çıkış dosyası adını geçersiz kılabilirsiniz `/p:MetricsOutputFile=<filename>` . Ayrıca, ' i belirterek [eski stil](#previous-versions) kod ölçümleri verilerini de alabilirsiniz `/p:LEGACY_CODE_METRICS_MODE=true` . Örnek:

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

NuGet paketini yüklemek istemiyorsanız, çalıştırılabilir *Metrics.exe* doğrudan oluşturabilir ve kullanabilirsiniz. *Metrics.exe* yürütülebiliri oluşturmak için:

1. [DotNet/Roslyn-çözümleyiciler](https://github.com/dotnet/roslyn-analyzers) deposunu kopyalayın.
2. Visual Studio için Geliştirici Komut İstemi yönetici olarak açın.
3. **Roslyn-çözümleyiciler** deposunun kökünden aşağıdaki komutu yürütün:`Restore.cmd`
4. Dizini *Src\tools*olarak değiştirin.
5. **Ölçümler. csproj** projesi oluşturmak için aşağıdaki komutu yürütün:

   ```shell
   msbuild /m /v:m /p:Configuration=Release Metrics.csproj
   ```

   *Metrics.exe* adlı yürütülebilir dosya depo kökünün altındaki *artifacts\bin* dizininde oluşturulur.

#### <a name="metricsexe-usage"></a>Metrics.exe kullanımı

*Metrics.exe*çalıştırmak için, bağımsız değişken olarak bir proje veya çözüm ve bır çıkış XML dosyası sağlayın. Örnek:

```shell
C:\>Metrics.exe /project:ConsoleApp20.csproj /out:report.xml
Loading ConsoleApp20.csproj...
Computing code metrics for ConsoleApp20.csproj...
Writing output to 'report.xml'...
Completed Successfully.
```

#### <a name="legacy-mode"></a>Eski mod

*Metrics.exe* *eski modda*derlemeyi seçebilirsiniz. Aracın eski mod sürümü, [aracın daha eski sürümlerinin üretilmesinden](#previous-versions)daha yakın ölçüm değerleri üretir. Ayrıca, eski modda *Metrics.exe* , aracının önceki sürümlerinin kod ölçümlerini oluşturduğu aynı yöntem türleri kümesi için kod ölçümleri üretir. Örneğin, alan ve özellik başlatıcıları için kod ölçümleri verisi oluşturmaz. Eski mod, geriye dönük uyumluluk için veya kod ölçüm numaralarına göre kod iade kapıları varsa yararlıdır. Eski modda *Metrics.exe* oluşturma komutu şunlardır:

```shell
msbuild /m /v:m /t:rebuild /p:LEGACY_CODE_METRICS_MODE=true Metrics.csproj
```

Daha fazla bilgi için bkz. [eski modda kod ölçümleri oluşturmayı etkinleştirme](https://github.com/dotnet/roslyn-analyzers/pull/1841).

### <a name="previous-versions"></a>Önceki sürümler

::: moniker range=">=vs-2019"
Visual Studio 2015, *Metrics.exe*olarak da bilinen bir komut satırı kod ölçümleri aracına dahil edilmiştir. Aracın bu önceki sürümü bir ikili analiz, yani derleme tabanlı bir analiz işlemi gerçekleştirmiş. *Metrics.exe* aracının daha yeni sürümü kaynak kodu analiz eder. Yeni *Metrics.exe* aracı kaynak kodu tabanlı olduğundan, komut satırı kod ölçümleri sonuçları, VISUAL Studio IDE tarafından oluşturulan ve önceki *Metrics.exe*sürümleriyle farklı olabilir. Visual Studio 2019 ' den itibaren, Visual Studio IDE, kaynak kodunu komut satırı aracı gibi analiz eder ve sonuçlar aynı olmalıdır.

::: moniker-end
::: moniker range="vs-2017"
Visual Studio 2015, *Metrics.exe*olarak da bilinen bir komut satırı kod ölçümleri aracına dahil edilmiştir. Aracın bu önceki sürümü bir ikili analiz, yani derleme tabanlı bir analiz işlemi gerçekleştirmiş. Yeni *Metrics.exe* aracı bunun yerine kaynak kodu analiz eder. Yeni *Metrics.exe* aracı kaynak kodu tabanlı olduğundan, komut satırı kod ölçümleri sonuçları, VISUAL Studio IDE tarafından oluşturulan ve önceki *Metrics.exe*sürümleriyle farklıdır.
::: moniker-end

Yeni komut satırı kod ölçümleri Aracı, çözüm ve proje yüklenebilse de, kaynak kodu hatalarının varlığına bile ölçümleri hesaplar.

#### <a name="metric-value-differences"></a>Ölçüm değeri farkları

::: moniker range=">=vs-2019"
Visual Studio 2019 sürüm 16,4 ve Microsoft. CodeAnalysis. Metiği ('nın 2.9.5 sürümüyle) sürümünden başlayarak `SourceLines` `ExecutableLines` önceki ölçümü yerine koyun `LinesOfCode` . Yeni ölçümlerin açıklamaları için bkz. [kod ölçüm değerleri](../code-quality/code-metrics-values.md). `LinesOfCode`Ölçüm eski modda kullanılabilir.
::: moniker-end
::: moniker range="vs-2017"
`LinesOfCode`Ölçüm, yeni komut satırı kod ölçümleri aracında daha doğru ve güvenilirdir. Bu, herhangi bir codegen farkından bağımsızdır ve araç takımı veya çalışma zamanı değiştiğinde değişmez. Yeni araç, boş satırlar ve açıklamalar dahil olmak üzere gerçek kod satırlarını sayar.
::: moniker-end

Ve gibi diğer ölçümler `CyclomaticComplexity` `MaintainabilityIndex` , önceki *Metrics.exe*sürümleriyle aynı formülleri kullanır, ancak yeni araç `IOperations` ara dil (IL) yönergeleri yerine (mantıksal kaynak yönergeleri) sayısını sayar. Numaralar, Visual Studio IDE tarafından oluşturulan ve önceki *Metrics.exe*sürümleri tarafından biraz farklı olacaktır.

## <a name="see-also"></a>Ayrıca bkz.

- [Kod ölçümleri sonuçları penceresini kullanın](../code-quality/working-with-code-metrics-data.md)
- [Kod ölçüm değerleri](../code-quality/code-metrics-values.md)