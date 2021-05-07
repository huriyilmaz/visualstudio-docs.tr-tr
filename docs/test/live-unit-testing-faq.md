---
title: Live Unit Testing SSS
description: Desteklenen çerçeveler Live Unit Testing yapılandırma ve özelleştirme gibi sık sorulan soruları gözden geçirebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 10/03/2017
ms.topic: conceptual
helpviewer_keywords:
- Live Unit Testing FAQ
author: mikejo5000
ms.author: mikejo
ms.workload:
- dotnet
ms.openlocfilehash: bb2c9a4cae25b388d5817b04ff54f6e6443b2f44
ms.sourcegitcommit: dd2fc6e03a789c044f8438096b8f112e4dba5557
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2021
ms.locfileid: "108800528"
---
# <a name="live-unit-testing-frequently-asked-questions"></a>Live Unit Testing sorulan sorular

## <a name="supported-frameworks"></a>Desteklenen çerçeveler

**Hangi test çerçeveleri Live Unit Testing ve desteklenen en düşük sürümler hangileridir?**

Live Unit Testing, aşağıdaki tabloda listelenen üç popüler birim testi çerçevesiyle çalışır. Bağdaştırıcılarının ve çerçevelerinin desteklenen en düşük sürümü de tabloda listelenmiştir. Birim testi çerçeveleri, NuGet.org.

|Test Çerçevesi  |Visual Studio Bağdaştırıcısı en düşük sürümü  |Çerçeve en düşük sürümü  |
|---------|---------|---------|
|xUnit.net |xunit.runner.visualstudio sürüm 2.2.0-beta3-build1187 |xunit 1.9.2 |
|NUnit |NUnit3TestAdapter sürüm 3.7.0 |NUnit sürüm 3.5.0 |
|MSTest |MSTest.TestAdapter 1.1.4-preview |MSTest.TestFramework 1.0.5-preview |

Başvurulan eski MSTest tabanlı test projeleriniz varsa ve daha yeni MSTest NuGet paketlerine taşımak `Microsoft.VisualStudio.QualityTools.UnitTestFramework` yoksa, Visual Studio 2019 veya 2017'ye Visual Studio yükseltin.

Bazı durumlarda, çözümün çalışması için çözümdeki projeler tarafından başvurulan NuGet paketlerini Live Unit Testing gerekir. Çözümün açık bir derlemesini yaparak (üst düzey Visual Studio menüsünden Çözümü Yeniden Derleme'yi seçin) veya çözüme sağ tıklar ve Living Unit Testing'i etkinleştirmeden önce NuGet Paketlerini Geri Yükle'yi seçerek paketleri geri  >   yükleyebilirsiniz. 

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

## <a name="customize-builds"></a>Derlemeleri özelleştirme

**Derlemelerimi özel Live Unit Testing miyim?**

Çözümünüz , "normal" olarak irdelemeli olmayan derleme için gerekli olmayan ölçümlü (Live Unit Testing) için özel adımlar gerektiriyorsa, projenize kod ekleyebilir veya özelliği kontrol etmek ve özel derleme öncesi/sonrası adımları gerçekleştiren *.targets* dosyalarına kod `BuildingForLiveUnitTesting` abilirsiniz. Ayrıca belirli derleme adımlarını (yayımlama veya paket oluşturma gibi) kaldırmayı veya derleme adımlarını (önkoşulları kopyalama gibi) bu proje özelliğine göre Live Unit Testing derlemeye eklemek de seçebilirsiniz. Derlemenizi bu özelliği temel alarak özelleştirmek normal derlemenizi herhangi bir şekilde değiştirmez ve yalnızca derlemeleri Live Unit Testing etkiler.

Örneğin, normal bir derleme sırasında NuGet paketleri üreten bir hedef olabilir. Büyük olasılıkla, nuget paketlerinin, yapılan her düzenlemeden sonra üretilenemlerini istemeyebilirsiniz. Bu nedenle, aşağıdakine benzer bir Live Unit Testing hedef derlemesinde bu hedefi devre dışı siniz:  

```xml
<Target Name="GenerateNuGetPackages" BeforeTargets="AfterBuild" Condition="'$(BuildingForLiveUnitTesting)' != 'true'">
    <Exec Command='"$(MSBuildThisFileDirectory)..\tools\GenPac" '/>
</Target>
```

## <a name="error-messages-with-outputpath-outdir-or-intermediateoutputpath"></a>, veya ile \<OutputPath> hata \<OutDir> iletileri \<IntermediateOutputPath>

**Live Unit Testing çözümüm derlemeye çalıştığında neden şu hatayı alıyorum: "... , veya koşulsuz olarak ayarlanmış gibi `<OutputPath>` `<OutDir>` görünür. Live Unit Testing derlemeden test yürütmezsiniz"?**

Çözümünüz için derleme işlemi ikililerin nerede oluşturulacaklarını belirten özel mantığa sahipse bu hatayı alabilirsiniz. Varsayılan olarak ikili değerlerinizi konumunuz , `<OutputPath>` veya `<OutDir>` veya `<IntermediateOutputPath>` değerine `<BaseOutputPath>` `<BaseIntermediateOutputPath>` bağlıdır.

Live Unit Testing, derleme yapıtlarının bir Live Unit Testing yapıtlar klasörüne bırakıldıklarını ve derleme işleminiz de bu değişkenleri geçersiz kılarsa başarısız olmasını sağlamak için bu değişkenleri geçersiz kılar.

Derlemeyi başarıyla oluşturmak için iki Live Unit Testing yaklaşım vardır. Daha kolay derleme yapılandırmaları için çıkış yollarınızı temel olarak `<BaseIntermediateOutputPath>` ebilirsiniz. Daha karmaşık yapılandırmalar için çıkış yollarınızı temel olarak `<LiveUnitTestingBuildRootPath>` ebilirsiniz.

### <a name="overriding-outputpathintermediateoutputpath-conditionally-based-on-baseoutputpath-baseintermediateoutputpath"></a>temel alarak `<OutputPath>` / `<IntermediateOutputPath>` koşullu olarak geçersiz `<BaseOutputPath>` / `<BaseIntermediateOutputPath>` kılma.

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

**Test Gezgini penceresinden test çalıştırmanın, testlerin testlerde çalıştırıla Live Unit Testing?**

Birkaç farklılık vardır:

- Test Gezgini penceresinden testleri **çalıştırma** veya hata ayıklama normal ikililer çalıştırırken, Live Unit Testing ikililer çalıştırır. Araçlı ikili dosyalarda hata ayıklamak istemiyorsanız, test yönteminize bir [Debugger.Launch](xref:System.Diagnostics.Debugger.Launch) yöntemi çağrısı eklemek, bu yöntem her yürütülürken (Live Unit Testing tarafından yürütülürken dahil) hata ayıklayıcının başlatılmasına neden olur ve ardından, araçlı ikili dosyayı iliştirerek ve hata ayıklamasını gerçekleştirebilirsiniz. Ancak, çoğu kullanıcı senaryosunda ölçüm ölçümenin sizin için saydam olduğunu ve araçlı ikili dosyalarda hata ayıklamaya gerek olmadığını umuyoruz.

- Live Unit Testing testleri çalıştırmak için yeni bir uygulama etki alanı oluşturmaz, ancak **Test** Gezgini penceresinden çalıştırilen testler yeni bir uygulama etki alanı oluşturabilir.

- Live Unit Testing her test derlemesinde testleri sırayla çalıştırır. **Test Gezgini'nde** birden çok testi paralel olarak çalıştırmayı seçebilirsiniz.

- **Test Gezgini** testleri varsayılan olarak tek iş parçacıklı bir kanalda (STA) çalıştırırken, Live Unit Testing iş parçacıklı bir kanalda (MTA) testler çalıştırır. Live Unit Testing'da STA'da MSTest testleri çalıştırmak için test yöntemini veya içeren sınıfı NuGet paketinde bulunan veya özniteliğiyle `<STATestMethod>` `<STATestClass>` `MSTest.STAExtensions 1.0.3-beta` dekoreleyin. NUnit için, test yöntemini özniteliğiyle `<RequiresThread(ApartmentState.STA)>` ve xUnit için özniteliğiyle dekore `<STAFact>` et.

## <a name="exclude-tests"></a>Testleri hariç tut

**Nasıl yaparım? katılan testleri dışlamak Live Unit Testing?**

Kullanıcıya özgü ayar için bu makaledeki Use [Live Unit Testing](live-unit-testing.md#include-and-exclude-test-projects-and-test-methods) (Test projelerini ve test Visual Studio dahil edin ve hariç tut) bölümüne bakın. Belirli bir düzenleme oturumu için belirli bir test kümesi çalıştırmak veya kendi kişisel tercihlerinizi kalıcı yapmak istediğiniz zaman testleri dahil etmek veya hariç tutarak yararlı olur.

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

Live Unit Testing, kaynak dosyaların değiştiğini algıladığında bir derlemeyi başlatır. Çözümünüzün derlemesi kaynak dosyalar oluşturduğundan Live Unit Testing sonsuz bir derleme döngüsüne alınır. Ancak, Live Unit Testing ikinci derlemeyi başlatırken (önceki derlemeden yeni oluşturulan kaynak dosyaları algıladikten sonra) hedefin girişleri ve çıkışları denetlenirse, giriş ve çıkış denetimleri her şeyin güncel olduğunu işaret eder çünkü derleme döngüsünden çıkar.

## <a name="editor-icons"></a>Düzenleyici simgeleri

**Çıkış penceresindeki iletilere göre testleri çalıştırmış Live Unit Testing neden düzenleyicide herhangi bir simge göremiyorum?**

Üzerinde çalışan derlemeler herhangi bir nedenle Live Unit Testing düzenleyicide simge görmeyebilirsiniz. Örneğin, Live Unit Testing ayara sahip projelerle uyumlu `<UseHostCompilerIfAvailable>false</UseHostCompilerIfAvailable>` değildir. Bu durumda, derleme işleminizin bu ayarı kaldırmak veya bu ayarın çalışması için olarak değiştirmek `true` Live Unit Testing gerekir. 

## <a name="capture-logs"></a>Günlükleri yakalama

**Nasıl yaparım? raporlarına daha ayrıntılı günlükler mi toplayabilirsiniz?**

Daha ayrıntılı günlükler toplamak için birkaç şey yapabiliriz:

- Araçlar **Seçenekler'e**  >    >  **Live Unit Testing** ve günlüğe kaydetme seçeneğini Ayrıntılı **olarak ayarlayın.** Ayrıntılı günlük kaydı, Çıkış penceresinde daha ayrıntılı günlükler gösterilmeye **neden** olur.

- Kullanıcı `LiveUnitTesting_BuildLog` ortamı değişkenlerini MSBuild günlüğünü yakalamak için kullanmak istediğiniz dosyanın adına ayarlayın. Derlemelerden ayrıntılı MSBuild Live Unit Testing daha sonra bu dosyadan alınabilirsiniz.

- Test Platformu `LiveUnitTesting_TestPlatformLog` günlüğünü yakalamak için kullanıcı ortamı `1` değişkenini olarak ayarlayın. Daha sonra, Live Unit Testing ayrıntılı Test Platformu günlük iletileri'den `[Solution Root]\.vs\[Solution Name]\log\[VisualStudio Process ID]` alınabilirsiniz.

- adlı kullanıcı düzeyinde bir ortam değişkeni oluşturun ve 1 (veya herhangi bir değer) olarak ayarlayın ve bu değişkeni `VS_UTE_DIAGNOSTICS` Visual Studio. Şimdi çıkışta çıkış - testler sekmesinde **çok fazla** günlük kaydı Visual Studio.

## <a name="see-also"></a>Ayrıca bkz.

- [Live Unit Testing](live-unit-testing.md)
