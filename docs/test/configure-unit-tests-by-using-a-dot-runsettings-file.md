---
title: Birim testlerini bir .runsettings dosyasıyla yapılandırma
description: Komut satırı, IDE veya derleme iş akışında çalıştırılan birim testlerini yapılandırmak için Visual Studio'daki .runsettings dosyasını kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 12/06/2021
ms.topic: conceptual
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 5bc7610a65b2bc5b8f7194781fd05c04a26f0cb2
ms.sourcegitcommit: 965372ad0d75f015403c1af508080bf799914ce3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "135805357"
---
# <a name="configure-unit-tests-by-using-a-runsettings-file"></a>*.runsettings* dosyası kullanarak birim testlerini yapılandırma

Birim testleri Visual Studio bir *.runsettings dosyası kullanılarak yalıtabilirsiniz.* Örneğin, testlerin çalıştır olduğu .NET sürümünü, test sonuçlarının dizinini veya test çalıştırması sırasında toplanan verileri değiştirebilirsiniz. .runsettings dosyasının *yaygın bir kullanımı,* kod kapsamı [analizini özelleştirmektir.](../test/customizing-code-coverage-analysis.md)

Çalıştırma ayarları dosyaları, komut satırı [,](vstest-console-options.md)IDE veya Azure Test Plans veya Team Foundation Server (TFS) kullanarak bir derleme iş akışında çalıştırılan testleri yapılandırmak için kullanılabilir. [](/azure/devops/pipelines/test/getting-started-with-continuous-testing?view=vsts&preserve-view=true)

Çalıştırma ayarları dosyaları isteğe bağlıdır. Özel yapılandırmaya gerek yoksa bir *.runsettings dosyasına ihtiyacınız* yok.

## <a name="create-a-run-settings-file-and-customize-it"></a>Çalıştırma ayarları dosyası oluşturma ve özelleştirme

1. Çözümünüze bir çalıştırma ayarları dosyası ekleyin. Bu **Çözüm Gezgini,** çözümlü çözüm kısayol menüsünde Yeni Öğe  >  **Ekle'yi ve** **ARDıNDAN XML Dosyası'yı seçin.** Dosyayı *test.runsettings gibi bir adla kaydedin.*

   > [!TIP]
   > *.runsettings* uzantısını kullanıyorsanız dosya adı önemli değildir.

2. [Örnek *.runsettings dosyasından içeriği ekleyin](#example-runsettings-file)ve ardından aşağıdaki bölümlerde açıklandığı gibi ihtiyaçlarınıza göre özelleştirin.

3. Aşağıdaki yöntemlerden birini kullanarak istediğiniz *.runsettings dosyasını belirtin:

   - [Visual Studio IDE](#specify-a-run-settings-file-in-the-ide)
   - [Komut satırı](#specify-a-run-settings-file-from-the-command-line)
   - [Azure Test Plans](/azure/devops/pipelines/test/getting-started-with-continuous-testing?view=vsts&preserve-view=true) veya Team Foundation Server (TFS) kullanarak iş akışı oluşturma.

4. Özel çalıştırma ayarlarını kullanmak için birim testlerini çalıştırın.

::: moniker range="vs-2017"

IDE'de özel ayarları kapatmak ve açmak için Test Çalışma Alanı menüsünde  dosyanın > **seçimini kaldırın veya Ayarlar** seçin.

![Visual Studio 2017'de özel ayarlar dosyasıyla test ayarları menüsü](../test/media/codecoverage-settingsfile.png)

::: moniker-end

::: moniker range=">=vs-2019"

IDE'de özel ayarları kapatmak ve açmak için Test menüsünde dosyanın seçimini kaldırın **veya** dosyayı seçin.

::: moniker-end

> [!TIP]
> Çözümde birden fazla *.runsettings* dosyası oluşturabilir ve gerektiğinde etkin test ayarları dosyası olarak birini seçebilirsiniz.

## <a name="specify-a-run-settings-file-in-the-ide"></a>IDE'de bir çalıştırma ayarları dosyası belirtme

Kullanılabilir yöntemler, uygulama sürümünüze Visual Studio.

::: moniker range="vs-2017"
IDE'de bir çalıştırma ayarları dosyası belirtmek için **Test** Testi Ayarlar Test Ayarlar Dosyasını Seçin'i ve >  >  *ardından .runsettings dosyasını* seçin.

![Visual Studio 2017'de test ayarları dosya menüsünü seçin](media/select-test-settings-file.png)

Dosya, Test Ayarlar görünür ve dosyayı seçebilirsiniz veya seçimini kaldırabilirsiniz. Seçiliyken, Kod Kapsamı Çözümle'yi her seçtiğiniz zaman **çalıştırma ayarları dosyası uygulanır.**
::: moniker-end

::: moniker range=">=vs-2019"

### <a name="visual-studio-2019-version-164-and-later"></a>Visual Studio 2019 sürüm 16.4 ve sonrası

2019 sürüm 16.4 ve Visual Studio çalıştırma ayarları dosyası belirtmenin üç yolu vardır.

- [Çalıştırma ayarlarını otomatik olarak algılama](#autodetect-the-run-settings-file)
- [Çalıştırma ayarlarını el ile ayarlama](#manually-select-the-run-settings-file)
- [Derleme özelliği ayarlama](#set-a-build-property)

#### <a name="autodetect-the-run-settings-file"></a>Çalıştırma ayarları dosyasını otomatik olarak algılama

> [!NOTE]
> Bu yalnızca adlı bir dosya için `.runsettings` çalışır.

Çalıştırma ayarları dosyasını otomatik olarak algılamak için bunu çözümünün köküne yer değiştirin.

Çalıştırma ayarları dosyalarının otomatik olarak algılanması etkinleştirilirse, bu dosyada yer alan ayarlar tüm test çalıştırmalarında uygulanır. Runsettings dosyalarının otomatik algılama özelliğini iki yöntem kullanarak açabilirsiniz:

- Araç **Seçenekleri** > **Test** > **Otomatik** Algılama > **Runsettings Dosyalarını Seçme**

   ![Visual Studio'da runsettings dosyasını otomatik algıla seçeneği](media/auto-detect-runsettings-tools-window.png)

- Runsettings  > **Dosyalarını Otomatik Algıla Ayarlar** > **Test Çalıştır'ı seçin**

   ![Çalışma menüsünde runsettings dosya menüsünü otomatik Visual Studio](media/auto-detect-runsettings-menu.png)

#### <a name="manually-select-the-run-settings-file"></a>Çalıştırma ayarları dosyasını el ile seçin

IDE'de,  Çalıştırmayı Sına'Ayarlar Çözüm Genelinde runsettings Dosyasını Seçin'i >  > **ve** *ardından .runsettings dosyasını* seçin.

- Bu dosya, varsa çözümün kökünde yer alan *.runsettings* dosyasını geçersiz kılar ve tüm test çalıştırmaları için uygulanır.
- Bu dosya seçimi yalnızca yerel olarak kalıcıdır.

![Uygulama menüsünde çözüm genelinde test runsettings dosya menüsünü Visual Studio](media/select-solution-settings-file.png)

#### <a name="set-a-build-property"></a>Derleme özelliği ayarlama

Proje dosyası veya Directory.Build.props dosyası aracılığıyla projeye derleme özelliği ekleyin. Bir projenin çalıştırma ayarları dosyası **RunSettingsFilePath özelliği tarafından belirtilir.**

- Project düzey çalıştırma ayarları şu anda C#, VB, C++ ve F# projelerinde de desteklemektedir.
- Proje için belirtilen bir dosya, çözümde belirtilen diğer çalıştırma ayarları dosyasını geçersiz kılar.
- [Bu MSBuild,](../msbuild/msbuild-reserved-and-well-known-properties.md) runsettings dosyasının yolunu belirtmek için kullanılabilir.

Bir proje için *.runsettings* dosyası belirtme örneği:

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RunSettingsFilePath>$(MSBuildProjectDirectory)\example.runsettings</RunSettingsFilePath>
  </PropertyGroup>
  ...
</Project>
```

### <a name="visual-studio-2019-version-163-and-earlier"></a>Visual Studio 2019 sürüm 16.3 ve önceki sürümler

IDE'de bir çalıştırma ayarları dosyası belirtmek için Test Seç'i **Ayarlar**  >  **seçin.** *.runsettings* dosyasına gidin ve dosyayı seçin.

![Visual Studio 2019'da test ayarları dosya menüsünü seçin](media/vs-2019/select-settings-file.png)

Dosya Test menüsünde görünür ve dosyayı seçebilirsiniz veya seçimini kaldırabilirsiniz. Seçiliyken, Kod Kapsamı Çözümle'yi her seçtiğiniz zaman **çalıştırma ayarları dosyası uygulanır.**
::: moniker-end

## <a name="specify-a-run-settings-file-from-the-command-line"></a>Komut satırına bir çalıştırma ayarları dosyası belirtme

Testleri komut satırdan çalıştırmak içinvstest.console.exe *kullanın* ve **/Ayarlar parametresini kullanarak ayarlar dosyasını** belirtin.

1. için [Geliştirici Komut İstemi'Visual Studio.](../ide/reference/command-prompt-powershell.md)

2. Aşağıdakine benzer bir komut girin:

   ```cmd
   vstest.console.exe MyTestAssembly.dll /EnableCodeCoverage /Settings:CodeCoverage.runsettings
   ```

   veya

   ```cmd
   vstest.console.exe --settings:test.runsettings test.dll
   ```

Daha fazla bilgi için [bkz.VSTest.Console.exe komut satırı seçenekleri.](vstest-console-options.md)

## <a name="the-runsettings-file"></a>*.runsettings dosyası

*.runsettings dosyası, **RunSettings** öğesi içinde farklı yapılandırma öğeleri içeren bir XML dosyasıdır. Aşağıdaki bölümler farklı öğeleri ayrıntılı olarak açıklar. Tam bir örnek için [bkz. Örnek *.runsettings dosyası.](#example-runsettings-file)

```xml
<?xml version="1.0" encoding="utf-8"?>
<RunSettings>
  <!-- configuration elements -->
</RunSettings>
```

Yapılandırma öğelerinin her biri, varsayılan bir değere sahip olduğundan isteğe bağlıdır.

## <a name="runconfiguration-element"></a>RunConfiguration öğesi

```xml
<RunConfiguration>
    <MaxCpuCount>1</MaxCpuCount>
    <ResultsDirectory>.\TestResults</ResultsDirectory>
    <TargetPlatform>x86</TargetPlatform>
    <TargetFrameworkVersion>Framework40</TargetFrameworkVersion>
    <TestAdaptersPaths>%SystemDrive%\Temp\foo;%SystemDrive%\Temp\bar</TestAdaptersPaths>
    <TestSessionTimeout>10000</TestSessionTimeout>
    <TreatNoTestsAsError>true</TreatNoTestsAsError>
</RunConfiguration>
```

**RunConfiguration öğesi** aşağıdaki öğeleri içerebilir:

|Düğüm|Varsayılan|Değerler|
|-|-|-|
|**MaxCpuCount**|1|Bu ayar, makinede kullanılabilir çekirdekleri kullanarak birim testlerini çalıştırma sırasında paralel test yürütme derecesini kontrol eder. Test yürütme altyapısı, kullanılabilir her çekirdekte ayrı bir işlem olarak başlar ve her çekirdek için çalıştıracak testleri olan bir kapsayıcı verir. Kapsayıcı bir derleme, DLL veya ilgili yapıt olabilir. Test kapsayıcısı zamanlama birimidir. Her kapsayıcıda testler test çerçevesine göre sınanır. Çok sayıda kapsayıcı varsa, işlemler bir kapsayıcıda testleri yürütmeyi tamamlar ve bu kapsayıcılara bir sonraki kullanılabilir kapsayıcı verilir.<br /><br />MaxCpuCount şu şekilde olabilir:<br /><br />n, burada 1 <= n <= çekirdek sayısı: en fazla n işlem başlatıldı<br /><br />n, burada n = başka bir değer: başlatılan işlem sayısı kullanılabilir çekirdek sayısına kadar olabilir. Örneğin, platformun ortama göre başlatacak en uygun işlem sayısına otomatik olarak karar vermesine izin vermek için n=0 olarak ayarlayın.|
|**ResultsDirectory**||Test sonuçlarının yerleştiril olduğu dizin. Yol, .runsettings dosyasını içeren dizine göredir.|
|**TargetFrameworkVersion**|Framework40|`FrameworkCore10`.NET Core kaynakları için, UWP tabanlı kaynaklar `FrameworkUap10` için, `Framework45` .NET Framework 4.5 ve üst için, `Framework40` .NET Framework 4.0 ve `Framework35` .NET Framework 3.5 için.<br /><br />Bu ayar, testleri bulmak ve yürütmek için kullanılan birim testi çerçevesinin sürümünü belirtir. Birim test projesinin yapı özelliklerinde belirttiğiniz .NET platformu sürümünden farklı olabilir.<br /><br />`TargetFrameworkVersion` *.runsettings* dosyasından öğesini atlarsanız platform, yerleşik ikili dosyaları temel alarak çerçeve sürümünü otomatik olarak belirler.|
|**Targetplatform**|x86|x86, x64|
|**TreatTestAdapterErrorsAsWarnings**|yanlış|yanlış, doğru|
|**TestAdaptersPaths**||TestAdapter'ların bulunduğu dizine bir veya daha fazla yol|
|**TestSessionTimeout**||Kullanıcıların belirli bir zaman aşımını aşarak bir test oturumunu sonlandırmasına izin verir. Zaman aşımı ayarlamak kaynakların iyi tüketildiğinden ve test oturumlarının ayarlanmış bir süreyle kısıtlanmış olduğunu sağlar. Bu ayar **2017 Visual Studio 15.5 ve sonraki sürümlerde** kullanılabilir.|
|**DotnetHostPath**||Testhost'u çalıştırmak için kullanılan dotnet ana bilgisayarının özel yolunu belirtin. Bu, örneğin dotnet/runtime deposunu derlemek için kendi dotnet'inizi derlemeniz için kullanışlıdır. Bu seçeneğin belirterek her zaman testhost.exe arama atlar ve her zaman testhost.dll.|
|**TreatNoTestsAsError**|yanlış| true veya false <br>Hiçbir test keşfedilmezseniz çıkış kodunu tanımlayan bir Boole değeri belirtin. Değer ise ve `true` test yoksa sıfır olmayan bir çıkış kodu döndürülür. Aksi takdirde sıfır döndürülür.|

## <a name="datacollectors-element-diagnostic-data-adapters"></a>DataCollectors öğesi (tanılama veri bağdaştırıcıları)

**DataCollectors öğesi,** tanılama veri bağdaştırıcılarının ayarlarını belirtir. Tanılama veri bağdaştırıcıları, test kapsamındaki ortam ve uygulama hakkında ek bilgi toplar. Her bağdaştırıcının varsayılan ayarları vardır ve yalnızca varsayılanları kullanmak istemiyorsanız ayarları sağlayabilirsiniz.

```xml
<DataCollectionRunSettings>
  <DataCollectors>
    <!-- data collectors -->
  </DataCollectors>
</DataCollectionRunSettings>
```

### <a name="codecoverage-data-collector"></a>CodeCoverage veri toplayıcısı

Kod kapsamı veri toplayıcısı uygulama kodu bölümlerinin testte uygulandığı bir günlük oluşturur. Kod kapsamı ayarlarını özelleştirme hakkında ayrıntılı bilgi için bkz. Kod kapsamı [analizini özelleştirme.](../test/customizing-code-coverage-analysis.md)

```xml
<DataCollector friendlyName="Code Coverage" uri="datacollector://Microsoft/CodeCoverage/2.0" assemblyQualifiedName="Microsoft.VisualStudio.Coverage.DynamicCoverageDataCollector, Microsoft.VisualStudio.TraceCollector, Version=11.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a">
  <Configuration>
    <CodeCoverage>
      <ModulePaths>
        <Exclude>
          <ModulePath>.*CPPUnitTestFramework.*</ModulePath>
        </Exclude>
      </ModulePaths>

      <UseVerifiableInstrumentation>True</UseVerifiableInstrumentation>
      <AllowLowIntegrityProcesses>True</AllowLowIntegrityProcesses>
      <CollectFromChildProcesses>True</CollectFromChildProcesses>
      <CollectAspDotNet>False</CollectAspDotNet>
    </CodeCoverage>
  </Configuration>
</DataCollector>
```

### <a name="videorecorder-data-collector"></a>VideoRecorder veri toplayıcısı

Video veri toplayıcısı, testler çalıştırıldıkları zaman bir ekran kaydı yakalar. Bu kayıt, UI testlerinin sorunlarını gidermek için kullanışlıdır. Video veri toplayıcısı **2017 Visual Studio 15.5 ve sonraki sürümlerde** kullanılabilir. Bu veri toplayıcısını yapılandırma örneği için Örnek [*.runsettings dosyasına bakın.](#example-runsettings-file)

Diğer tanılama veri bağdaştırıcılarını özelleştirmek için bir test ayarları [dosyası kullanın.](../test/collect-diagnostic-information-using-test-settings.md)

### <a name="blame-data-collector"></a>Sorumlu veri toplayıcısı

Bu seçenek, test ana bilgisayarı kilitlenmesi neden olan sorunlu bir testi yalıtmanıza yardımcı olabilir. Toplayıcıyı çalıştırarak *TestResults**içinde kilitlenmeden* önce testin yürütme sırası yakalayan bir çıkış dosyası (Sequence.xml) oluşturur.

```xml
<DataCollector friendlyName="blame" enabled="True">
</DataCollector>
```

## <a name="testrunparameters"></a>TestRunParameters

```xml
<TestRunParameters>
    <Parameter name="webAppUrl" value="http://localhost" />
    <Parameter name="docsUrl" value="https://docs.microsoft.com" />
</TestRunParameters>
```

Test çalıştırması parametreleri, çalışma zamanında testlerde kullanılabilen değişkenleri ve değerleri tanımlamak için bir yol sağlar. MSTest özelliğini <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.Properties%2A?displayProperty=nameWithType> (veya NUnit [TestContext) kullanarak parametrelere erişin:](https://docs.nunit.org/articles/nunit/writing-tests/TestContext.html)

```csharp
private string _appUrl;
public TestContext TestContext { get; set; }

[TestMethod] // [Test] for NUnit
public void HomePageTest()
{
    string _appURL = TestContext.Properties["webAppUrl"];
}
```

Test çalıştırması parametrelerini kullanmak için test <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext> sınıfınıza genel bir özellik ekleyin.

## <a name="loggerrunsettings-element"></a>LoggerRunSettings öğesi

bölümü, `LoggerRunSettings` test çalıştırması için kullanılacak bir veya daha fazla günlük kullanıcı tanımlar. En yaygın günlük dosyaları konsol, Visual Studio Test Sonuçları Dosya (trx) ve html'tir.

```xml
<LoggerRunSettings>
    <Loggers>
      <Logger friendlyName="console" enabled="True">
        <Configuration>
            <Verbosity>quiet</Verbosity>
        </Configuration>
      </Logger>
      <Logger friendlyName="trx" enabled="True">
        <Configuration>
          <LogFileName>foo.trx</LogFileName>
        </Configuration>
      </Logger>
      <Logger friendlyName="html" enabled="True">
        <Configuration>
          <LogFileName>foo.html</LogFileName>
        </Configuration>
      </Logger>
    </Loggers>
  </LoggerRunSettings>
```

## <a name="mstest-element"></a>MSTest öğesi

Bu ayarlar, özniteliğine sahip test yöntemlerini çalıştıran test bağdaştırıcısına <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> özeldir.

```xml
<MSTest>
    <MapInconclusiveToFailed>True</MapInconclusiveToFailed>
    <CaptureTraceOutput>false</CaptureTraceOutput>
    <DeleteDeploymentDirectoryAfterTestRunIsComplete>False</DeleteDeploymentDirectoryAfterTestRunIsComplete>
    <DeploymentEnabled>False</DeploymentEnabled>
    <AssemblyResolution>
      <Directory path="D:\myfolder\bin\" includeSubDirectories="false"/>
    </AssemblyResolution>
</MSTest>
```

|Yapılandırma|Varsayılan|Değerler|
|-|-|-|
|**ForcedLegacyMode**|yanlış|2012 Visual Studio de MSTest bağdaştırıcısı daha hızlı ve daha ölçeklenebilir hale gelecek şekilde optimize edilmiştir. Testlerin çalışma sırası gibi bazı davranışlar Visual Studio'nun önceki sürümlerindekiyle aynı olmayabilir. Eski test bağdaştırıcısını **kullanmak için bu** değeri true olarak ayarlayın.<br /><br />Örneğin, birim testi için belirtilen birapp.config *varsa* bu ayarı kullanabilirsiniz.<br /><br />Daha yeni bağdaştırıcı kullanmanıza olanak vermek için testlerinizi yeniden düzenlemenizi öneririz.|
|**IgnoreTestImpact**|yanlış|Test etkisi özelliği, MSTest'te veya Microsoft Test Yöneticisi'da (2017'de kullanım dışı) çalıştırıldıklarında son değişikliklerden etkilenen testleri Visual Studio öncelik sırasına alır. Bu ayar özelliği devre dışı bırakır. Daha fazla bilgi için [bkz. Önceki derlemeden bu yana hangi testlerin çalışması gerektiği.](/previous-versions/dd286589(v=vs.140))|
|**SettingsFile**||Burada MSTest bağdaştırıcısıyla birlikte kullanmak üzere bir test ayarları dosyası belirtebilirsiniz. Ayarlar menüsünden bir test ayarları [dosyası da belirtebilirsiniz.](#specify-a-run-settings-file-in-the-ide)<br /><br />Bu değeri **belirtirsanız, ForcedLegacyMode** değerini de true olarak **ayarlay gerekir.**<br /><br />`<ForcedLegacyMode>true</ForcedLegacyMode>`|
|**KeepExecutorAliveAfterLegacyRun**|yanlış|Test çalıştırması tamamlandıktan sonra MSTest kapatılır. Testin bir parçası olarak başlatılan tüm işlemler de sonlandı. Test yürütücüslerini canlı tutmak için değerini true olarak **ayarlayın.** Örneğin, kodlanmış UI testleri arasında tarayıcıyı çalışır durumda tutmak için bu ayarı kullanabilirsiniz.|
|**DeploymentEnabled**|true|değeri false olarak **ayarlanırsa,** test yönteminde belirttiğiniz dağıtım öğeleri dağıtım dizinine kopyalanmaz.|
|**CaptureTraceOutput**|true|kullanarak test yönteminden hata ayıklama izlemesi <xref:System.Diagnostics.Trace.WriteLine%2A?displayProperty=nameWithType> yazabilir.|
|**DeleteDeploymentDirectoryAfterTestRunIsComplete**|true|Bir test çalıştırması sonrasında dağıtım dizinini korumak için bu değeri false olarak **ayarlayın.**|
|**MapInconclusiveToFailed**|yanlış|Bir test sonlu bir durumla tamamlanırsa, Test Gezgini'nde atlanan **durumla eşlenmiş olur.** Sonlu testlerin başarısız olarak gösternsin, değerini true olarak **ayarlayın.**|
|**InProcMode**|yanlış|Testlerinizi MSTest bağdaştırıcısıyla aynı işlemde çalıştırmak için bu değeri true olarak **ayarlayın.** Bu ayar, küçük bir performans kazancı sağlar. Ancak bir test özel durumla birlikte çıkarsa kalan testler çalışmaz.|
|**AssemblyResolution**|yanlış|Birim testlerini bulma ve çalıştırmada ek derlemelerin yollarını belirterek. Örneğin, test derlemesi ile aynı dizinde olmayan bağımlılık derlemeleri için bu yolları kullanın. Bir yol belirtmek için dizin yolu **öğesi** kullanın. Yollar ortam değişkenlerini içerebilir.<br /><br />`<AssemblyResolution>  <Directory path="D:\myfolder\bin\" includeSubDirectories="false"/> </AssemblyResolution>`|

## <a name="example-runsettings-file"></a>Örnek *.runsettings* dosyası

Aşağıdaki XML, tipik bir *.runsettings dosyasının içeriğini* gösterir. Bu kodu kopyalayın ve ihtiyaçlarınıza uyacak şekilde düzenleyin.

Dosyanın her öğesi, varsayılan bir değere sahip olduğundan isteğe bağlıdır.

```xml
<?xml version="1.0" encoding="utf-8"?>
<RunSettings>
  <!-- Configurations that affect the Test Framework -->
  <RunConfiguration>
    <MaxCpuCount>1</MaxCpuCount>
    <!-- Path relative to directory that contains .runsettings file-->
    <ResultsDirectory>.\TestResults</ResultsDirectory>

    <!-- x86 or x64 -->
    <!-- You can also change it from the Test menu; choose "Processor Architecture for AnyCPU Projects" -->
    <TargetPlatform>x86</TargetPlatform>

    <!-- Framework35 | [Framework40] | Framework45 -->
    <TargetFrameworkVersion>Framework40</TargetFrameworkVersion>

    <!-- Path to Test Adapters -->
    <TestAdaptersPaths>%SystemDrive%\Temp\foo;%SystemDrive%\Temp\bar</TestAdaptersPaths>

    <!-- TestSessionTimeout was introduced in Visual Studio 2017 version 15.5 -->
    <!-- Specify timeout in milliseconds. A valid value should be greater than 0 -->
    <TestSessionTimeout>10000</TestSessionTimeout>

    <!-- true or false -->
    <!-- Value that specifies the exit code when no tests are discovered -->
    <TreatNoTestsAsError>true</TreatNoTestsAsError>
  </RunConfiguration>

  <!-- Configurations for data collectors -->
  <DataCollectionRunSettings>
    <DataCollectors>
      <DataCollector friendlyName="Code Coverage" uri="datacollector://Microsoft/CodeCoverage/2.0" assemblyQualifiedName="Microsoft.VisualStudio.Coverage.DynamicCoverageDataCollector, Microsoft.VisualStudio.TraceCollector, Version=11.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a">
        <Configuration>
          <CodeCoverage>
            <ModulePaths>
              <Exclude>
                <ModulePath>.*CPPUnitTestFramework.*</ModulePath>
              </Exclude>
            </ModulePaths>

            <!-- We recommend you do not change the following values: -->
            <UseVerifiableInstrumentation>True</UseVerifiableInstrumentation>
            <AllowLowIntegrityProcesses>True</AllowLowIntegrityProcesses>
            <CollectFromChildProcesses>True</CollectFromChildProcesses>
            <CollectAspDotNet>False</CollectAspDotNet>

          </CodeCoverage>
        </Configuration>
      </DataCollector>

      <DataCollector uri="datacollector://microsoft/VideoRecorder/1.0" assemblyQualifiedName="Microsoft.VisualStudio.TestTools.DataCollection.VideoRecorder.VideoRecorderDataCollector, Microsoft.VisualStudio.TestTools.DataCollection.VideoRecorder, Version=15.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a" friendlyName="Screen and Voice Recorder">
        <!--Video data collector was introduced in Visual Studio 2017 version 15.5 -->
        <Configuration>
          <!-- Set "sendRecordedMediaForPassedTestCase" to "false" to add video attachments to failed tests only -->
          <MediaRecorder sendRecordedMediaForPassedTestCase="true"  xmlns="">           
            <ScreenCaptureVideo bitRate="512" frameRate="2" quality="20" />
          </MediaRecorder>
        </Configuration>
      </DataCollector>

      <!-- Configuration for blame data collector -->
      <DataCollector friendlyName="blame" enabled="True">
      </DataCollector>

    </DataCollectors>
  </DataCollectionRunSettings>

  <!-- Parameters used by tests at run time -->
  <TestRunParameters>
    <Parameter name="webAppUrl" value="http://localhost" />
    <Parameter name="webAppUserName" value="Admin" />
    <Parameter name="webAppPassword" value="Password" />
  </TestRunParameters>

  <!-- Configuration for loggers -->
  <LoggerRunSettings>
    <Loggers>
      <Logger friendlyName="console" enabled="True">
        <Configuration>
            <Verbosity>quiet</Verbosity>
        </Configuration>
      </Logger>
      <Logger friendlyName="trx" enabled="True">
        <Configuration>
          <LogFileName>foo.trx</LogFileName>
        </Configuration>
      </Logger>
      <Logger friendlyName="html" enabled="True">
        <Configuration>
          <LogFileName>foo.html</LogFileName>
        </Configuration>
      </Logger>
      <Logger friendlyName="blame" enabled="True" />
    </Loggers>
  </LoggerRunSettings>

  <!-- Adapter Specific sections -->

  <!-- MSTest adapter -->
  <MSTest>
    <MapInconclusiveToFailed>True</MapInconclusiveToFailed>
    <CaptureTraceOutput>false</CaptureTraceOutput>
    <DeleteDeploymentDirectoryAfterTestRunIsComplete>False</DeleteDeploymentDirectoryAfterTestRunIsComplete>
    <DeploymentEnabled>False</DeploymentEnabled>
    <AssemblyResolution>
      <Directory path="D:\myfolder\bin\" includeSubDirectories="false"/>
    </AssemblyResolution>
  </MSTest>

</RunSettings>
```

## <a name="specify-environment-variables-in-the-runsettings-file"></a>*.runsettings dosyasında ortam değişkenlerini* belirtme

Ortam değişkenleri, test ana bilgisayarıyla doğrudan etkileşime girebilen *. runsettings* dosyasında ayarlanabilir. *. Runsettings* dosyasında ortam değişkenlerinin belirtilmesi, *DOTNET_ROOT* gibi ortam değişkenlerinin ayarlanmasını gerektiren önemsiz olmayan projeleri desteklemek için gereklidir. Bu değişkenler, test ana bilgisayarı işlemini oluşturma sırasında ayarlanır ve konakta kullanılabilir.

### <a name="example"></a>Örnek

Aşağıdaki kod, ortam değişkenlerini geçiren örnek bir *. runsettings* dosyasıdır:

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- File name extension must be .runsettings -->
<RunSettings>
  <RunConfiguration>
    <EnvironmentVariables>
      <!-- List of environment variables we want to set-->
      <DOTNET_ROOT>C:\ProgramFiles\dotnet</DOTNET_ROOT>
      <SDK_PATH>C:\Codebase\Sdk</SDK_PATH>
    </EnvironmentVariables>
  </RunConfiguration>
</RunSettings>
```

**RunConfiguration** düğümü bir **EnvironmentVariables** düğümü içermelidir. Bir ortam değişkeni, öğe adı ve değeri olarak belirtilebilir.

> [!NOTE]
> Bu ortam değişkenleri, test ana bilgisayarı başlatıldığında her zaman ayarlanması gerektiğinden, testlerin her zaman ayrı bir işlemde çalışması gerekir. Bunun için, test ana bilgisayarının her zaman çağrılması için ortam değişkenleri olduğunda */ınısolation* bayrağı ayarlanır.

## <a name="see-also"></a>Ayrıca bkz.

- [Test çalıştırması yapılandırma](https://github.com/microsoft/vstest-docs/blob/master/docs/configure.md)
- [Kod kapsamı analizini özelleştirme](../test/customizing-code-coverage-analysis.md)
- [Visual Studio test görevi (Azure Test Plans)](/azure/devops/pipelines/tasks/test/vstest?view=vsts&preserve-view=true)
