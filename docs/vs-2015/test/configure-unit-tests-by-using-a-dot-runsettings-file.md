---
title: . Runsettings dosyasını kullanarak birim testlerini yapılandırma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: f7e9e4a2-5d01-4f78-b408-5be3892bd162
caps.latest.revision: 28
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b9779dd685ad662cd0761dc85be58d0dbb3ccf0c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660665"
---
# <a name="configure-unit-tests-by-using-a-runsettings-file"></a>.runsettings dosyasını kullanarak birim testlerini yapılandırma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 'daki birim testleri, *. runsettings dosyası kullanılarak yapılandırılabilir. (Dosya adı ne kadar değil, '. runsettings. ' uzantısını kullanmanız gerekir) Örneğin, testlerin çalıştırılacağı .NET Framework, test sonuçlarının teslim edildiği dizini ve test çalışması sırasında toplanan verileri değiştirebilirsiniz.

 Herhangi bir özel yapılandırma yapmak istemiyorsanız, *. runsettings dosyasına ihtiyacınız yoktur. En sık kullanılan kullanım, [kod kapsamını](../test/customizing-code-coverage-analysis.md)özelleştirecek.

> [!NOTE]
> **. runsettings ve. testsettings**
>
> Testleri yapılandırmak için iki tür dosya vardır. *. runsettings birim testleri için kullanılır. Ve [Laboratuvar ortamı testleri](https://msdn.microsoft.com/library/0c15317e-80c6-4317-aed3-82b8e15e3901), Web performansı ve yük testleri Için ve IntelliTrace ve olay günlüğü bağdaştırıcıları gibi bazı tanılama veri bağdaştırıcısı türlerini özelleştirmek için \*. testsettings.
>
> Visual Studio 'nun önceki sürümlerinde 2010 'e kadar, birim testleri de *. testsettings dosyaları kullanılarak özelleştirildi. Yine de bunu yapabilirsiniz, ancak \*. runsettings dosyasında eşdeğer yapılandırmaların kullanılması durumunda testler daha yavaş çalışır.

## <a name="customizing-tests-with-a-runsettings-file"></a>Bir .runsettings dosyası ile testleri özelleştirme

1. Visual Studio çözümünüze bir XML dosyası ekleyin ve test. runsettings olarak yeniden adlandırın. (Dosya adı önemi değildir, ancak uzantının. runsettings olması gerekir.)

2. Dosya içeriğini [örnekle](#example)değiştirin.

    Kendi gereksinimlerine göre düzenleyin.

3. **Test** menüsünde **Test ayarları**' nı seçin, **Test ayarları dosyası**' nı seçin.

   Çözümünüzde birden fazla \*. runsettings dosyası oluşturabilir ve **Test ayarları** menüsünü kullanarak onları farklı zamanlarda etkinleştirebilir veya devre dışı bırakabilirsiniz.

   ![Çalışma ayarları dosyasını etkinleştirme](../test/media/runsettings-1.png "RunSettings-1")

## <a name="example"></a>Bu örnek. runsettings dosyasını kopyalayın
 Tipik bir *. runsettings dosyası aşağıda verilmiştir. Her değerin bir varsayılanı olduğundan, dosyanın her bir öğesi isteğe bağlıdır.

```xml
<?xml version="1.0" encoding="utf-8"?>
<RunSettings>
  <!-- Configurations that affect the Test Framework -->
  <RunConfiguration>
    <MaxCpuCount>1</MaxCpuCount>
    <!-- Path relative to solution directory -->
    <ResultsDirectory>.\TestResults</ResultsDirectory>

    <!-- [x86] | x64
      - You can also change it from menu Test, Test Settings, Default Processor Architecture -->
    <TargetPlatform>x86</TargetPlatform>

    <!-- Framework35 | [Framework40] | Framework45 -->
    <TargetFrameworkVersion>Framework40</TargetFrameworkVersion>

    <!-- Path to Test Adapters -->
    <TestAdaptersPaths>%SystemDrive%\Temp\foo;%SystemDrive%\Temp\bar</TestAdaptersPaths>
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

    </DataCollectors>
  </DataCollectionRunSettings>

  <!-- Parameters used by tests at runtime -->
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

 . Runsettings dosyası, [kod kapsamını](../test/customizing-code-coverage-analysis.md)yapılandırmak için de kullanılır.

 Bu konunun geri kalanı dosya içeriğini açıklamaktadır.

## <a name="edit-your-runsettings-file"></a>.runsettings dosyanızı düzenleme
 .Runsettings dosyası aşağıdaki öğelere sahiptir.

### <a name="test-run-configuration"></a>Test çalıştırma yapılandırması

|Düğüm|Varsayılan|Değerler|
|----------|-------------|------------|
|`ResultsDirectory`||Test sonuçlarının yerleştirileceği dizin.|
|`TargetFrameworkVersion`|Framework40|Framework35, Framework40, Framework45<br /><br /> Bu birim test çerçevesinin hangi sürümünün testlerini bulmak ve yürütmek için kullanıldığını belirtir. Birim test projesinin yapı özelliklerinde belirttiğiniz .NET platformu sürümünden farklı olabilir.|
|`TargetPlatform`|x86|x86, x64|
|`TreatTestAdapterErrorsAsWarnings`|false|yanlış, doğru|
|`TestAdaptersPaths`||TestAdapters 'nin bulunduğu dizinin bir veya birden çok yolu|
|`MaxCpuCount`|1\.|Bu, makinedeki kullanılabilir çekirdekleri kullanarak birim testlerini çalıştırırken paralel test yürütme derecesini denetler.  Test yürütme altyapısı, kullanılabilir her çekirdek üzerinde ayrı bir işlem olarak başlar ve her bir çekirdeğe, bir derleme, DLL veya ilgili yapıt gibi testleri çalıştıracak şekilde bir kapsayıcı verir.  Sınama kapsayıcısı zamanlama birimidir.  Her kapsayıcıda testler, test çerçevesine göre çalıştırılır.  Birçok kapsayıcı varsa, süreçler bir kapsayıcıda testlerin yürütülmesi tamamlandığında, bir sonraki kullanılabilir kapsayıcıya verilirler.<br /><br /> MaxCpuCount şu olabilir:<br /><br /> n, burada 1 < = n < = çekirdek sayısı: en fazla n işlem başlatılacak<br /><br /> n, burada n = diğer herhangi bir değer: başlatılan işlem sayısı makinede kullanılabilir çekirdekler kadar olacaktır|

### <a name="diagnostic-data-adapters-data-collectors"></a>Tanılama Veri Bağdaştırıcıları (Veri Toplayıcıları)
 @No__t_0 öğesi, tanılama veri bağdaştırıcılarının ayarlarını belirtir. Tanılama veri bağdaştırıcıları, test uygulanmakta olan uygulama ve ortam hakkında ek bilgi toplamak için kullanılır. Her bağdaştırıcı varsayılan ayarlara sahiptir ve yalnızca varsayılan değerleri kullanmak istemiyorsanız ayarları sağlamanız gerekir.

#### <a name="code-coverage-adapter"></a>Kod kapsamı bağdaştırıcısı
 Kod kapsamı veri toplayıcısı uygulama kodu bölümlerinin testte uygulandığı bir günlük oluşturur. Kod kapsamının ayarlarını özelleştirme hakkında daha fazla bilgi için bkz. [kod kapsamı analizini özelleştirme](../test/customizing-code-coverage-analysis.md).

#### <a name="other-diagnostic-data-adapters"></a>Diğer tanılama veri bağdaştırıcıları
 Kod kapsamı bağdaştırıcısı şu anda çalışma ayarları dosyası kullanılarak özelleştirilebilen tek bağdaştırıcıdır.

 Başka herhangi bir tür tanılama verisi bağdaştırıcısını özelleştirmek için test ayarları dosyası kullanmanız gerekir. Daha fazla bilgi için bkz. [Visual Studio Testleri Için test ayarlarını belirtme](https://msdn.microsoft.com/library/0c15317e-80c6-4317-aed3-82b8e15e3901).

#### <a name="testrunparameters"></a>TestRunParameters
 TestRunParameters, çalışma zamanında testler için kullanılabilen değişkenleri ve değerleri tanımlamak için bir yol sağlar.

### <a name="mstest-run-settings"></a>MSTest Çalıştırma Ayarları
 Bu ayarlar, `[TestMethod]` özniteliğine sahip test yöntemlerini çalıştıran test bağdaştırıcısına özgüdür.

|Yapılandırma|Varsayılan|Değerler|
|-------------------|-------------|------------|
|ForcedLegacyMode|false|Visual Studio 2012'de, MSTest bağdaştırıcısı daha hızlı ve daha ölçeklenebilir olması için iyileştirilmiştir. Testlerin çalışma sırası gibi bazı davranışlar Visual Studio'nun önceki sürümlerindekiyle aynı olmayabilir. Bu değer `true` eski test bağdaştırıcısını kullanacak şekilde ayarlayın.<br /><br /> Örneğin, birim testi için belirtilen bir app.config dosyanız varsa bunu kullanabilirsiniz.<br /><br /> Daha yeni bağdaştırıcı kullanmanıza olanak vermek için testlerinizi yeniden düzenlemenizi öneririz.|
|IgnoreTestImpact|false|MSTest veya Microsoft Test Yöneticisi'nde çalıştırıldığında test etkisi özelliği son değişikliklerden etkilenen testleri önceliklendirir. Bu ayar özelliği devre dışı bırakır. Daha fazla bilgi için bkz. [nasıl yapılır: kod değişikliklerinden sonra hangi testlerin çalıştırılacağını denetlemek Için veri toplama](https://msdn.microsoft.com/library/2f921ea1-9bb0-4870-a30f-0521fc22cb47).|
|SettingsFile||Burada MS Test bağdaştırıcısı ile kullanmak için test ayarları dosyası belirtebilirsiniz. Test ayarları dosyasını menü **testi**, **Test**ayarları, **Test ayarları dosyası seç**' i kullanarak da belirtebilirsiniz.<br /><br /> Bu değeri belirtirseniz, **Forcedlegacymode** öğesini de **true**olarak ayarlamanız gerekir.<br /><br /> `<RunSettings>   <MSTest>     <SettingsFile>my.testsettings</SettingsFile>      <ForcedLegacyMode>true</ForcedLegacyMode>    </MSTest> </RunSettings>`|
|KeepExecutorAliveAfterLegacyRun|false|Test çalıştırması tamamlandıktan sonra MSTest kapatılır. Testin bir parçası olarak başlatılan tüm işlemler de şu anda bitirilecek. Test yürütücüsünü canlı tutmak istiyorsanız bu yapılandırmayı doğru olarak etkinleştirin.<br /><br /> Örneğin, tarayıcının kodlanmış UI testleri arasında çalışmasını sürdürmek için bunu kullanabilirsiniz.|
|DeploymentEnabled|true|Bunu yanlış olarak ayarlarsanız, test yönteminizde belirttiğiniz dağıtım öğeleri dağıtım dizinine kopyalanmaz.|
|CaptureTraceOutput|true|Trace.WriteLine kullanarak Test yönteminizden hata ayıklama izine yazabilirsiniz. Bu yapılandırmayı kullanarak bu hata ayıklama izlemelerini kapatabilirsiniz.|
|DeleteDeploymentDirectoryAfterTestRunIsComplete|true|Dağıtım Dizini'ni, bu değeri yanlış olarak ayarlayarak bir test çalıştırdıktan sonra koruyabilirsiniz.|
|MapInconclusiveToFailed|false|Bir test, yetersiz durum getirirse genellikle Test Gezgini'nde Atlandı durumuna eşlenir. Yetersiz testlerin Başarısız olarak gösterilmesini istiyorsanız bu yapılandırmayı kullanın.|
|InProcMode|false|MS Test bağdaştırıcısı olarak testlerinizin aynı işlemde çalıştırılmasını isterseniz bu değeri doğru olarak ayarlayın. Bu ayar, küçük bir performans kazancı sağlar. Ancak özel durum içeren bir test varsa, diğer testler devam etmez.|
|AssemblyResolution|false|Birim testlerini bulurken ve çalıştırırken ek derlemeler için yollar belirtebilirsiniz.  Örneğin, test derlemesi ile aynı dizinde bulunmayan bağımlılık derlemeleri için bu yolları kullanın.  Bir yol belirtmek için "Dizin yolu" öğesini kullanın.  Yollar, ortam değişkenleri içerebilir.<br /><br /> `<AssemblyResolution>  <Directory Path>"D:\myfolder\bin\" includeSubDirectories="false"/> </AssemblyResolution>`|

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio Testleri Için test ayarlarını belirten](https://msdn.microsoft.com/library/0c15317e-80c6-4317-aed3-82b8e15e3901) [kod kapsamı analizini özelleştirme](../test/customizing-code-coverage-analysis.md)
