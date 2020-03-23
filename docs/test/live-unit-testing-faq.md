---
title: Live Unit Testing SSS
ms.date: 10/03/2017
ms.topic: conceptual
helpviewer_keywords:
- Live Unit Testing FAQ
author: mikejo5000
ms.author: mikejo
ms.workload:
- dotnet
ms.openlocfilehash: ba231e6c203197518b75a7a8c0592f01bba4ffe9
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591547"
---
# <a name="live-unit-testing-frequently-asked-questions"></a>Canlı Ünite Testi sık sorulan sorular

## <a name="supported-frameworks"></a>Desteklenen çerçeveler

**Canlı Birim Testi hangi test çerçevelerini destekler ve en az desteklenen sürümler nelerdir?**

Canlı Birim Testi, aşağıdaki tabloda listelenen üç popüler birim test çerçevesi ile çalışır. Bağdaştırıcılarının ve çerçevelerinin en az desteklenen sürümü de tabloda listelenir. Birim test çerçevelerinin tümü NuGet.org.

|Test Çerçevesi  |Visual Studio Adaptör minimum sürümü  |Çerçeve minimum sürümü  |
|---------|---------|---------|
|xUnit.net |xunit.runner.visualstudio sürümü 2.2.0-beta3-build1187 |xunit 1.9.2 |
|NUnit |NUnit3TestAdapter sürüm 3.7.0 |NUnit sürüm 3.5.0 |
|MSTest |MSTest.TestAdapter 1.1.4-önizleme |MSTest.TestFramework 1.0.5-önizleme |

Başvuru `Microsoft.VisualStudio.QualityTools.UnitTestFramework` yapan daha eski MSTest tabanlı test projeleriniz varsa ve yeni MSTest NuGet paketlerine geçmek istemiyorsanız Visual Studio 2019 veya Visual Studio 2017'ye yükseltin.

Bazı durumlarda, Canlı Birim Testi'nin çalışması için çözümdeki projeler tarafından başvurulan NuGet paketlerini açıkça geri yüklemeniz gerekebilir. Paketin açık bir kısmını çözüm yaparak (üst düzey Visual Studio menüsünden **Rebuild** > **Solution'ı** seçin) veya çözüme sağ tıklayarak ve Living Unit Test'i etkinleştirmeden önce **NuGet Paketlerini Geri Yükle'yi** seçerek paketleri geri yükleyebilirsiniz.

## <a name="net-core-support"></a>.NET Core desteği

**Canlı Birim Testi .NET Core ile çalışır mı?**

Evet. Canlı Birim Testi .NET Core ve .NET Framework ile çalışır.

## <a name="configuration"></a>Yapılandırma

**Live Unit Testing'i çalıştırdığımda neden çalışmıyor?**

Çıktı penceresi (Canlı Birim Testi açılır penceresi seçildiğinde) Canlı Birim Testi'nin neden çalışmadığını size bildirmelidir. Canlı Birim Testi aşağıdaki nedenlerden biriyle işe yaramayabilir:

- Çözümdeki projelertarafından başvurulan NuGet paketleri geri yüklenmediyse, Canlı Birim Testi çalışmaz. Live Unit Testing'i açmadan önce çözümün açık bir şekilde oluşturulması veya NuGet paketlerinin çözüme geri verilmesi bu sorunu çözmelidir.

- Projelerinizde MSTest tabanlı testler kullanıyorsanız, en son MSTest `Microsoft.VisualStudio.QualityTools.UnitTestFramework`NuGet paketlerine `MSTest.TestAdapter` (en az 1.1.11 sürümü gereklidir) ve (en `MSTest.TestFramework` az 1.1.11 sürümü gereklidir) başvurunuzu kaldırdığınızdan ve referanslar eklediğinizden emin olun. Daha fazla bilgi için Visual Studio makalesinde [Canlı Birim Testi'ni kullan](live-unit-testing.md#supported-test-frameworks) "Desteklenen test çerçeveleri" bölümüne bakın.

- Çözümünüzdeki en az bir projede bir NuGet başvurusu veya xUnit, NUnit veya MSTest test çerçevesine doğrudan başvuru olmalıdır. Bu proje aynı zamanda ilgili Visual Studio test adaptörleri NuGet paketine de başvurulmalıdır. Visual Studio test bağdaştırıcısı da *.runsettings* dosyası ndan başvurulabilir. *.runsettings* dosyasında aşağıdaki örnek gibi bir giriş olmalıdır:

```xml
<RunSettings>
    <RunConfiguration>
          <TestAdaptersPaths>path-to-your-test-adapter</TestAdaptersPaths>
     </RunConfiguration>
</RunSettings>
```

## <a name="incorrect-coverage-after-upgrade"></a>Yükseltmeden sonra yanlış kapsama

**Visual Studio Projelerinizde başvurulan test bağdaştırıcısını desteklenen sürüme yükselttikten sonra Canlı Birim Testi neden yanlış kapsama alanı gösteriyor?**

- Çözümdeki birden çok proje NuGet test bağdaştırıcıpaketine başvuruyorsa, her birinin desteklenen sürüme yükseltilmesi gerekir.

- Test bağdaştırıcısı paketinden alınan MSBuild *.props* dosyasının da doğru şekilde güncelleştirdiğinden emin olun. Genellikle proje dosyasının üst kısmında bulunan ve aşağıdaki gibi bulunan NuGet paket sürümünü/içe aktarma yolunu denetleyin:

   ```xml
    <Import Project="..\packages\xunit.runner.visualstudio.2.2.0\build\net20\xunit.runner.visualstudio.props" Condition="Exists('..\packages\xunit.runner.visualstudio.2.2.0\build\net20\xunit.runner.visualstudio.props')" />
   ```

## <a name="customize-builds"></a>Yapıları özelleştir

**Canlı Birim Test yapımı özelleştirebilir miyim?**

Çözümünüz, "düzenli" araç içermeyen yapı için gerekli olmayan enstrümantasyon (Canlı Birim Testi) için oluşturmak için özel adımlar gerektiriyorsa, `BuildingForLiveUnitTesting` projenize kod ekleyebilir veya .özelliği denetleyen ve özel ön/posta oluşturma adımları gerçekleştiren dosyaları *hedefleyebilirsiniz.* Ayrıca, belirli yapı adımlarını kaldırmayı (paket yayımlama veya oluşturma gibi) veya bu proje özelliğine dayalı bir Canlı Birim Testi yapısına yapı adımları (ön koşulları kopyalamak gibi) eklemeyi de seçebilirsiniz. Yapınızı bu özelliğe göre özelleştirmek normal yapınızı hiçbir şekilde değiştirmez ve yalnızca Canlı Birim Testi'nin yapılarını etkiler.

Örneğin, normal bir yapı sırasında NuGet paketleri üreten bir hedef olabilir. Büyük olasılıkla yaptığınız her bir editten sonra NuGet paketlerinin oluşturulmasını istemezsiniz. Böylece, Aşağıdaki gibi bir şey yaparak Canlı Birim Testi yapısındaki hedefi devre dışı kullanabilirsiniz:  

```xml
<Target Name="GenerateNuGetPackages" BeforeTargets="AfterBuild" Condition="'$(BuildingForLiveUnitTesting)' != 'true'">
    <Exec Command='"$(MSBuildThisFileDirectory)..\tools\GenPac" '/>
</Target>
```

## <a name="error-messages-with-outputpath-outdir-or-intermediateoutputpath"></a>OutputPath>, \< \<OutDir> veya \<IntermediateOutputPath> ile hata iletileri

**Canlı Birim Testi çözümümü oluşturmaya çalıştığında neden aşağıdaki hatayı alıyorum: "... koşulsuz olarak ayarlamak `<OutputPath>` için `<OutDir>`görünür veya . Canlı Birim Testi çıktı derlemesinden testleri yürütmez"?**

Çözümünüzün yapı işleminde ikililerin nerede oluşturulacağını belirten özel bir mantık varsa bu hatayı alabilirsiniz. Varsayılan `<OutputPath>`olarak, ikililerinizin konumu, `<OutDir>` ya `<IntermediateOutputPath>` da `<BaseOutputPath>` `<BaseIntermediateOutputPath>`

Canlı Birim Testi, yapı yapılarının Canlı Birim Test yapıları klasörüne bırakıldığından ve yapı işleminiz de bu değişkenleri geçersiz kılarsa başarısız olduğundan emin olmak için bu değişkenleri geçersiz kılar.

Canlı Birim Testi'nin başarılı bir şekilde oluşturulmasını sağlamak için iki ana yaklaşım vardır. Daha kolay yapı yapılandırmaları için çıktı yollarınızı `<BaseIntermediateOutputPath>`. Daha karmaşık yapılandırmalar için çıktı yollarınızı `<LiveUnitTestingBuildRootPath>`.

### <a name="overriding-outputpathintermediateoutputpath-conditionally-based-on-baseoutputpath-baseintermediateoutputpath"></a>Koşullu `<OutputPath>` / `<IntermediateOutputPath>` olarak `<BaseOutputPath>` / `<BaseIntermediateOutputPath>`geçersiz kılma.

> [!NOTE]
> Bu yaklaşımı kullanabilmek için, her projenin birbirinden bağımsız olarak oluşturabilmesi gerekir. Yapı sırasında başka bir projeden bir proje referans yapıları yok. Çalışma süresi boyunca başka bir projeden dinamik olarak yükleme derlemeleri yok (örneğin çağrı). `Assembly.Loadfile("..\..\Project2\Release\Project2.dll")`

Yapı sırasında, Canlı Birim `<BaseOutputPath>` / `<BaseIntermediateOutputPath>` Testi, Canlı Birim Test yapıları klasörünü hedeflemek için değişkenleri otomatik olarak geçersiz kılar.

Örneğin, yapınız aşağıda gösterildiği <OutputPath> gibi geçersiz kılarsa:

```xml
<Project>
  <PropertyGroup>
    <OutputPath>$(SolutionDir)Artifacts\$(Configuration)\bin\$(MSBuildProjectName)</OutputPath>
  </PropertyGroup>
</Project>
```

sonra aşağıdaki XML ile değiştirebilirsiniz:

```xml
<Project>
  <PropertyGroup>
    <BaseOutputPath Condition="'$(BaseOutputPath)' == ''">$(SolutionDir)Artifacts\$(Configuration)\bin\$(MSBuildProjectName)\</BaseOutputPath>
    <OutputPath Condition="'$(OutputPath)' == ''">$(BaseOutputPath)</OutputPath>
  </PropertyGroup>
</Project>
```

Bu, klasörün `<OutputPath>` `<BaseOutputPath>` içinde kalmasını sağlar.

Yapı sürecinizde `<OutDir>` doğrudan geçersiz kılınmayın; yapı `<OutputPath>` yapılarını belirli bir konuma düşürmek için geçersiz kılın.

### <a name="overriding-your-properties-based-on-the-liveunittestingbuildrootpath-property"></a>Özelliğitemel alınabağlı `<LiveUnitTestingBuildRootPath>` olarak mülklerinizi geçersiz kılma.

> [!NOTE]
> Bu yaklaşımda, yapı sırasında oluşturulmayan yapılar klasörüne eklenen dosyalar konusunda dikkatli olmanız gerekir. Aşağıdaki örnek, paketler klasörünü yapıtların altına yerleştirirken ne yapmanız gerektiğini gösterir. Bu klasörün içeriği yapı sırasında oluşturulmadığından, MSBuild özelliği **değiştirilmemelidir.**

Canlı Birim Test yapısı `<LiveUnitTestingBuildRootPath>` sırasında, özellik Canlı Birim Test yapıları klasörünün konumuna ayarlanır.

Örneğin, projenizin burada gösterilen yapıya sahip olduğunu varsayalım.

```
.vs\...\lut\0\b
artifacts\{binlog,obj,bin,nupkg,testresults,packages}
src\{proj1,proj2,proj3}
tests\{testproj1,testproj2}
Solution.sln
```
Canlı Birim Test oluşturma `<LiveUnitTestingBuildRootPath>` sırasında, özellik tam yol `.vs\...\lut\0\b`ayarlanır. Proje, çözümdir `<ArtifactsRoot>` ile eşalan özelliği tanımlıyorsa, MSBuild projesini aşağıdaki gibi güncelleştirebilirsiniz:

```xml
<Project>
    <PropertyGroup Condition="'$(LiveUnitTestingBuildRootPath)' == ''">
        <SolutionDir>$([MSBuild]::GetDirectoryNameOfFileAbove(`$(MSBuildProjectDirectory)`, `YOUR_SOLUTION_NAME.sln`))\</SolutionDir>

        <ArtifactsRoot>Artifacts\</ArtifactsRoot>
        <ArtifactsRoot Condition="'$(LiveUnitTestingBuildRootPath)' != ''">$(LiveUnitTestingBuildRootPath)</ArtifactsRoot>
    </PropertyGroup>

    <PropertyGroup>
        <BinLogPath>$(ArtifactsRoot)\BinLog</BinLogPath>
        <ObjPath>$(ArtifactsRoot)\Obj</ObjPath>
        <BinPath>$(ArtifactsRoot)\Bin</BinPath>
        <NupkgPath>$(ArtifactsRoot)\Nupkg</NupkgPath>
        <TestResultsPath>$(ArtifactsRoot)\TestResults</TestResultsPath>

        <!-- Note: Given that a build doesn't generate packages, the path should be relative to the solution dir, rather than artifacts root, which will change during a Live Unit Testing build. -->
        <PackagesPath>$(SolutionDir)\artifacts\packages</PackagesPath>
    </PropertyGroup>
</Project>
```

## <a name="build-artifact-location"></a>Yapı oluşturma konumu oluşturma

**Bir Canlı Birim Testi'nin yapılarının *.vs* klasörünün altındaki varsayılan konum yerine belirli bir konuma gitmesini istiyorum. Bunu nasıl değiştirebilirim?**

Kullanıcı `LiveUnitTesting_BuildRoot` düzeyindeki ortam değişkenini Canlı Birim Testi yapı yapı yapılarının bırakıldığı yola ayarlayın. 

## <a name="test-explorer-versus-live-unit-testing"></a>Test Explorer ve Canlı Birim Testi

**Test Gezgini penceresinden testleri çalıştırmanın Canlı Birim Testi'ndeki testleri çalıştırmaktan farkı nedir?**

Birkaç fark vardır:

- **Test Gezgini** penceresinden testleri çalıştırma veya hata ayıklama düzenli ikili çalışır, Canlı Birim Testi ise enstrümante ikili çalışır. Aracılı ikilileri hata ayıklamak istiyorsanız, test yönteminize bir [Hataayıklama.Başlat](xref:System.Diagnostics.Debugger.Launch) yöntemi çağrısı eklemek, hata ayıklamanın bu yöntem yürütüldüğünde başlatılmasına neden olur (Canlı Birim Testi tarafından yürütüldüğünde dahil) ve daha sonra enstrümantize edilen ikiliyi ekleyip hata ayıklama yapabilirsiniz. Ancak, bizim umudumuz enstrümantasyon çoğu kullanıcı senaryoları için size şeffaf olmasıdır ve enstrümante bingünlükhata ayıklama gerekmez.

- Canlı Birim Sınaması testleri çalıştırmak için yeni bir uygulama etki alanı oluşturmaz, ancak **Test Gezgini** penceresinden çalıştırılatan testler yeni bir uygulama etki alanı oluşturur.

- Canlı Birim Testi, her test tertibatında testleri sırayla çalışır. **Test Gezgini'nde,** birden çok testi paralel olarak çalıştırmayı seçebilirsiniz.

- **Test Gezgini** varsayılan olarak tek dişli bir dairede (STA) testler çalıştırırken, Canlı Birim Testi çok iş parçacığı bir dairede (MTA) testler çalıştırılır. Canlı Birim Testinde STA'da MSTest testlerini çalıştırmak için, test `<STATestMethod>` `<STATestClass>` yöntemini veya içeren sınıfı `MSTest.STAExtensions 1.0.3-beta` NuGet paketinde bulunan veya öznitelikle süsleyin. NUnit için, test yöntemini `<RequiresThread(ApartmentState.STA)>` öznitelik ile ve xUnit `<STAFact>` için öznitelik ile süsleyin.

## <a name="exclude-tests"></a>Testleri hariç tut

**Canlı Birim Testi'ne katılmaktan testleri nasıl dışlarım?**

Kullanıcıya özel ayar için [Visual Studio'da Canlı Birim Testini Kullan](live-unit-testing.md#include-and-exclude-test-projects-and-test-methods) makalesinin "Test projelerini ve test yöntemlerini dahil et ve hariç tut" bölümüne bakın. Belirli bir izleme oturumu için belirli bir test kümesini çalıştırmak veya kendi kişisel tercihlerinizi sürdürmek istediğinizde testler dahil etmek veya hariç tetmek yararlıdır.

Çözüme özgü ayarlar için, <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute?displayProperty=fullName> yöntemleri, özellikleri, sınıfları veya yapıları Canlı Birim Testi tarafından araçlandırılmaktan dışlamak için özniteliği programlı olarak uygulayabilirsiniz. Ayrıca, `<ExcludeFromCodeCoverage>` tüm projenin çalgılanmamasını hariç tutmak için özelliği `true` proje dosyanızda da ayarlayabilirsiniz. Canlı Birim Testi yine de enstrümante edilmemiş testleri çalıştıracaktır, ancak kapsamları görselleştirilmeyecektir.

Ayrıca geçerli uygulama `Microsoft.CodeAnalysis.LiveUnitTesting.Runtime` etki alanında yüklenip yüklenmediğini denetleyebilir ve neden lerine bağlı olarak testleri devre dışı kullanabilirsiniz. Örneğin, xUnit ile aşağıdaki gibi bir şey yapabilirsiniz:

```csharp
[ExcludeFromCodeCoverage]
public class SkipLiveFactAttribute : FactAttribute
{
   private static bool s_lutRuntimeLoaded = AppDomain.CurrentDomain.GetAssemblies().Any(a => a.GetName().Name ==
                                            "Microsoft.CodeAnalysis.LiveUnitTesting.Runtime");
   public override string Skip => s_lutRuntimeLoaded ? "Test excluded from Live Unit Testing" : "";
}

public class Class1
{
   [SkipLiveFact]
   public void F()
   {
      Assert.True(true);
   }
}
```

::: moniker range="vs-2017"

## <a name="win32-pe-headers"></a>Win32 PE üstbilgi

**Live Unit testi tarafından üretilen enstrümanlı derlemelerde Win32 PE başlıkları neden farklıdır?**

Bu sorun giderilmiştir ve Visual Studio 2017 sürüm 15.3 ve sonraki sürümlerinde yoktur.

Visual Studio 2017'nin eski sürümlerinde, Canlı Birim Testi'nin aşağıdaki Win32 PE Üstbilgi verilerini katıştırmamasına neden olabilecek bilinen bir hata vardır:

- Dosya Sürümü @System.Reflection.AssemblyFileVersionAttribute (kodda belirtilir).

- Win32 Simgesi (komut `/win32icon:` satırında belirtilir).

- Win32 Bildirimi (komut `/win32manifest:` satırında belirtilir).

Bu değerlere dayanan testler, Live Unit testi tarafından yürütüldüğünde başarısız olabilir.

::: moniker-end

## <a name="continuous-builds"></a>Sürekli yapılar

**Canlı Birim testi, herhangi bir delem yapmasam bile neden çözümümü sürekli oluşturmaya devam ediyor?**

Yapı işlemi çözümün kendi parçası olan kaynak kodu oluştursa ve yapı hedef dosyalarınızda belirtilen uygun giriş ve çıktılar yoksa, çözümünüzün yapılışı yapılsa bile çözüm oluşturabilirsiniz. Hedeflere, MSBuild'in uygun güncel denetimleri gerçekleştirebilmeleri ve yeni bir yapı gerekip gerekmediğini belirleyebilmeleri için giriş ve çıktıların bir listesi verilmelidir.

Canlı Birim Testi, kaynak dosyaların değiştiğini algıladığında bir yapı başlatır. Çözümünüz oluşturmak kaynak dosyaları oluşturduğundan, Canlı Birim Testi sonsuz bir yapı döngüsüne girer. Ancak, Canlı Birim Testi ikinci yapıyı başlattığında hedefin giriş ve çıkışları işaretlenirse (önceki yapıdan yeni oluşturulan kaynak dosyaları algıladıktan sonra), giriş ve çıktı denetimleri işaret ettiğinden yapı döngüsünden çıkar her şey güncel.

## <a name="editor-icons"></a>Editör simgeleri

**Canlı Birim Testi, Çıktı penceresindeki iletileri temel alan testleri çalıştırıyor gibi görünse de, neden editörde herhangi bir simge göremiyorum?**

Canlı Birim Testi'nin çalıştığı derlemeler herhangi bir nedenle enstrümante değilse, editörde simgeleri göremeyebilirsiniz. Örneğin, Canlı Birim Testi ayarlayan `<UseHostCompilerIfAvailable>false</UseHostCompilerIfAvailable>`projelerle uyumlu değildir. Bu durumda, yapı işleminizin bu ayarı kaldırmak veya Canlı `true` Birim Testi'nin çalışması için değiştirmek için güncelleştirilmesi gerekir. 

## <a name="capture-logs"></a>Günlükleri yakalama

**Hata raporları dosyalamak için daha ayrıntılı günlükleri nasıl toplarım?**

Daha ayrıntılı günlükleri toplamak için birkaç şey yapabilirsiniz:

- **Araçlar** > **Seçenekleri** > **Canlı Birim Testi'ne** gidin ve günlük seçeneğini **Verbose**olarak değiştirin. Verbose günlüğe kaydetme, **Çıktı** penceresinde daha ayrıntılı günlüklerin gösterilmesine neden olur.

- Kullanıcı `LiveUnitTesting_BuildLog` ortamı değişkenini MSBuild günlüğünü yakalamak için kullanmak istediğiniz dosyanın adına ayarlayın. Canlı Birim Testi yapılarından ayrıntılı MSBuild günlük iletileri bu dosyadan alınabilir.

- Test `LiveUnitTesting_TestPlatformLog` Platformu günlüğünü `1` yakalamak için kullanıcı ortamı değişkenini ayarlayın. Canlı Birim Test çalıştıran ayrıntılı Test Platformu günlük `[Solution Root]\.vs\[Solution Name]\log\[VisualStudio Process ID]`iletileri daha sonra alınabilir.

- Kullanıcı düzeyinde bir ortam `VS_UTE_DIAGNOSTICS` değişkeni oluşturun ve 1 (veya herhangi bir değer) olarak ayarlayın ve Visual Studio'yı yeniden başlatın. Şimdi Visual Studio **Çıktı - Testler** sekmesinde günlük çok görmelisiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Canlı Ünite Testi](live-unit-testing.md)
