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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75591547"
---
# <a name="live-unit-testing-frequently-asked-questions"></a>Live Unit Testing sık sorulan sorular

## <a name="supported-frameworks"></a>Desteklenen çerçeveler

**Hangi test çerçeveleri Live Unit Testing destekler ve desteklenen en düşük sürüm nedir?**

Live Unit Testing, aşağıdaki tabloda listelenen üç popüler birim testi çerçevesi ile birlikte kullanılabilir. Bağdaştırıcıların ve çerçevelerinin desteklenen minimum sürümü tabloda de listelenmiştir. Birim test çerçevelerinin tümü NuGet.org adresinden kullanılabilir.

|Test çerçevesi  |Visual Studio bağdaştırıcısı en düşük sürüm  |Framework minimum sürümü  |
|---------|---------|---------|
|xUnit.net |xUnit. Runner. VisualStudio sürüm 2.2.0-Beta3-build1187 |xUnit 1.9.2 |
|NUnit |NUnit3TestAdapter sürümü 3.7.0 |NUnit sürümü 3.5.0 |
|MSTest |MSTest. TestAdapter 1.1.4-Önizleme |MSTest. TestFramework 1.0.5-Önizleme |

Başvuru yapan `Microsoft.VisualStudio.QualityTools.UnitTestFramework` ve daha yeni MSTest NuGet paketlerine geçmek istemediğiniz daha eski bir test projesi varsa, Visual studio 2019 veya Visual studio 2017 sürümüne yükseltin.

Bazı durumlarda, Live Unit Testing çalışması için çözümdeki projeler tarafından başvurulan NuGet paketlerini açıkça geri yüklemeniz gerekebilir. Çözümün açık bir derlemesini yaparak ( **Build**  >  en üst düzey Visual Studio menüsünden derleme**yeniden oluşturma çözümünü** seçin) ya da çözüme sağ tıklayıp ve ardından, bilgisayarlarda sağ tıklayıp **NuGet paketlerini geri yükle** ' yi seçerek paketleri geri yükleyebilirsiniz.

## <a name="net-core-support"></a>.NET Core desteği

**Live Unit Testing .NET Core ile çalışıyor mu?**

Evet. Live Unit Testing .NET Core ve .NET Framework ile birlikte kullanılabilir.

## <a name="configuration"></a>Yapılandırma

**Bu öğeyi kapatdığımda neden Live Unit Testing çalışmıyor?**

Çıkış penceresi (Live Unit Testing açılan pencere seçildiğinde) Live Unit Testing neden çalışmadığını anlamalıdır. Aşağıdaki nedenlerden biri için Live Unit Testing çalışmayabilir:

- Çözümdeki projeler tarafından başvurulan NuGet paketleri geri yüklenemediğinde Live Unit Testing çalışmaz. Çözümün açık bir derlemesini yapmak veya Live Unit Testing açılmadan önce çözümde NuGet paketlerini geri yüklemek, bu sorunu çözmelidir.

- Projelerinizde MSTest tabanlı testler kullanıyorsanız, başvurusunu kaldırdığınızdan `Microsoft.VisualStudio.QualityTools.UnitTestFramework` ve en son MSTest NuGet paketlerine başvurular eklediğinizden emin olun, `MSTest.TestAdapter` (en düşük bir 1.1.11 sürümü gereklidir) ve `MSTest.TestFramework` (en az bir 1.1.11 sürümü gerekir). Daha fazla bilgi için, [Visual Studio 'da Live Unit Testing kullanma](live-unit-testing.md#supported-test-frameworks) makalesindeki "desteklenen test çerçeveleri" bölümüne bakın.

- Çözümünüzde en az bir projede bir NuGet başvurusu veya xUnit, NUnit veya MSTest test çerçevesine doğrudan başvuru olmalıdır. Bu proje Ayrıca karşılık gelen bir Visual Studio test bağdaştırıcıları NuGet paketine başvurmalıdır. Visual Studio test bağdaştırıcısına bir *. runsettings* dosyası aracılığıyla da başvurulabilir. *. Runsettings* dosyası aşağıdaki örnekteki gibi bir girdiye sahip olmalıdır:

```xml
<RunSettings>
    <RunConfiguration>
          <TestAdaptersPaths>path-to-your-test-adapter</TestAdaptersPaths>
     </RunConfiguration>
</RunSettings>
```

## <a name="incorrect-coverage-after-upgrade"></a>Yükseltmeden sonra yanlış kapsam

**Visual Studio projelerinizde başvurulan test bağdaştırıcısını desteklenen sürüme yükselttikten sonra neden Live Unit Testing yanlış kapsamı gösteriyor?**

- Çözümdeki birden çok proje NuGet test bağdaştırıcısı paketine başvuruda bulunursa, her birinin desteklenen sürüme yükseltilmesi gerekir.

- Test bağdaştırıcısı paketinden içeri aktarılan MSBuild *. props* dosyasının da doğru şekilde güncelleştirildiğinden emin olun. Genellikle proje dosyasının en üstünde bulunan, aşağıdaki gibi, bir içeri aktarmanın NuGet paketi sürümünü/yolunu denetleyin:

   ```xml
    <Import Project="..\packages\xunit.runner.visualstudio.2.2.0\build\net20\xunit.runner.visualstudio.props" Condition="Exists('..\packages\xunit.runner.visualstudio.2.2.0\build\net20\xunit.runner.visualstudio.props')" />
   ```

## <a name="customize-builds"></a>Derlemeleri Özelleştir

**Live Unit Testing Derlemelerimi özelleştirebilir miyim?**

Çözümünüz, "normal" işaretlenmiş olmayan derleme için gerekli olmayan izleme (Live Unit Testing) için derleme için özel adımlar gerektiriyorsa, projenize veya *. targets* dosyalarına `BuildingForLiveUnitTesting` özelliği denetleyen ve özel ön/sonrası oluşturma adımları gerçekleştiren bir kod ekleyebilirsiniz. Ayrıca, belirli derleme adımlarını (paket yayımlama veya oluşturma gibi) ya da bu proje özelliğine dayalı Live Unit Testing bir yapıya derleme adımları (örneğin, önkoşulları kopyalama) eklemeyi seçebilirsiniz. Bu özelliğe göre yapınızı özelleştirmek, normal derlemenizi herhangi bir şekilde değiştirmez ve yalnızca Live Unit Testing yapıları etkiler.

Örneğin, normal bir derleme sırasında NuGet paketleri üreten bir hedef olabilir. Yaptığınız her Düzenlemeden sonra NuGet paketlerinin oluşturulmasını istemezsiniz. Bu nedenle, aşağıdaki gibi bir şey yaparak Live Unit Testing derlemesinde bu hedefi devre dışı bırakabilirsiniz:  

```xml
<Target Name="GenerateNuGetPackages" BeforeTargets="AfterBuild" Condition="'$(BuildingForLiveUnitTesting)' != 'true'">
    <Exec Command='"$(MSBuildThisFileDirectory)..\tools\GenPac" '/>
</Target>
```

## <a name="error-messages-with-outputpath-outdir-or-intermediateoutputpath"></a>Veya içeren hata \<OutputPath> iletileri \<OutDir>\<IntermediateOutputPath>

**Live Unit Testing çözümümüzü derlemeyi denediğinde neden aşağıdaki hatayı alıyorum: "... koşulsuz olarak ayarlanan veya olarak `<OutputPath>` görünür `<OutDir>` . Live Unit Testing, çıkış derlemesinden testleri yürütmez "?**

Çözümünüz için derleme işleminin ikili dosyaların nerede oluşturulacağını belirten özel bir mantığı varsa, bu hatayı alabilirsiniz. Varsayılan olarak, ikili ağınızın konumu, veya veya ile değişir `<OutputPath>` `<OutDir>` `<IntermediateOutputPath>` `<BaseOutputPath>` `<BaseIntermediateOutputPath>` .

Live Unit Testing, derleme yapıtlarının bir Live Unit Testing yapıt klasörüne bırakılması ve derleme işleminiz bu değişkenleri geçersiz kılıyorsa başarısız olacağı için bu değişkenleri geçersiz kılar.

Live Unit Testing derlemeyi başarıyla oluşturmak için iki ana yaklaşım vardır. Daha kolay derleme yapılandırması için çıkış yollarınızın üzerine temelleyebilirsiniz `<BaseIntermediateOutputPath>` . Daha karmaşık yapılandırmalarda çıkış yollarınızı temel alabilirsiniz `<LiveUnitTestingBuildRootPath>` .

### <a name="overriding-outputpathintermediateoutputpath-conditionally-based-on-baseoutputpath-baseintermediateoutputpath"></a>`<OutputPath>` / `<IntermediateOutputPath>` Koşullu olarak geçersiz kılma `<BaseOutputPath>` / `<BaseIntermediateOutputPath>` .

> [!NOTE]
> Bu yaklaşımı kullanmak için, her projenin birbirinden bağımsız olarak derlenebilir olması gerekir. Derleme sırasında başka bir projeden bir proje başvuru yapıtlarına sahip değilsiniz. Çalışma zamanı (örneğin, çağrı) sırasında başka bir projeden dinamik olarak derleme yükleme `Assembly.Loadfile("..\..\Project2\Release\Project2.dll")` .

Yapı sırasında, Live Unit Testing `<BaseOutputPath>` / `<BaseIntermediateOutputPath>` Live Unit Testing yapıtlar klasörünü hedeflemek için değişkenleri otomatik olarak geçersiz kılar.

Örneğin, derlemeniz <OutputPath> aşağıda gösterildiği gibi geçersiz kılar:

```xml
<Project>
  <PropertyGroup>
    <OutputPath>$(SolutionDir)Artifacts\$(Configuration)\bin\$(MSBuildProjectName)</OutputPath>
  </PropertyGroup>
</Project>
```

ardından, aşağıdaki XML ile değiştirebilirsiniz:

```xml
<Project>
  <PropertyGroup>
    <BaseOutputPath Condition="'$(BaseOutputPath)' == ''">$(SolutionDir)Artifacts\$(Configuration)\bin\$(MSBuildProjectName)\</BaseOutputPath>
    <OutputPath Condition="'$(OutputPath)' == ''">$(BaseOutputPath)</OutputPath>
  </PropertyGroup>
</Project>
```

Bu `<OutputPath>` , klasörün içinde olmasını sağlar `<BaseOutputPath>` .

`<OutDir>`Doğrudan derleme sürecinizdeki üzerine vermeyin; `<OutputPath>` derleme yapıtlarını belirli bir konuma bırakmak yerine geçersiz kılın.

### <a name="overriding-your-properties-based-on-the-liveunittestingbuildrootpath-property"></a>Özelliği temel alarak özelliklerinizi geçersiz kılma `<LiveUnitTestingBuildRootPath>` .

> [!NOTE]
> Bu yaklaşımda, derleme sırasında oluşturulmayan yapıt klasörü altına eklenen dosyalar konusunda dikkatli olmanız gerekir. Aşağıdaki örnekte, paketler klasörü yapıtlar altına yerleştirilirken ne yapabileceğiniz gösterilmektedir. Bu klasörün içeriği derleme sırasında oluşturulmadığından, MSBuild özelliği **değiştirilmemelidir**.

Live Unit Testing yapı sırasında, `<LiveUnitTestingBuildRootPath>` özelliği Live Unit Testing yapıtlar klasörünün konumuna ayarlanır.

Örneğin, projenizin burada gösterilen yapıya sahip olduğunu varsayalım.

```
.vs\...\lut\0\b
artifacts\{binlog,obj,bin,nupkg,testresults,packages}
src\{proj1,proj2,proj3}
tests\{testproj1,testproj2}
Solution.sln
```
Live Unit Testing yapı sırasında, `<LiveUnitTestingBuildRootPath>` özelliği öğesinin tam yolu olarak ayarlanır `.vs\...\lut\0\b` . Proje, `<ArtifactsRoot>` çözüm dizini ile eşleşen özelliği tanımlıyorsa, MSBuild projesini aşağıdaki şekilde güncelleştirebilirsiniz:

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

## <a name="build-artifact-location"></a>Yapı yapıt konumu

**Live Unit Testing derleme yapıtlarının, *. vs* klasörü altındaki varsayılan konum yerine belirli bir konuma gitmesini istiyorum. Bunu nasıl değiştirebilirim?**

`LiveUnitTesting_BuildRoot`Kullanıcı düzeyi ortam değişkenini Live Unit Testing derleme yapıtlarının kesilmesini istediğiniz yola ayarlayın. 

## <a name="test-explorer-versus-live-unit-testing"></a>Test Gezgini Live Unit Testing karşı

**Test Gezgini penceresinden testlerin Live Unit Testing testlerin çalıştırılmasının farkı nasıl çalışır?**

Çeşitli farklılıklar vardır:

- **Test Gezgini** penceresinde testleri çalıştırmak veya hata ayıklamak, düzenli ikili dosyalar çalıştırlarken Live Unit Testing, işaretlenmiş ikililer çalıştırır. Araçlı ikililerin hata ayıklaması yapmak istiyorsanız, [hata ayıklayıcı ekleme.](xref:System.Diagnostics.Debugger.Launch)   Test yönteinizde başlatma yöntemi çağrısı, bu yöntem yürütüldüğünde hata ayıklayıcının başlatılmasına neden olur (Live Unit Testing tarafından yürütüldüğünde dahil) ve ardından, izlenen ikiliyi iliştirebilir ve hata ayıklaması yapabilirsiniz. Bununla birlikte, umuyoruz çoğu kullanıcı senaryosunda sizin için şeffaf ve işaretlenmiş ikililerin hata ayıklamanıza gerek kalmaz.

- Live Unit Testing testleri çalıştırmak için yeni bir uygulama etki alanı oluşturmaz, ancak **Test Gezgini** penceresinden çalıştırılan testler yeni bir uygulama etki alanı oluşturur.

- Live Unit Testing her bir test derlemesindeki testleri sırayla çalıştırır. **Test Gezgini**'nde, paralel olarak birden çok test çalıştırmayı seçebilirsiniz.

- **Test Gezgini** , testleri tek iş parçacıklı bir grupta (STA) çalıştırır. Live Unit Testing, testleri çok iş parçacıklı bir grupta (MTA) çalıştırır. Live Unit Testing 'de STA 'da MSTest testlerini çalıştırmak için, test yöntemini veya içeren sınıfı, `<STATestMethod>` `<STATestClass>` NuGet paketinde bulunan veya özniteliğiyle süsle birlikte kullanabilirsiniz `MSTest.STAExtensions 1.0.3-beta` . NUnit için, özniteliğiyle birlikte test yöntemini `<RequiresThread(ApartmentState.STA)>` ve xUnit için özniteliği ile süslemek için `<STAFact>` .

## <a name="exclude-tests"></a>Testleri hariç tut

**Nasıl yaparım? testlerin Live Unit Testing katılmasını hariç tutsın mı?**

Kullanıcıya özgü ayar için, [Visual Studio 'da Live Unit Testing kullanma](live-unit-testing.md#include-and-exclude-test-projects-and-test-methods) makalesindeki "test projelerini ve test yöntemlerini ekleme ve dışlama" bölümüne bakın. Belirli bir düzenleme oturumu için belirli bir test kümesini çalıştırmak veya kendi kişisel tercihlerinizi sürdürmek istediğinizde, testlerin dahil edilmesi veya dışlanması yararlı olur.

Çözüme özgü ayarlar için, <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute?displayProperty=fullName> metodu, özellikleri, sınıfları veya yapıları Live Unit Testing tarafından işaretlenmiş olarak hariç tutmak için programlı olarak özniteliği uygulayabilirsiniz. Ayrıca, projenin `<ExcludeFromCodeCoverage>` `true` tamamını işaretlenmiş olarak hariç tutmak için özelliği proje dosyanızda olarak ayarlayabilirsiniz. Live Unit Testing, henüz eklenmemiş testleri çalıştırmaya devam eder, ancak kapsamı görselleştirilecektir.

Ayrıca, `Microsoft.CodeAnalysis.LiveUnitTesting.Runtime` geçerli uygulama etki alanına yüklenip yüklenmediğini denetleyebilir ve Testleri neden temel alarak devre dışı bırakabilirsiniz. Örneğin, xUnit ile aşağıdakine benzer bir şey yapabilirsiniz:

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

## <a name="win32-pe-headers"></a>Win32 PE üstbilgileri

**Canlı birim testi tarafından oluşturulan işaretlenmiş derlemelerde Win32 PE üstbilgileri neden farklıdır?**

Bu sorun düzeltildi ve Visual Studio 2017 sürüm 15,3 ve sonraki sürümlerde yok.

Visual Studio 2017 ' nin eski sürümleri için, Live Unit Testing derlemelerin aşağıdaki Win32 PE başlık verilerini ekleyememesi ile sonuçlanabileceğini belirten bilinen bir hata vardır:

- Dosya sürümü (kodda tarafından belirtilen @System.Reflection.AssemblyFileVersionAttribute ).

- Win32 simgesi ( `/win32icon:` komut satırında tarafından belirtilen).

- Win32 bildirimi ( `/win32manifest:` komut satırında tarafından belirtilen).

Bu değerleri kullanan testler, canlı birim testi tarafından yürütüldüğünde başarısız olabilir.

::: moniker-end

## <a name="continuous-builds"></a>Sürekli derlemeler

**Canlı birim testi neden, hiç bir düzenleme yapmadığım halde çözümümüzü her zaman oluşturmaya devam ediyor?**

Yapı işlemi çözümün kendisinin parçası olan kaynak kodu oluşturursa ve yapı hedef dosyalarınızda uygun girişler ve çıktılar belirtilmemişse, çözümünüz, düzenleme yapmasanız bile oluşturabilir. MSBuild 'in uygun güncel denetimleri gerçekleştirebilmesi ve yeni bir derleme gerekip gerekmediğini belirleyebilmesi için, hedeflerin bir giriş ve çıkış listesi verilmelidir.

Live Unit Testing, kaynak dosyaların değiştiğini algıladığında bir derlemeyi başlatır. Çözümünüzün derlemesi kaynak dosyalar oluşturduğundan Live Unit Testing sonsuz bir derleme döngüsüne alınır. Ancak, Live Unit Testing ikinci derlemeyi başlattığında hedefin giriş ve çıkışları işaretlenirse (önceki derlemeden yeni oluşturulan kaynak dosyalarını algıladıktan sonra), giriş ve çıkış denetimleri her şeyin güncel olduğunu göstermek için derleme döngüsünün dışına çıkar.

## <a name="editor-icons"></a>Düzenleyici simgeleri

**Neden, çıkış penceresindeki iletilere göre testlerin çalıştırılmasına rağmen Live Unit Testing düzenleyicide hiç simge görmüyorum?**

Live Unit Testing üzerinde çalışan derlemeler herhangi bir nedenle işaretlenmemişse düzenleyicide simge göremeyebilirsiniz. Örneğin, Live Unit Testing, tarafından ayarlanan projelerle uyumlu değildir `<UseHostCompilerIfAvailable>false</UseHostCompilerIfAvailable>` . Bu durumda, derleme işleminizin bu ayarı kaldırmak veya Live Unit Testing çalışması için olarak değiştirmek üzere güncelleştirilmesi gerekir `true` . 

## <a name="capture-logs"></a>Günlükleri yakala

**Hata raporlarına dosya eklemek için daha ayrıntılı Günlükler mi Nasıl yaparım??**

Daha ayrıntılı Günlükler toplamak için birkaç şey yapabilirsiniz:

- **Araçlar**  >  **Seçenekler**  >  **Live Unit Testing** gidin ve günlük seçeneğini **verbose**olarak değiştirin. Ayrıntılı günlük kaydı, **Çıkış** penceresinde daha ayrıntılı günlüklerin gösterilmesine neden olur.

- `LiveUnitTesting_BuildLog`Kullanıcı ortam değişkenini, MSBuild günlüğünü yakalamak için kullanmak istediğiniz dosyanın adı olarak ayarlayın. Live Unit Testing derlemelerden ayrıntılı MSBuild günlük iletileri daha sonra bu dosyadan alınabilir.

- `LiveUnitTesting_TestPlatformLog` `1` Test platformu günlüğünü yakalamak için Kullanıcı ortam değişkenini olarak ayarlayın. Live Unit Testing çalıştırmalarının ayrıntılı test platformu günlüğü iletileri daha sonra öğesinden alınabilir `[Solution Root]\.vs\[Solution Name]\log\[VisualStudio Process ID]` .

- Adlı bir Kullanıcı düzeyi ortam değişkeni oluşturun `VS_UTE_DIAGNOSTICS` ve bunu 1 (veya herhangi bir değer) olarak ayarlayın ve Visual Studio 'yu yeniden başlatın. Artık Visual Studio 'daki **çıkış testleri** sekmesinde çok fazla günlük görmeniz gerekir.

## <a name="see-also"></a>Ayrıca bkz.

- [Live Unit Testing](live-unit-testing.md)
