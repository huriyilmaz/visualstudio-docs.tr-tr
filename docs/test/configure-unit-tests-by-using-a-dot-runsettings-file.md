---
title: Bir. runsettings dosyası ile birim testlerini yapılandırma
ms.date: 10/03/2019
ms.topic: conceptual
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 4f7d44482937eb80540314db37bc9c664eaab689
ms.sourcegitcommit: bf2e9d4ff38bf5b62b8af3da1e6a183beb899809
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/22/2020
ms.locfileid: "77557953"
---
# <a name="configure-unit-tests-by-using-a-runsettings-file"></a>*. Runsettings* dosyasını kullanarak birim testlerini yapılandırma

Visual Studio 'daki birim testleri, bir *. runsettings* dosyası kullanılarak yapılandırılabilir. Örneğin, testlerin çalıştırıldığı .NET sürümünü, test sonuçlarının dizinini veya bir test çalıştırması sırasında toplanan verileri değiştirebilirsiniz.

Çalışma ayarları dosyaları isteğe bağlıdır. Özel yapılandırma gerekmiyorsa *. runsettings* dosyasına ihtiyacınız yoktur. *. Runsettings* dosyasının ortak kullanımı, [kod kapsamı analizini](../test/customizing-code-coverage-analysis.md)özelleştirecek.

## <a name="specify-a-run-settings-file"></a>Çalışma ayarları dosyası belirtin

Çalışma ayarları dosyaları, [komut satırından](vstest-console-options.md), IDE 'de veya Azure test Plans ya da Team FOUNDATION Server (TFS) kullanarak bir [derleme iş akışında](/azure/devops/pipelines/test/getting-started-with-continuous-testing?view=vsts) çalıştırılan testleri yapılandırmak için kullanılabilir.

### <a name="ide"></a>IDE

::: moniker range="vs-2017"

IDE 'de bir çalıştırma ayarları dosyası belirtmek için test > test **ayarları** > **Test ayarları dosyası**' **nı seçin ve** *. runsettings* dosyasını seçin.

![Visual Studio 2017 'de test ayarları Dosya menüsünü seçin](media/select-test-settings-file.png)

Dosya, test ayarları menüsünde görünür ve onu seçebilir veya seçimden kaldırabilirsiniz. Seçildiğinde, çalışma ayarları dosyası **kod kapsamını çözümle**' yi seçtiğiniz her seferinde geçerlidir.

::: moniker-end

::: moniker range=">=vs-2019"

#### <a name="visual-studio-2019-version-163-and-earlier"></a>Visual Studio 2019 sürüm 16,3 ve önceki sürümleri

IDE 'de bir çalıştırma ayarları dosyası belirtmek için **Test** > **ayarları dosyası seç**' i seçin. *. Runsettings* dosyasına gidin ve seçin.

![Visual Studio 2019 'de test ayarları Dosya menüsünü seçin](media/vs-2019/select-settings-file.png)

Dosya, Test menüsünde görünür ve onu seçebilir veya seçimden kaldırabilirsiniz. Seçildiğinde, çalışma ayarları dosyası **kod kapsamını çözümle**' yi seçtiğiniz her seferinde geçerlidir.

#### <a name="visual-studio-2019-version-164-and-later"></a>Visual Studio 2019 sürüm 16,4 ve üzeri

Visual Studio 2019 sürüm 16,4 ve sonrasında bir çalıştırma ayarları dosyası belirtmenin üç yolu vardır:

- Proje dosyası ya da bir dizin. Build. props dosyası aracılığıyla bir projeye yapı özelliği ekleyin. Bir projenin çalıştırma ayarları dosyası **Runsettingsfilepath**özelliği tarafından belirtilir. 

    - Proje düzeyi çalışma ayarları şu anda C#, vb, C++ve F# projelerinde destekleniyor.
    - Bir proje için belirtilen dosya, çözümde belirtilen diğer çalışma ayarları dosyalarını geçersiz kılar.

    Bir proje için *. runsettings* dosyası belirtme örneği:
    
    ```xml
    <Project Sdk="Microsoft.NET.Sdk">
      <PropertyGroup>
        <RunSettingsFilePath>$(SolutionDir)\example.runsettings</RunSettingsFilePath>
      </PropertyGroup>
      ...
    </Project>
    ```

- Çözümünüzün köküne ". runsettings" adlı bir çalıştırma ayarları dosyası yerleştirin.

  Çalışma ayarları dosyalarının otomatik algılanması etkinleştirilirse, bu dosyadaki ayarlar tüm testler üzerinde uygulanır. Runsettings dosyalarını iki konumdan otomatik algılamayı açabilirsiniz:
  
    - **Araçlar** > **seçenekler** > **Test** > **runsettings dosyalarını otomatik algıla**

      ![Visual Studio 2019 'de runsettings dosya seçeneğini otomatik algıla](media/vs-2019/auto-detect-runsettings-tools-window.png)
      
    - **Test** > **çalıştırma ayarlarını yapılandır** > **runsettings dosyalarını otomatik algıla**
    
      ![Visual Studio 2019 'de runsettings Dosya menüsünü otomatik algıla](media/vs-2019/auto-detect-runsettings-menu.png)

- IDE 'de **Test** > **çalıştır ayarlarını yapılandır** > **çözüm genelindeki runsettings dosyasını seçin**ve *. runsettings* dosyasını seçin.

   ![Visual Studio 2019 ' de test çözümü geniş çalıştırma ayarları Dosya menüsünü seçin](media/vs-2019/select-solution-settings-file.png)
      
   - Bu dosya, varsa çözümün kökündeki ". runsettings" dosyasını geçersiz kılar ve tüm testler üzerinde uygulanır.  
   - Bu dosya seçimi yalnızca yerel olarak devam ettirir. 

::: moniker-end

### <a name="command-line"></a>Komut satırı

Komut satırından testleri çalıştırmak için *VSTest. Console. exe*' yi kullanın ve **/Settings** parametresini kullanarak ayarlar dosyasını belirtin.

1. Visual Studio Geliştirici Komut Satırını başlatın:

   ::: moniker range="vs-2017"

   Windows **Başlat** menüsünde, **vs 2017 için** **Visual Studio 2017** > Geliştirici komut istemi ' u seçin.

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   Windows **Başlat** menüsünde, **vs 2019 için** **Visual Studio 2019** > Geliştirici komut istemi ' u seçin.

   ::: moniker-end

2. Şuna benzer bir komut girin:

   ```cmd
   vstest.console.exe MyTestAssembly.dll /EnableCodeCoverage /Settings:CodeCoverage.runsettings
   ```

   or

   ```cmd
   vstest.console.exe --settings:test.runsettings test.dll
   ```

Daha fazla bilgi için bkz. [VSTest. Console. exe komut satırı seçenekleri](vstest-console-options.md).

## <a name="customize-tests"></a>Testleri özelleştirme

Testlerinizi bir *. runsettings* dosyası kullanarak özelleştirmek için şu adımları izleyin:

1. Visual Studio çözümünüze bir XML dosyası ekleyin ve bunu *test. runsettings*olarak kaydedin.

   > [!TIP]
   > Dosya adı, *. runsettings*uzantısını kullandığınız sürece büyük değildir.

2. Dosya içeriğini izleyen örnekteki XML ile değiştirin ve gerektiği gibi özelleştirin.

::: moniker range="vs-2017"

3. **Test menüsünde test** **ayarları** ' nı seçin > **Test ayarları dosyasını seçin**. Oluşturduğunuz *. runsettings* dosyasına gidin ve ardından **Tamam**' ı seçin.

::: moniker-end

::: moniker range=">=vs-2019"

3. Çalışma ayarları dosyasını seçmek için **Test** > **ayarları dosyası seç**' i seçin. Oluşturduğunuz *. runsettings* dosyasına gidin ve ardından **Tamam**' ı seçin.

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
    </DataCollectors>
  </DataCollectionRunSettings>

  <!-- Parameters used by tests at run time -->
  <TestRunParameters>
    <Parameter name="webAppUrl" value="http://localhost" />
    <Parameter name="webAppUserName" value="Admin" />
    <Parameter name="webAppPassword" value="Password" />
  </TestRunParameters>

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

### <a name="run-configuration"></a>Çalıştırma yapılandırma

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

|Node|Varsayılan|Değerler|
|-|-|-|
|**ResultsDirectory**||Test sonuçlarının yerleştirildiği dizin.|
|**TargetFrameworkVersion**|Framework40|.NET Core kaynakları için `FrameworkCore10`, UWP tabanlı kaynaklar için `FrameworkUap10`, .NET Framework 4,5 ve üzeri `Framework45`, `Framework40` 4,0 için .NET Framework ve `Framework35` 3,5 .NET Framework.<br /><br />Bu ayar, testleri keşfetmek ve yürütmek için kullanılan birim test çerçevesinin sürümünü belirtir. Birim test projesinin yapı özelliklerinde belirttiğiniz .NET platformu sürümünden farklı olabilir.<br /><br />*. Runsettings* dosyasından `TargetFrameworkVersion` öğeyi atlarsanız, platform otomatik olarak oluşturulan ikili dosyaları temel alan çerçeve sürümünü belirler.|
|**TargetPlatform**|x86|x86, x64|
|**Treattestadaptererrorsasuyarılar**|yanlış|yanlış, doğru|
|**TestAdaptersPaths**||TestAdapters 'nin bulunduğu dizine ait bir veya daha fazla yol|
|**MaxCpuCount**|1|Bu ayar, makinedeki kullanılabilir çekirdekleri kullanarak birim testlerini çalıştırırken paralel test yürütme derecesini denetler. Test yürütme altyapısı, kullanılabilir her çekirdek üzerinde ayrı bir işlem olarak başlar ve her bir çekirdeğe, testlerin çalışmasına sahip bir kapsayıcı verir. Kapsayıcı bir derleme, DLL veya ilgili yapıt olabilir. Sınama kapsayıcısı zamanlama birimidir. Her kapsayıcıda testler, test çerçevesine göre çalıştırılır. Birçok kapsayıcı varsa, süreçler bir kapsayıcıda testlerin yürütülmesi tamamlandığında, bir sonraki kullanılabilir kapsayıcıya verilirler.<br /><br />MaxCpuCount şu olabilir:<br /><br />n, burada 1 < = n < = çekirdek sayısı: en fazla n işlem başlatıldı<br /><br />n, burada n = diğer herhangi bir değer: başlatılan işlem sayısı kullanılabilir çekirdek sayısına kadar olabilir. Örneğin, n = 0 ' ı, platformun ortama göre başlatılacak en iyi işlem sayısına otomatik olarak karar vermesini sağlamak için ayarlayın.|
|**TestSessionTimeout**||Belirli bir zaman aşımını aştığında kullanıcıların bir test oturumunu sonlanmasına izin verir. Bir zaman aşımı ayarlamak, kaynakların iyi şekilde tüketilmesini ve test oturumlarının bir ayarlama zamanına göre kısıtlanmasını sağlar. Bu ayar, **Visual Studio 2017 sürüm 15,5** ve sonraki sürümlerinde kullanılabilir.|

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

### <a name="testrunparameters"></a>TestRunParameters

```xml
<TestRunParameters>
    <Parameter name="webAppUrl" value="http://localhost" />
    <Parameter name="docsUrl" value="https://docs.microsoft.com" />
</TestRunParameters>
```

Test çalıştırması parametreleri, çalışma zamanında testlerin kullanabileceği değişkenleri ve değerleri tanımlamak için bir yol sağlar. <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.Properties%2A?displayProperty=nameWithType> özelliğini kullanarak parametrelere erişin:

```csharp
[TestMethod]
public void HomePageTest()
{
    string appURL = TestContext.Properties["webAppUrl"];
}
```

Test çalıştırması parametrelerini kullanmak için, test sınıfınız için bir özel <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext> alanı ve ortak <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext> özelliği ekleyin.

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

Bu ayarlar, <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> özniteliğine sahip test yöntemlerini çalıştıran test bağdaştırıcısına özgüdür.

|Yapılandırma|Varsayılan|Değerler|
|-|-|-|
|**Forcedlegacymode öğesini**|yanlış|Visual Studio 2012 ' de, MSTest bağdaştırıcısı daha hızlı ve daha ölçeklenebilir hale getirmek için iyileştirildi. Testlerin çalışma sırası gibi bazı davranışlar Visual Studio'nun önceki sürümlerindekiyle aynı olmayabilir. Eski test bağdaştırıcısını kullanmak için bu değeri **true** olarak ayarlayın.<br /><br />Örneğin, birim testi için belirtilen bir *app. config* dosyanız varsa bu ayarı kullanabilirsiniz.<br /><br />Daha yeni bağdaştırıcı kullanmanıza olanak vermek için testlerinizi yeniden düzenlemenizi öneririz.|
|**Ignoretesmpyasası**|yanlış|MSTest veya Microsoft Test Yöneticisi'nde çalıştırıldığında test etkisi özelliği son değişikliklerden etkilenen testleri önceliklendirir. Bu ayar özelliği devre dışı bırakır. Daha fazla bilgi için bkz. [önceki bir derlemeden bu yana hangi testlerin çalıştırılması gerekir](https://msdn.microsoft.com/library/dd286589).|
|**SettingsFile**||Burada MSTest bağdaştırıcısıyla kullanılacak bir test ayarları dosyası belirtebilirsiniz. Ayrıca [, Ayarlar menüsünden](#ide)bir test ayarları dosyası belirtebilirsiniz.<br /><br />Bu değeri belirtirseniz, **Forcedlegacymode** öğesini de **true**olarak ayarlamanız gerekir.<br /><br />`<ForcedLegacyMode>true</ForcedLegacyMode>`|
|**KeepExecutorAliveAfterLegacyRun**|yanlış|Test çalıştırması tamamlandıktan sonra MSTest kapatılır. Testin bir parçası olarak başlatılan tüm işlemler de sonlandırıldı. Test yürütücüsünü canlı tutmak istiyorsanız, değeri **true**olarak ayarlayın. Örneğin, bu ayarı, tarayıcının kodlanmış UI testleri arasında çalışmasını sağlamak için kullanabilirsiniz.|
|**DeploymentEnabled**|true|Değeri **false**olarak ayarlarsanız, test yöntetiniz içinde belirttiğiniz dağıtım öğeleri dağıtım dizinine kopyalanmaz.|
|**CaptureTraceOutput**|true|<xref:System.Diagnostics.Trace.WriteLine%2A?displayProperty=nameWithType>kullanarak, test yönteminizin hata ayıklama izlemeye yazabilirsiniz.|
|**Deletedeploymentdirectoryaftertestrunistamamlanmıştır**|true|Bir test çalıştırdıktan sonra dağıtım dizinini sürdürmek için bu değeri **false**olarak ayarlayın.|
|**MapInconclusiveToFailed**|yanlış|Bir test, Sonuçlandırılamayan bir durumla tamamlanırsa **Test Gezgini**'nde atlanan duruma eşlenir. Sonuçlandırılamayan testlerin başarısız olarak görüntülenmesini istiyorsanız değeri **true**olarak ayarlayın.|
|**Inprocmode**|yanlış|Testlerinizin MSTest bağdaştırıcısıyla aynı işlemde çalıştırılmasını istiyorsanız, bu değeri **true**olarak ayarlayın. Bu ayar, küçük bir performans kazancı sağlar. Ancak bir test bir özel durumla çıkıldığında, kalan testler çalıştırılmaz.|
|**AssemblyResolution**|yanlış|Birim testlerini bulurken ve çalıştırırken ek derlemeler için yollar belirtebilirsiniz. Örneğin, test derlemesi ile aynı dizinde olmayan bağımlılık derlemeleri için bu yolları kullanın. Bir yol belirtmek için bir **Dizin yolu** öğesi kullanın. Yol, ortam değişkenleri içerebilir.<br /><br />`<AssemblyResolution>  <Directory Path="D:\myfolder\bin\" includeSubDirectories="false"/> </AssemblyResolution>`|

## <a name="see-also"></a>Ayrıca bkz.

- [Test çalıştırması yapılandırma](https://github.com/microsoft/vstest-docs/blob/master/docs/configure.md)
- [Kod kapsamı analizini özelleştirme](../test/customizing-code-coverage-analysis.md)
- [Visual Studio test görevi (Azure Test Plans)](/azure/devops/pipelines/tasks/test/vstest?view=vsts)
