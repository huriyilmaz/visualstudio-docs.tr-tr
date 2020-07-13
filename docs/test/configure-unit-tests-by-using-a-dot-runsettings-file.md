---
title: Bir. runsettings dosyası ile birim testlerini yapılandırma
ms.date: 10/03/2019
ms.topic: how-to
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: e03400cf916319f963457af5740139bc88fc5105
ms.sourcegitcommit: 5e82a428795749c594f71300ab03a935dc1d523b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2020
ms.locfileid: "86211605"
---
# <a name="configure-unit-tests-by-using-a-runsettings-file"></a>*. Runsettings* dosyasını kullanarak birim testlerini yapılandırma

Visual Studio 'daki birim testleri, bir *. runsettings* dosyası kullanılarak yapılandırılabilir. Örneğin, testlerin çalıştırıldığı .NET sürümünü, test sonuçlarının dizinini veya bir test çalıştırması sırasında toplanan verileri değiştirebilirsiniz.

Çalışma ayarları dosyaları isteğe bağlıdır. Özel yapılandırma gerekmiyorsa *. runsettings* dosyasına ihtiyacınız yoktur. *. Runsettings* dosyasının ortak kullanımı, [kod kapsamı analizini](../test/customizing-code-coverage-analysis.md)özelleştirecek.

## <a name="specify-a-run-settings-file"></a>Çalışma ayarları dosyası belirtin

Çalışma ayarları dosyaları, [komut satırından](vstest-console-options.md), IDE 'de veya Azure test Plans ya da Team FOUNDATION Server (TFS) kullanarak bir [derleme iş akışında](/azure/devops/pipelines/test/getting-started-with-continuous-testing?view=vsts) çalıştırılan testleri yapılandırmak için kullanılabilir.

### <a name="ide"></a>IDE

::: moniker range="vs-2017"

IDE 'de bir çalıştırma ayarları dosyası belirtmek **için test** > **testi ayarları** > **Test ayarları dosyasını seçin**ve ardından *. runsettings* dosyasını seçin.

![Visual Studio 2017 'de test ayarları Dosya menüsünü seçin](media/select-test-settings-file.png)

Dosya, test ayarları menüsünde görünür ve onu seçebilir veya seçimden kaldırabilirsiniz. Seçildiğinde, çalışma ayarları dosyası **kod kapsamını çözümle**' yi seçtiğiniz her seferinde geçerlidir.

::: moniker-end

::: moniker range=">=vs-2019"

#### <a name="visual-studio-2019-version-163-and-earlier"></a>Visual Studio 2019 sürüm 16,3 ve önceki sürümleri

IDE 'de bir çalıştırma ayarları dosyası belirtmek için **Test**  >  **seçme ayarları dosyası**' nı seçin. *. Runsettings* dosyasına gidin ve seçin.

![Visual Studio 2019 'de test ayarları Dosya menüsünü seçin](media/vs-2019/select-settings-file.png)

Dosya, Test menüsünde görünür ve onu seçebilir veya seçimden kaldırabilirsiniz. Seçildiğinde, çalışma ayarları dosyası **kod kapsamını çözümle**' yi seçtiğiniz her seferinde geçerlidir.

#### <a name="visual-studio-2019-version-164-and-later"></a>Visual Studio 2019 sürüm 16,4 ve üzeri

Visual Studio 2019 sürüm 16,4 ve sonrasında bir çalıştırma ayarları dosyası belirtmenin üç yolu vardır:

- Proje dosyası ya da bir dizin. Build. props dosyası aracılığıyla bir projeye yapı özelliği ekleyin. Bir projenin çalıştırma ayarları dosyası **Runsettingsfilepath**özelliği tarafından belirtilir.

    - Proje düzeyi çalışma ayarları şu anda C#, VB, C++ ve F # projelerinde destekleniyor.
    - Bir proje için belirtilen dosya, çözümde belirtilen diğer çalışma ayarları dosyalarını geçersiz kılar.
    - [Bu MSBuild özellikleri](https://docs.microsoft.com/visualstudio/msbuild/msbuild-reserved-and-well-known-properties?view=vs-2019) , runsettings dosyasının yolunu belirtmek için kullanılabilir. 

    Bir proje için *. runsettings* dosyası belirtme örneği:
    
    ```xml
    <Project Sdk="Microsoft.NET.Sdk">
      <PropertyGroup>
        <RunSettingsFilePath>$(MSBuildProjectDirectory)\example.runsettings</RunSettingsFilePath>
      </PropertyGroup>
      ...
    </Project>
    ```

- Çözümünüzün köküne *. runsettings* adlı bir çalışma ayarları dosyası yerleştirin.

  Çalışma ayarları dosyalarının otomatik algılanması etkinleştirilirse, bu dosyadaki ayarlar tüm testler üzerinde uygulanır. Runsettings dosyalarını iki konumdan otomatik algılamayı açabilirsiniz:
  
    - **Araçlar** > **Seçenekler** > **Test et** > **Runsettings dosyalarını otomatik algıla**

      ![Visual Studio 2019 'de runsettings dosya seçeneğini otomatik algıla](media/vs-2019/auto-detect-runsettings-tools-window.png)
      
    - **Test et** > **Çalıştırma ayarlarını yapılandır** > **Runsettings dosyalarını otomatik algıla**
    
      ![Visual Studio 2019 'de runsettings Dosya menüsünü otomatik algıla](media/vs-2019/auto-detect-runsettings-menu.png)

- IDE 'de **Test** > **Çalıştır ayarlarını yapılandır** > **çözüm genelindeki runsettings dosyasını**seçin ve ardından *. runsettings* dosyasını seçin.

   ![Visual Studio 2019 'de çözüm genelinde çalışma ayarları Dosya menüsünü seçin](media/vs-2019/select-solution-settings-file.png)
      
   - Bu dosya, varsa çözümün kökündeki ". runsettings" dosyasını geçersiz kılar ve tüm testler üzerinde uygulanır.  
   - Bu dosya seçimi yalnızca yerel olarak devam ettirir. 

::: moniker-end

### <a name="command-line"></a>Komut satırı

Komut satırından testleri çalıştırmak için *vstest.console.exe*kullanın ve **/Settings** parametresini kullanarak ayarlar dosyasını belirtin.

1. Visual Studio Geliştirici Komut Satırını başlatın:

   ::: moniker range="vs-2017"

   Windows **Başlat** menüsünde, vs 2017 için **Visual Studio 2017** > **Geliştirici komut istemi**seçin.

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   Windows **Başlat** menüsünde, vs 2019 için **Visual Studio 2019** > **Geliştirici komut istemi**seçin.

   ::: moniker-end

2. Şuna benzer bir komut girin:

   ```cmd
   vstest.console.exe MyTestAssembly.dll /EnableCodeCoverage /Settings:CodeCoverage.runsettings
   ```

   veya

   ```cmd
   vstest.console.exe --settings:test.runsettings test.dll
   ```

Daha fazla bilgi için bkz. [VSTest.Console.exe komut satırı seçenekleri](vstest-console-options.md).

## <a name="customize-tests"></a>Testleri özelleştirme

Testlerinizi bir *. runsettings* dosyası kullanarak özelleştirmek için şu adımları izleyin:

1. Visual Studio çözümünüze bir XML dosyası ekleyin ve bunu *test. runsettings*olarak kaydedin.

   > [!TIP]
   > Dosya adı, *. runsettings*uzantısını kullandığınız sürece büyük değildir.

2. Dosya içeriğini izleyen örnekteki XML ile değiştirin ve gerektiği gibi özelleştirin.

::: moniker range="vs-2017"

3. **Test** menüsünde test **ayarları**  >  **Test ayarları dosyasını seçin**. Oluşturduğunuz *. runsettings* dosyasına gidin ve ardından **Tamam**' ı seçin.

::: moniker-end

::: moniker range=">=vs-2019"

3. Çalışma ayarları dosyasını seçmek için **Test**  >  **seçme ayarları dosyası**' nı seçin. Oluşturduğunuz *. runsettings* dosyasına gidin ve ardından **Tamam**' ı seçin.

::: moniker-end

   > [!TIP]
   > Çözümünüzde birden fazla *. runsettings* dosyası oluşturabilir ve gerektiğinde etkin test ayarları dosyası olarak bir tane seçebilirsiniz.

## <a name="example-runsettings-file"></a>Örnek *. runsettings* dosyası

Aşağıdaki XML, tipik bir *. runsettings* dosyasının içeriğini gösterir. Varsayılan bir değere sahip olduğundan, dosyanın her bir öğesi isteğe bağlıdır.

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

## <a name="elements-of-a-runsettings-file"></a>*. Runsettings* dosyasının öğeleri

İzleyen bölümler *. runsettings* dosyasının öğelerini ayrıntılandırır.

### <a name="run-configuration"></a>Yapılandırmayı Çalıştır

```xml
<RunConfiguration>
    <MaxCpuCount>1</MaxCpuCount>
    <ResultsDirectory>.\TestResults</ResultsDirectory>
    <TargetPlatform>x86</TargetPlatform>
    <TargetFrameworkVersion>Framework40</TargetFrameworkVersion>
    <TestAdaptersPaths>%SystemDrive%\Temp\foo;%SystemDrive%\Temp\bar</TestAdaptersPaths>
    <TestSessionTimeout>10000</TestSessionTimeout>
</RunConfiguration>
```

**RunConfiguration** öğesi aşağıdaki öğeleri içerebilir:

|Düğüm|Varsayılan|Değerler|
|-|-|-|
|**ResultsDirectory**||Test sonuçlarının yerleştirildiği dizin.|
|**TargetFrameworkVersion**|Framework40|`FrameworkCore10`.NET Core kaynakları için, `FrameworkUap10` UWP tabanlı kaynaklar için, `Framework45` .NET Framework 4,5 ve üzeri için, `Framework40` .NET Framework 4,0 ve `Framework35` .NET Framework 3,5 için.<br /><br />Bu ayar, testleri keşfetmek ve yürütmek için kullanılan birim test çerçevesinin sürümünü belirtir. Birim test projesinin yapı özelliklerinde belirttiğiniz .NET platformu sürümünden farklı olabilir.<br /><br />`TargetFrameworkVersion` *. Runsettings* dosyasındaki öğeyi atlarsanız, platform otomatik olarak oluşturulan ikili dosyaları temel alan çerçeve sürümünü belirler.|
|**TargetPlatform**|x86|x86, x64|
|**Treattestadaptererrorsasuyarılar**|yanlış|yanlış, doğru|
|**TestAdaptersPaths**||TestAdapters 'nin bulunduğu dizine ait bir veya daha fazla yol|
|**MaxCpuCount**|1|Bu ayar, makinedeki kullanılabilir çekirdekleri kullanarak birim testlerini çalıştırırken paralel test yürütme derecesini denetler. Test yürütme altyapısı, kullanılabilir her çekirdek üzerinde ayrı bir işlem olarak başlar ve her bir çekirdeğe, testlerin çalışmasına sahip bir kapsayıcı verir. Kapsayıcı bir derleme, DLL veya ilgili yapıt olabilir. Sınama kapsayıcısı zamanlama birimidir. Her kapsayıcıda testler, test çerçevesine göre çalıştırılır. Birçok kapsayıcı varsa, süreçler bir kapsayıcıda testlerin yürütülmesi tamamlandığında, bir sonraki kullanılabilir kapsayıcıya verilirler.<br /><br />MaxCpuCount şu olabilir:<br /><br />n, burada 1 <= n <= çekirdek sayısı: en fazla n işlem başlatıldı<br /><br />n, burada n = diğer herhangi bir değer: başlatılan işlem sayısı kullanılabilir çekirdek sayısına kadar olabilir. Örneğin, n = 0 ' ı, platformun ortama göre başlatılacak en iyi işlem sayısına otomatik olarak karar vermesini sağlamak için ayarlayın.|
|**TestSessionTimeout**||Belirli bir zaman aşımını aştığında kullanıcıların bir test oturumunu sonlanmasına izin verir. Bir zaman aşımı ayarlamak, kaynakların iyi şekilde tüketilmesini ve test oturumlarının bir ayarlama zamanına göre kısıtlanmasını sağlar. Bu ayar, **Visual Studio 2017 sürüm 15,5** ve sonraki sürümlerinde kullanılabilir.|
|**Dotnewthostpath**||Testhost çalıştırmak için kullanılan DotNet konağının özel yolunu belirtin. Bu, DotNet/Runtime deposunu oluştururken kendi DotNet 'nizi oluştururken kullanışlıdır. Bu seçeneğin belirtilmesi testhost.exe arama işlemini atlar ve testhost.dll her zaman kullanır. 

### <a name="diagnostic-data-adapters-data-collectors"></a>Tanılama veri bağdaştırıcıları (veri toplayıcıları)

**Datatoplayıcıları** öğesi, tanılama veri bağdaştırıcılarının ayarlarını belirtir. Tanılama veri bağdaştırıcıları, ortam ve test edilen uygulama hakkında ek bilgiler toplar. Her bağdaştırıcı varsayılan ayarlara sahiptir ve yalnızca varsayılan değerleri kullanmak istemiyorsanız ayarları sağlamanız gerekir.

#### <a name="code-coverage-adapter"></a>Kod kapsamı bağdaştırıcısı

```xml
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
```

Kod kapsamı veri toplayıcısı uygulama kodu bölümlerinin testte uygulandığı bir günlük oluşturur. Kod kapsamının ayarlarını özelleştirme hakkında daha fazla bilgi için bkz. [kod kapsamı analizini özelleştirme](../test/customizing-code-coverage-analysis.md).

#### <a name="video-data-collector"></a>Video veri toplayıcısı

Video veri toplayıcısı, testler çalıştırıldığında bir ekran kaydını yakalar. Bu kayıt, UI testlerinin sorunlarını gidermek için kullanışlıdır. Video veri toplayıcısı, **Visual Studio 2017 sürüm 15,5** ve sonraki sürümlerinde kullanılabilir.

Diğer herhangi bir tanılama veri bağdaştırıcısı türünü özelleştirmek için, bir [Test ayarları dosyası](../test/collect-diagnostic-information-using-test-settings.md)kullanın.


### <a name="blame-data-collector"></a>Blame veri toplayıcısı

```xml
<DataCollector friendlyName="blame" enabled="True">
</DataCollector>
```

Bu seçenek, test ana bilgisayarı kilitlenmesine neden olan sorunlu bir testi yalıtmanıza yardımcı olabilir. Toplayıcıyı *çalıştırmak, test*eden bir çıkış dosyası (*Sequence.xml*) oluşturur ve bu, kilitlenmeden önce testin yürütülme sırasını yakalar. 

### <a name="testrunparameters"></a>TestRunParameters

```xml
<TestRunParameters>
    <Parameter name="webAppUrl" value="http://localhost" />
    <Parameter name="docsUrl" value="https://docs.microsoft.com" />
</TestRunParameters>
```

Test çalıştırması parametreleri, çalışma zamanında testlerin kullanabileceği değişkenleri ve değerleri tanımlamak için bir yol sağlar. Özelliği kullanarak parametrelere erişin <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.Properties%2A?displayProperty=nameWithType> :

```csharp
[TestMethod]
public void HomePageTest()
{
    string appURL = TestContext.Properties["webAppUrl"];
}
```

Test çalıştırması parametrelerini kullanmak için, <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext> Test sınıfınız için bir özel alan ve bir ortak <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext> özellik ekleyin.

### <a name="logger-run-settings"></a>Günlükçü çalışma ayarları

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

Bu `LoggerRunSettings` bölüm, test çalıştırması için kullanılacak bir veya daha fazla günlüğe kaydetme tanımlar. En yaygın günlüğe kaydetme cihazları konsol, TRX ve HTML 'dir. 

### <a name="mstest-run-settings"></a>MSTest çalıştırma ayarları

```xml
<MSTest>
    <MapInconclusiveToFailed>True</MapInconclusiveToFailed>
    <CaptureTraceOutput>false</CaptureTraceOutput>
    <DeleteDeploymentDirectoryAfterTestRunIsComplete>False</DeleteDeploymentDirectoryAfterTestRunIsComplete>
    <DeploymentEnabled>False</DeploymentEnabled>
    <AssemblyResolution>
      <Directory Path="D:\myfolder\bin\" includeSubDirectories="false"/>
    </AssemblyResolution>
</MSTest>
```

Bu ayarlar, özniteliğine sahip test yöntemlerini çalıştıran test bağdaştırıcısına özgüdür <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> .

|Yapılandırma|Varsayılan|Değerler|
|-|-|-|
|**ForcedLegacyMode**|yanlış|Visual Studio 2012 ' de, MSTest bağdaştırıcısı daha hızlı ve daha ölçeklenebilir hale getirmek için iyileştirildi. Testlerin çalışma sırası gibi bazı davranışlar Visual Studio'nun önceki sürümlerindekiyle aynı olmayabilir. Eski test bağdaştırıcısını kullanmak için bu değeri **true** olarak ayarlayın.<br /><br />Örneğin, birim testi için belirtilen bir *app.config* dosyanız varsa bu ayarı kullanabilirsiniz.<br /><br />Daha yeni bağdaştırıcı kullanmanıza olanak vermek için testlerinizi yeniden düzenlemenizi öneririz.|
|**IgnoreTestImpact**|yanlış|Test etkisi özelliği, son değişikliklerden etkilenen testleri, MSTest 'te veya Microsoft Test Yöneticisi (Visual Studio 2017 ' de kullanım dışı) çalıştırıldığında önceliklendirir. Bu ayar özelliği devre dışı bırakır. Daha fazla bilgi için bkz. [önceki bir derlemeden bu yana hangi testlerin çalıştırılması gerekir](https://msdn.microsoft.com/library/dd286589).|
|**SettingsFile**||Burada MSTest bağdaştırıcısıyla kullanılacak bir test ayarları dosyası belirtebilirsiniz. Ayrıca [, Ayarlar menüsünden](#ide)bir test ayarları dosyası belirtebilirsiniz.<br /><br />Bu değeri belirtirseniz, **Forcedlegacymode** öğesini de **true**olarak ayarlamanız gerekir.<br /><br />`<ForcedLegacyMode>true</ForcedLegacyMode>`|
|**KeepExecutorAliveAfterLegacyRun**|yanlış|Test çalıştırması tamamlandıktan sonra MSTest kapatılır. Testin bir parçası olarak başlatılan tüm işlemler de sonlandırıldı. Test yürütücüsünü canlı tutmak istiyorsanız, değeri **true**olarak ayarlayın. Örneğin, bu ayarı, tarayıcının kodlanmış UI testleri arasında çalışmasını sağlamak için kullanabilirsiniz.|
|**DeploymentEnabled**|true|Değeri **false**olarak ayarlarsanız, test yöntetiniz içinde belirttiğiniz dağıtım öğeleri dağıtım dizinine kopyalanmaz.|
|**CaptureTraceOutput**|true|Kullanarak test yönteminizin hata ayıklama izini yazabilirsiniz <xref:System.Diagnostics.Trace.WriteLine%2A?displayProperty=nameWithType> .|
|**DeleteDeploymentDirectoryAfterTestRunIsComplete**|true|Bir test çalıştırdıktan sonra dağıtım dizinini sürdürmek için bu değeri **false**olarak ayarlayın.|
|**MapInconclusiveToFailed**|yanlış|Bir test, Sonuçlandırılamayan bir durumla tamamlanırsa **Test Gezgini**'nde atlanan duruma eşlenir. Sonuçlandırılamayan testlerin başarısız olarak görüntülenmesini istiyorsanız değeri **true**olarak ayarlayın.|
|**InProcMode**|yanlış|Testlerinizin MSTest bağdaştırıcısıyla aynı işlemde çalıştırılmasını istiyorsanız, bu değeri **true**olarak ayarlayın. Bu ayar, küçük bir performans kazancı sağlar. Ancak bir test bir özel durumla çıkıldığında, kalan testler çalıştırılmaz.|
|**AssemblyResolution**|yanlış|Birim testlerini bulurken ve çalıştırırken ek derlemeler için yollar belirtebilirsiniz. Örneğin, test derlemesi ile aynı dizinde olmayan bağımlılık derlemeleri için bu yolları kullanın. Bir yol belirtmek için bir **Dizin yolu** öğesi kullanın. Yol, ortam değişkenleri içerebilir.<br /><br />`<AssemblyResolution>  <Directory Path="D:\myfolder\bin\" includeSubDirectories="false"/> </AssemblyResolution>`|

## <a name="specify-environment-variables-in-the-runsettings-file"></a>*. Runsettings* dosyasında ortam değişkenlerini belirtme

Ortam değişkenleri, test ana bilgisayarıyla doğrudan etkileşime girebilen *. runsettings* dosyasında ayarlanabilir. *. Runsettings* dosyasında ortam değişkenlerinin belirtilmesi, *DOTNET_ROOT*gibi ortam değişkenlerinin ayarlanmasını gerektiren önemsiz olmayan projeleri desteklemek için gereklidir. Bu değişkenler, test ana bilgisayarı işlemini oluşturma sırasında ayarlanır ve konakta kullanılabilir.

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
- [Visual Studio test görevi (Azure Test Plans)](/azure/devops/pipelines/tasks/test/vstest?view=vsts)

