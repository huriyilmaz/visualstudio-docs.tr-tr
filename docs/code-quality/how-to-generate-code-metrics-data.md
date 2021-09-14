---
title: IDE'den veya komut satırına kod ölçümleri oluşturma
ms.date: 11/02/2018
description: Veri kaynağında kod ölçümleri verileri Visual Studio. Bkz. Çözüm Gezgini, kural kümesi dosyası, komut satırı veya menü komutu kullanma.
ms.custom: SEO-VS-2020
ms.topic: how-to
helpviewer_keywords:
- code metrics data
- code metrics results
- code metrics [Visual Studio]
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-code-analysis
ms.workload:
- multiple
ms.openlocfilehash: 1e7928b06a75ed3a27d654182ab65f0baeba6144
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631953"
---
# <a name="how-to-generate-code-metrics-data"></a>Nasıl kullanılır: Kod ölçümleri verileri oluşturma

Kod ölçümleri verilerini üç şekilde oluşturabilirsiniz:

- .NET kod [kalitesi çözümleyicilerini etkinleştirerek](#net-code-quality-analyzers-code-metrics-rules) ve içerdiği dört kod ölçümü (bakım) kurallarını etkinleştirerek.

- Hesap menüsünde [ **Kod**  >  **Ölçümlerini Hesapla**](#calculate-code-metrics-menu-command) menü komutunu seçerek Visual Studio.

- C# [için komut](#command-line-code-metrics) satırı ve Visual Basic.

## <a name="net-code-quality-analyzers-code-metrics-rules"></a>.NET kod kalitesi çözümleyicileri kod ölçümleri kuralları

.NET kod kalitesi çözümleyicileri çeşitli kod ölçümleri [çözümleyicisi kuralları](roslyn-analyzers-overview.md) içerir:

- [CA1501](/dotnet/fundamentals/code-analysis/quality-rules/ca1501)
- [CA1502](/dotnet/fundamentals/code-analysis/quality-rules/ca1502)
- [CA1505](/dotnet/fundamentals/code-analysis/quality-rules/ca1505)
- [CA1506](/dotnet/fundamentals/code-analysis/quality-rules/ca1506)

Bu kurallar varsayılan olarak devre dışıdır ancak bunları bir [**Çözüm Gezgini**](use-roslyn-analyzers.md#set-rule-severity-from-solution-explorer) [editorConfig dosyasından etkinleştirebilirsiniz.](use-roslyn-analyzers.md#set-rule-severity-in-an-editorconfig-file) Örneğin, CA1502 kuralını bir uyarı olarak etkinleştirmek için EditorConfig dosyanız aşağıdaki girdiyi içerir:

```cs
dotnet_diagnostic.CA1502.severity = warning
```

### <a name="configuration"></a>Yapılandırma

Kod ölçümleri kurallarının hangi eşiklerde başlatıldıklarını yapılandırabilirsiniz.

1. Bir metin dosyası oluşturun. Örneğin, adını olarak *CodeMetricsConfig.txt.*

2. İstenen eşikleri metin dosyasına aşağıdaki biçimde ekleyin:

   ```txt
   CA1502: 10
   ```

   Bu örnekte [CA1502](/dotnet/fundamentals/code-analysis/quality-rules/ca1502) kuralı, bir yöntemin cyclomatic karmaşıklık düzeyi 10'dan fazla olduğunda 10'dan fazla olduğunda sılaya neden olacak şekilde yapılandırılmıştır.

3. Yapılandırma **dosyasının** Özellikler Visual Studio veya proje dosyasında yapılandırma dosyasının derleme eylemlerini [**AdditionalFiles olarak işaretle.**](../ide/build-actions.md#build-action-values) Örnek:

   ```xml
   <ItemGroup>
     <AdditionalFiles Include="CodeMetricsConfig.txt" />
   </ItemGroup>
   ```

## <a name="calculate-code-metrics-menu-command"></a>Kod Ölçümlerini Hesapla menü komutu

Kod Ölçümlerini Hesapla menüsünü kullanarak IDE'de açık olan projelerinizin biri veya **hepsi** için  >  **kod ölçümleri** oluşturma.

### <a name="generate-code-metrics-results-for-an-entire-solution"></a>Çözümün tamamı için kod ölçümleri sonuçları oluşturma

Aşağıdaki yöntemlerden herhangi birini kullanarak bir çözümün tamamı için kod ölçümleri sonuçları oluşturabilirsiniz:

- Menü çubuğundan Çözüm için Kod  >  **Ölçümlerini Hesapla'ya**  >  **tıklayın.**

- Bu **Çözüm Gezgini** çözümüne sağ tıklayın ve Ardından Kod Ölçümlerini **Hesapla'yı seçin.**

- Kod **Ölçümleri Sonuçları penceresinde** Çözüm için Kod **Ölçümlerini Hesapla düğmesini** seçin.

Sonuçlar oluşturulur ve **Kod Ölçümleri Sonuçları** penceresi görüntülenir. Sonuçların ayrıntılarını görüntülemek için Hiyerarşi sütunundaki **ağacı genişletin.**

### <a name="generate-code-metrics-results-for-one-or-more-projects"></a>Bir veya daha fazla proje için kod ölçümleri sonuçları oluşturma

1. Bu **Çözüm Gezgini** bir veya daha fazla proje seçin.

1. Menü çubuğundan Seçilen **Ölçümler**  >  **için Kod**  >  **Ölçümlerini Hesapla'Project seçin.**

Sonuçlar oluşturulur ve **Kod Ölçümleri Sonuçları** penceresi görüntülenir. Sonuçların ayrıntılarını görüntülemek için Hiyerarşisi'nin ağacını **genişletin.**

::: moniker range="vs-2017"

> [!NOTE]
> Kod **Ölçümlerini Hesapla** komutu .NET Core ve .NET Standard çalışmıyor. Bir .NET Core veya .NET Standard için kod ölçümlerini hesaplamak için:
>
> - Bunun yerine komut satırdan [kod ölçümlerini](#command-line-code-metrics) hesaplama
>
> - Visual Studio [2019'a yükseltme](https://visualstudio.microsoft.com/downloads)

::: moniker-end

## <a name="command-line-code-metrics"></a>Komut satırı kod ölçümleri

.NET Framework, .NET Core ve .NET Standard uygulamaları için C# ve Visual Basic projeleri için komut .NET Standard oluşturabilirsiniz. Komut satırdan kod ölçümlerini çalıştırmak için [Microsoft.CodeAnalysis.Metrics NuGet](#microsoftcodeanalysismetrics-nuget-package) paketini yükleyin veyaMetrics.exe[yürütülebilir](#metricsexe) dosyasını kendiniz derlemeniz gerekir.

### <a name="microsoftcodeanalysismetrics-nuget-package"></a>Microsoft.CodeAnalysis.Metrics NuGet paketi

Komut satırına kod ölçümleri verileri oluşturmanın en kolay [yolu, Microsoft.CodeAnalysis.Metrics](https://www.nuget.org/packages/Microsoft.CodeAnalysis.Metrics/) NuGet yüklemektir. Paketi yükledikten sonra proje `msbuild /t:Metrics` dosyanızı içeren dizinden çalıştırın. Örnek:

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

belirterek çıkış dosyası adını geçersiz `/p:MetricsOutputFile=<filename>` kılabilirsiniz. ayrıca belirterek [eski stil kod](#previous-versions) ölçümleri verilerini de eldeabilirsiniz. `/p:LEGACY_CODE_METRICS_MODE=true` Örnek:

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

NuGet paketini yüklemek istemiyorsanız, doğrudanMetrics.exeçalıştırılabilir *dosyasınıMetrics.exe* kullanabilirsiniz. Yürütülebilir *dosyaMetrics.exe* için:

1. [dotnet/roslyn-analyzers repo'larını](https://github.com/dotnet/roslyn-analyzers) kopyalama.
2. Yönetici olarak Geliştirici Komut İstemi için Visual Studio'i açın.
3. **roslyn-analyzers repo kökünden** aşağıdaki komutu yürütün:`Restore.cmd`
4. dizinini *src\Tools\Metrics olarak değiştirme.*
5. **Metrics.csproj projesini oluşturmak için aşağıdaki komutu yürütün:**

   ```shell
   msbuild /m /v:m /p:Configuration=Release Metrics.csproj
   ```

   Metrics.exeadlı *yürütülebilir* dosya, depo kökü altındaki *artifacts\bin* dizininde oluşturulur.

#### <a name="metricsexe-usage"></a>Metrics.exe kullanımı

bir *Metrics.exe* çalıştırmak için, bağımsız değişken olarak bir proje veya çözüm ve çıkış XML dosyası sağlar. Örnek:

```shell
C:\>Metrics.exe /project:ConsoleApp20.csproj /out:report.xml
Loading ConsoleApp20.csproj...
Computing code metrics for ConsoleApp20.csproj...
Writing output to 'report.xml'...
Completed Successfully.
```

#### <a name="legacy-mode"></a>Eski mod

Eski modda bir *Metrics.exe* *seçebilirsiniz.* Aracın eski mod sürümü, aracın eski sürümleri tarafından oluşturulana [daha yakın ölçüm değerleri üretir.](#previous-versions) Ayrıca, eski modda *Metrics.exe,* aracın önceki sürümlerinde kod ölçümleri oluşturan aynı yöntem türleri kümesi için kod ölçümleri üretir. Örneğin, alan ve özellik başlatıcıları için kod ölçümleri verileri oluşturmaz. Eski mod geriye dönük uyumluluk için veya kod ölçüm numaralarına göre kod iade geçitleri varsa yararlıdır. Eski modda *Metrics.exe* komutu şudur:

```shell
msbuild /m /v:m /t:rebuild /p:LEGACY_CODE_METRICS_MODE=true Metrics.csproj
```

Daha fazla bilgi için [bkz. Eski modda kod ölçümleri oluşturma.](https://github.com/dotnet/roslyn-analyzers/pull/1841)

### <a name="previous-versions"></a>Önceki sürümler

::: moniker range=">=vs-2019"
Visual Studio 2015'te bir komut satırı kod ölçümleri aracı da *Metrics.exe.* Aracın önceki sürümü, derleme tabanlı bir analiz olan ikili bir analiz gerçekleştirdi. Metrics.exe *aracının yeni* sürümü bunun yerine kaynak kodunu analiz eder. Yeni *Metrics.exe* aracı kaynak kodu tabanlı olduğundan, komut satırı kod ölçümleri sonuçları Visual Studio IDE tarafından ve öncekiMetrics.exesürümleri tarafından oluşturulanlardan *farklı olabilir.* Visual Studio 2019'dan başlayarak, Visual Studio IDE komut satırı aracı gibi kaynak kodunu analiz eder ve sonuçlar aynı olması gerekir.

::: moniker-end
::: moniker range="vs-2017"
Visual Studio 2015'te bir komut satırı kod ölçümleri aracı da *Metrics.exe.* Aracın önceki sürümü, derleme tabanlı bir analiz olan ikili bir analiz gerçekleştirdi. Yeni *Metrics.exe* aracı bunun yerine kaynak kodunu analiz eder. Yeni *Metrics.exe* aracı kaynak kodu tabanlı olduğundan, komut satırı kod ölçümleri sonuçları Visual Studio IDE tarafından ve önceki sürümleri tarafından oluşturulan sonuçlardan *Metrics.exe.*
::: moniker-end

Yeni komut satırı kod ölçümleri aracı, çözüm ve proje yüklen sürece kaynak kodu hataları olsa bile ölçümleri hesaplar.

#### <a name="metric-value-differences"></a>Ölçüm değeri farklılıkları

::: moniker range=">=vs-2019"
Visual Studio 2019 sürüm 16.4 ve Microsoft.CodeAnalysis.Metics (2.9.5) sürümünden başlayarak önceki `SourceLines` `ExecutableLines` ölçümü `LinesOfCode` değiştirin. Yeni ölçümlerin açıklamaları için bkz. [Kod ölçümleri değerleri.](../code-quality/code-metrics-values.md) Ölçüm `LinesOfCode` eski modda kullanılabilir.
::: moniker-end
::: moniker range="vs-2017"
Yeni `LinesOfCode` komut satırı kod ölçümleri aracında ölçüm daha doğru ve güvenilirdir. Codegen farkları birbirinden bağımsızdır ve araç kümesi veya çalışma zamanı değiştiklerde değişmez. Yeni araç, boş satırlar ve açıklamalar dahil olmak üzere gerçek kod satırlarını sayar.
::: moniker-end

ve gibi diğer ölçümler, öncekiMetrics.exesürümleriyle aynı formülleri kullanır ancak yeni araç, ara dil (IL) yönergeleri yerine sayısını (mantıksal kaynak `CyclomaticComplexity` `MaintainabilityIndex` ** `IOperations` yönergeleri) sayar. Sayılar, IDE tarafından oluşturulanlardan ve Visual Studio önceki sürümlerine göre biraz *farklıMetrics.exe.*

## <a name="see-also"></a>Ayrıca bkz.

- [Kod Ölçümleri Sonuçları penceresini kullanma](../code-quality/working-with-code-metrics-data.md)
- [Kod ölçümleri değerleri](../code-quality/code-metrics-values.md)