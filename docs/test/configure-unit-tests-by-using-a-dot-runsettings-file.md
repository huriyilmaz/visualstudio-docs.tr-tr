---
title: Birim testlerini .runsettings dosyasıyla yapılandırma
ms.date: 10/03/2019
ms.topic: conceptual
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: cad3a644935e14a605dbef02bddc1f9337c1f5e9
ms.sourcegitcommit: eeff6f675e7850e718911647343c5df642063d5e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80233090"
---
# <a name="configure-unit-tests-by-using-a-runsettings-file"></a>*.runsettings* dosyasi kullanarak birim testlerini yapılandır

Visual Studio'daki birim testleri *.runsettings* dosyası kullanılarak yapılandırılabilir. Örneğin, testlerin çalıştırıldığı .NET sürümünü, test sonuçları dizinini veya test çalışması sırasında toplanan verileri değiştirebilirsiniz.

Çalıştır ayarları dosyaları isteğe bağlıdır. Özel yapılandırma nız yoksa, *.runsettings* dosyasına ihtiyacınız yoktur. *.runsettings* dosyasının yaygın [kullanımı, kod kapsamı çözümlemesi](../test/customizing-code-coverage-analysis.md)özelleştirmektir.

## <a name="specify-a-run-settings-file"></a>Çalışma ayarları dosyasi belirt

Çalıştır ayarları dosyaları, Komut [satırında](vstest-console-options.md), IDE'de veya Azure Test Planları veya Team Foundation Server (TFS) kullanılarak oluşturulan bir [iş akışında](/azure/devops/pipelines/test/getting-started-with-continuous-testing?view=vsts) çalıştırılan testleri yapılandırmak için kullanılabilir.

### <a name="ide"></a>IDE

::: moniker range="vs-2017"

IDE'de bir çalışma ayarları dosyası belirtmek için **Test Ayarlarını** > **Seçin Test Ayarları Dosyasını** **seçin** > ve ardından *.runsettings* dosyasını seçin.

![Visual Studio 2017'de test ayarları dosya menüsünü seçin](media/select-test-settings-file.png)

Dosya Test Ayarları menüsünde görünür ve dosyayı seçebilir veya seçebilirsiniz. Seçili yken, **Kodu Kapsamını Çözümle'yi**seçtiğinizde çalıştır ayarları dosyası geçerlidir.

::: moniker-end

::: moniker range=">=vs-2019"

#### <a name="visual-studio-2019-version-163-and-earlier"></a>Visual Studio 2019 sürüm 16.3 ve önceki

IDE'de bir çalıştırma ayarları dosyası belirtmek için**Ayarlar Dosyasını**Test **Seç'i** > seçin. *.runsettings* dosyasına göz atın ve seçin.

![Visual Studio 2019'da test ayarları dosya menüsünü seçin](media/vs-2019/select-settings-file.png)

Dosya Test menüsünde görünür ve dosyayı seçebilir veya seçebilirsiniz. Seçili yken, **Kodu Kapsamını Çözümle'yi**seçtiğinizde çalıştır ayarları dosyası geçerlidir.

#### <a name="visual-studio-2019-version-164-and-later"></a>Visual Studio 2019 sürüm 16.4 ve sonrası

Visual Studio 2019 sürüm 16.4 ve sonrası bir çalışma ayarları dosyabelirtmenin üç yolu vardır:

- Proje dosyası veya Dizin.Build.props dosyası aracılığıyla projeye yapı özelliği ekleyin. Bir projenin çalıştır ayarları dosyası **RunSettingsFilePath**özelliği tarafından belirtilir.

    - Proje düzeyinde ki çalışma ayarları şu anda C#, VB, C++ve F# projelerinde desteklenir.
    - Proje için belirtilen dosya, çözümde belirtilen diğer çalıştırma ayarları dosyasını geçersiz kılar.
    - [Bu MSBuild özellikleri,](https://docs.microsoft.com/visualstudio/msbuild/msbuild-reserved-and-well-known-properties?view=vs-2019) runsettings dosyasına giden yolu belirtmek için kullanılabilir. 

    Bir proje için *.runsettings* dosyası belirtme örneği:
    
    ```xml
    <Project Sdk="Microsoft.NET.Sdk">
      <PropertyGroup>
        <RunSettingsFilePath>$(MSBuildProjectDirectory)\example.runsettings</RunSettingsFilePath>
      </PropertyGroup>
      ...
    </Project>
    ```

- Çözümünüzün köküne ".runsettings" adlı bir çalışma ayarları dosyası yerleştirin.

  Çalıştır ayarları dosyalarının otomatik algılaması etkinleştirilmişse, bu dosyadaki ayarlar çalıştırılantüm testlere uygulanır. Runsettings dosyalarının otomatik algılamasini iki yerden açabilirsiniz:
  
    - **Araçlar** > **Seçenekleri** > **Test** > **Otomatik Algılama runsettings Dosyaları**

      ![Visual Studio 2019'da otomatik algılama runsettings dosya seçeneği](media/vs-2019/auto-detect-runsettings-tools-window.png)
      
    - **Yapıyı** > **Yapılandırma Çalıştırma Ayarları** > **Otomatik Algılama runsettings Dosyaları**
    
      ![Visual Studio 2019'da otomatik algılama runsettings dosya menüsü](media/vs-2019/auto-detect-runsettings-menu.png)

- IDE'de, **Test** > **Yapılaşı Çalıştır Ayarlarını** > **Çözüm Geniş runsettings Dosyasını**Seçin'i seçin ve ardından *.runsettings* dosyasını seçin.

   ![Visual Studio 2019'da çözüm genelinde ki çalışma ayarları dosya menüsünü seçin](media/vs-2019/select-solution-settings-file.png)
      
   - Bu dosya varsa çözümün kökündeki ".runsettings" dosyasını geçersiz kılar ve çalıştırılatan tüm testlere uygulanır.  
   - Bu dosya seçimi yalnızca yerel olarak devam eder. 

::: moniker-end

### <a name="command-line"></a>Komut satırı

Komut satırından testleri çalıştırmak için *vstest.console.exe'yi*kullanın ve **/Ayarlar** parametresini kullanarak ayarlar dosyasını belirtin.

1. Visual Studio Geliştirici Komut Satırını başlatın:

   ::: moniker range="vs-2017"

   Windows **Başlat** menüsünde, VS **2017 için Visual Studio 2017** > **Geliştirici Komut Komut Komut Ustem'ini**seçin.

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   Windows **Başlat** menüsünde, VS **2019 için Visual Studio 2019** > **Geliştirici Komut Komut Komut Ustem'i**seçin.

   ::: moniker-end

2. Benzer bir komut girin:

   ```cmd
   vstest.console.exe MyTestAssembly.dll /EnableCodeCoverage /Settings:CodeCoverage.runsettings
   ```

   or

   ```cmd
   vstest.console.exe --settings:test.runsettings test.dll
   ```

Daha fazla bilgi için [VSTest.Console.exe komut satırı seçeneklerine](vstest-console-options.md)bakın.

## <a name="customize-tests"></a>Testleri özelleştirme

*.runsettings* dosyasını kullanarak testlerinizi özelleştirmek için aşağıdaki adımları izleyin:

1. Visual Studio çözümünüze bir XML dosyası ekleyin ve *test.runsettings*olarak kaydedin.

   > [!TIP]
   > Uzantı *.runsettings'i*kullandığınız sürece dosya adı önemli değil.

2. Aşağıdaki örnekten dosya içeriğini XML ile değiştirin ve gerektiğinde özelleştirin.

::: moniker range="vs-2017"

3. **Test** menüsünde, **Test Ayarlarını** > **Seçin Test Ayarları Dosyasını**seçin. Oluşturduğunuz *.runsettings* dosyasına göz atın ve ardından **Tamam'ı**seçin.

::: moniker-end

::: moniker range=">=vs-2019"

3. Çalıştır ayarları dosyasını seçmek için**Ayarlar Dosyasını** **Seç'i** > seçin. Oluşturduğunuz *.runsettings* dosyasına göz atın ve ardından **Tamam'ı**seçin.

::: moniker-end

   > [!TIP]
   > Çözümünüzde birden fazla *.runsettings* dosyası oluşturabilir ve gerektiğinde etkin test ayarları dosyası olarak birini seçebilirsiniz.

## <a name="example-runsettings-file"></a>Örnek *.runsettings* dosyası

Aşağıdaki XML, tipik bir *.runsettings* dosyasının içeriğini gösterir. Varsayılan bir değere sahip olduğundan dosyanın her öğesi isteğe bağlıdır.

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

## <a name="elements-of-a-runsettings-file"></a>*.runsettings* dosyasının öğeleri

İzleyen bölümler *.runsettings* dosyasının öğelerini ayrıntıya kadar ayrıntıya getirir.

### <a name="run-configuration"></a>Yapılandırmayı çalıştır

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
|**SonuçlarDindizin**||Test sonuçlarının yerleştirildiği dizin.|
|**TargetFrameworkVersion**|Framework40|`FrameworkCore10`.NET Çekirdek kaynakları `FrameworkUap10` için, UWP `Framework45` tabanlı kaynaklar için, .NET `Framework40` Framework 4.5 ve üzeri `Framework35` için, .NET Framework 4.0 için ve .NET Framework 3.5 için.<br /><br />Bu ayar, testleri keşfetmek ve yürütmek için kullanılan birim test çerçevesinin sürümünü belirtir. Birim test projesinin yapı özelliklerinde belirttiğiniz .NET platformu sürümünden farklı olabilir.<br /><br />*.runsettings* dosyasından `TargetFrameworkVersion` öğeyi atlarsanız, platform yapılı ikilileri temel alan çerçeve sürümünü otomatik olarak belirler.|
|**Targetplatform**|x86|x86, x64|
|**TreatTestAdapterErrorsAsWarnings**|yanlış|yanlış, doğru|
|**TestAdaptersYollar**||TestAdapters'ın bulunduğu dizine giden bir veya daha fazla yol|
|**MaxCpuCount**|1|Bu ayar, makinedeki kullanılabilir çekirdekleri kullanarak birim testlerini çalıştırırken paralel test yürütme derecesini denetler. Test yürütme motoru, kullanılabilir her çekirdekte ayrı bir işlem olarak başlar ve her çeki, çalışması gereken testleri olan bir kapsayıcı verir. Kapsayıcı bir derleme, DLL veya ilgili artifakı olabilir. Test kapsayıcısı zamanlama birimidir. Her kapsayıcıda, testler test çerçevesine göre çalıştırılır. Çok sayıda kapsayıcı varsa, işlemler testleri bir kapsayıcıda yürütmeyi tamamladıkça, bir sonraki kullanılabilir kapsayıcı verilir.<br /><br />MaxCpuCount olabilir:<br /><br />n, 1 <= n <= çekirdek sayısı: n'ye kadar prosesler başlatılır<br /><br />n, nerede n = başka bir değer: başlatılan işlem sayısı kullanılabilir çekirdek sayısına kadar olabilir. Örneğin, n=0'ı, platformun ortama göre başlatılması gereken en uygun işlem sayısına otomatik olarak karar vermesi için ayarlayın.|
|**TestSessionTimeout**||Kullanıcıların belirli bir zaman aşımını aştığında bir test oturumunu sonlandırmasına olanak tanır. Zaman aşımını ayarlamak, kaynakların iyi tüketilmesini ve test oturumlarının belirli bir süreyle sınırlandırIlmesini sağlar. Ayar **Visual Studio mevcuttur 2017 sürüm 15.5** ve sonrası.|
|**DotnetHostPath**||Test host'u çalıştırmak için kullanılan dotnet ana bilgisayara özel bir yol belirtin. Bu, kendi dotnetinizi yaparken( örneğin dotnet/runtime deposunu yaparken) kullanışlıdır. Bu seçeneği belirtmek testhost.exe'yi aramayı atlar ve her zaman testhost.dll'yi kullanır. 

### <a name="diagnostic-data-adapters-data-collectors"></a>Tanısal veri bağdaştırıcıları (veri toplayıcıları)

**DataCollectors** öğesi tanılama veri bağdaştırıcılarının ayarlarını belirtir. Tanılama veri bağdaştırıcıları, test altında ortam ve uygulama hakkında ek bilgiler toplar. Her bağdaştırıcının varsayılan ayarları vardır ve yalnızca varsayılanları kullanmak istemiyorsanız ayarları sağlamanız gerekir.

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

Kod kapsamı veri toplayıcısı uygulama kodu bölümlerinin testte uygulandığı bir günlük oluşturur. Kod kapsamı için ayarları özelleştirme hakkında daha fazla bilgi için [kod kapsamı çözümlemesi özelleştir'e](../test/customizing-code-coverage-analysis.md)bakın.

#### <a name="video-data-collector"></a>Video veri toplayıcı

Video veri toplayıcısı, testler çalıştırıldığında bir ekran kaydı yakalar. Bu kayıt, ui testlerini sorun giderme için yararlıdır. Video veri toplayıcısı **Visual Studio 2017 sürüm 15.5** ve sonrası mevcuttur.

Diğer tanılama veri bağdaştırıcılarını özelleştirmek için bir [test ayarları dosyası](../test/collect-diagnostic-information-using-test-settings.md)kullanın.

### <a name="testrunparameters"></a>TestRunParametreleri

```xml
<TestRunParameters>
    <Parameter name="webAppUrl" value="http://localhost" />
    <Parameter name="docsUrl" value="https://docs.microsoft.com" />
</TestRunParameters>
```

Test çalıştırma parametreleri, çalışma zamanında testleriçin kullanılabilen değişkenleri ve değerleri tanımlamak için bir yol sağlar. Özelliği kullanarak parametrelere erişin: <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.Properties%2A?displayProperty=nameWithType>

```csharp
[TestMethod]
public void HomePageTest()
{
    string appURL = TestContext.Properties["webAppUrl"];
}
```

Test çalıştırma parametrelerini kullanmak <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext> için, <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext> test sınıfınıza özel bir alan ve ortak bir özellik ekleyin.

### <a name="mstest-run-settings"></a>MSTest çalışma ayarları

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

Bu ayarlar, özniteliği olan test yöntemlerini çalıştıran test bağdaştırıcısına <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> özgür.

|Yapılandırma|Varsayılan|Değerler|
|-|-|-|
|**ForcedLegacyMode**|yanlış|Visual Studio 2012'de, MSTest bağdaştırıcısı daha hızlı ve daha ölçeklenebilir hale getirmek için optimize edildi. Testlerin çalışma sırası gibi bazı davranışlar Visual Studio'nun önceki sürümlerindekiyle aynı olmayabilir. Eski test bağdaştırıcısını kullanmak için bu değeri **doğru** olarak ayarlayın.<br /><br />Örneğin, birim testi için belirtilen bir *app.config* dosyanız varsa bu ayarı kullanabilirsiniz.<br /><br />Daha yeni bağdaştırıcı kullanmanıza olanak vermek için testlerinizi yeniden düzenlemenizi öneririz.|
|**IgnoreTestImpact**|yanlış|MSTest veya Microsoft Test Yöneticisi'nde çalıştırıldığında test etkisi özelliği son değişikliklerden etkilenen testleri önceliklendirir. Bu ayar özelliği devre dışı bırakır. Daha fazla bilgi için bkz. önceki [yapıdan bu yana hangi testlerin çalıştırılması gerektiği.](https://msdn.microsoft.com/library/dd286589)|
|**SettingsFile**||Burada MSTest bağdaştırıcısı ile kullanılacak bir test ayarları dosyası belirtebilirsiniz. Ayrıca [ayarlar menüsünden](#ide)bir test ayarları dosyası belirtebilirsiniz.<br /><br />Bu değeri belirtirseniz, **ForcedlegacyMode'u** da **doğru**olarak ayarlamanız gerekir.<br /><br />`<ForcedLegacyMode>true</ForcedLegacyMode>`|
|**KeepExecutorAliveAfterLegacyRun**|yanlış|Test çalıştırması tamamlandıktan sonra MSTest kapatılır. Testin bir parçası olarak başlatılan herhangi bir işlem de öldürülür. Test uygulayıcısını canlı tutmak istiyorsanız, değeri **doğru**olarak ayarlayın. Örneğin, tarayıcının kodlanmış UI testleri arasında çalışmasını sağlamak için bu ayarı kullanabilirsiniz.|
|**DeploymentEnabled**|true|Değeri, test yönteminizde belirttiğiniz **yanlış,** dağıtım öğelerine ayarlarsanız dağıtım dizinine kopyalanmaz.|
|**CaptureTraceOutput**|true|Test yönteminizden hata ayıklama izine <xref:System.Diagnostics.Trace.WriteLine%2A?displayProperty=nameWithType>.|
|**DeleteDeploymentDirectoryAfterTestRunIsComplete**|true|Bir test çalışmasından sonra dağıtım dizinini korumak için bu değeri **false**olarak ayarlayın.|
|**MapInconclusiveToFailed**|yanlış|Bir test sonuçsuz bir durumla tamamlanırsa, **Test Gezgini'nde**atlanan duruma eşlenir. Sonuçsuz testlerin başarısız olarak gösterilmesini istiyorsanız, değeri **doğru**olarak ayarlayın.|
|**InProcMode**|yanlış|Testlerinizin MSTest bağdaştırıcısı ile aynı işlemde çalıştırılmasını istiyorsanız, bu değeri **doğru**olarak ayarlayın. Bu ayar, küçük bir performans kazancı sağlar. Ancak bir test bir istisna dışında çıkarsa, kalan testler çalışmaz.|
|**Montaj Çözümü**|yanlış|Birim testleri bulurken ve çalıştırırken ek derlemelere giden yolları belirtebilirsiniz. Örneğin, test derlemesi ile aynı dizinde olmayan bağımlılık derlemeleri için bu yolları kullanın. Bir yol belirtmek için bir **Dizin Yolu** öğesi kullanın. Yollar ortam değişkenlerini içerebilir.<br /><br />`<AssemblyResolution>  <Directory Path="D:\myfolder\bin\" includeSubDirectories="false"/> </AssemblyResolution>`|

## <a name="see-also"></a>Ayrıca bkz.

- [Test çalışmasını yapılandırma](https://github.com/microsoft/vstest-docs/blob/master/docs/configure.md)
- [Kod kapsamı analizini özelleştirme](../test/customizing-code-coverage-analysis.md)
- [Visual Studio test görevi (Azure Test Planları)](/azure/devops/pipelines/tasks/test/vstest?view=vsts)

